---
TOCTitle: 'Konfigurera certifierings- och licensieringstjänsterna på den första servern'
Title: 'Konfigurera certifierings- och licensieringstjänsterna på den första servern'
ms:assetid: 'cce29a2f-984f-48ed-9187-0eb68286ec5b'
ms:contentKeyID: 18124898
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747756(v=WS.10)'
---

Konfigurera certifierings- och licensieringstjänsterna på den första servern
============================================================================

Om du vill installera RMS i en skog börjar du med att installera och etablera en server. Den första servern som du etablerar är rotcertifikatservern. Den servern hanterar både certifiering och licensiering och kan användas som en ensam server i en enskild serverkonfiguration eller som den första servern i ett rotcertifikatkluster.

Roller, behörigheter och rättigheter krävs för installation och etablering av ytterligare RMS-servrar.
------------------------------------------------------------------------------------------------------

När du installerar RMS måste du logga in med ett konto med lokala administratörsrättigheter. Dessutom måste du vara inloggad på en domän med ett giltigt domänkonto för att Active Directory ska kunna autentisera RMS. Om du distribuerar RMS i en miljö där Active Directory-infrastrukturen använder Enhetligt läge i Windows 2000 är det inte säkert att RMS kan läsa attributet memberOf för Active Directory-objekt när Active Directory försöker expandera gruppmedlemskap. RMS-tjänstkontot måste vara ett konto på domännivå som tillhör gruppen Åtkomst till äldre operativsystem (före Windows 2000) i skogen, för att RMS ska kunna läsa attributet memberOf. Om du har distribuerat grupper med dolt medlemskap behöver du också konfigurera RMS-tjänstkontot med behörighet att läsa dolt medlemskap.

| ![](images/Cc747756.note(WS.10).gif)Obs!                   |
|-----------------------------------------------------------------------------------------|
| RMS-tjänstkontot kan inte vara samma domänkonto som användes vid installationen av RMS. |

Installations- och etableringsprocesser för den första servern
--------------------------------------------------------------

RMS-servern distribueras i två steg. Först måste RMS-serverprogramvaran installeras tillsammans med alla stödprogram, t.ex. IIS, Message Queuing och ASP.NET. Mer information om installationen finns i ”Så här installerar du RMS med Service Pack 1” i ”Använda en RMS-server”.

| ![](images/Cc747756.note(WS.10).gif)Obs!                                                                    |
|------------------------------------------------------------------------------------------------------------------------------------------|
| Du kan också installera RMS via Kommandotolken. Mer information finns i ”RMS-installation via Kommandotolken” i ”Använda en RMS-server”. |

När du har installerat RMS på en server måste du etablera RMS på en webbplats på den aktuella servern. När du etablerar denna webbplats ändras flera inställningar för webbplatsen och virtuella kataloger läggs till. Mer information om de här ändringarna finns i ”Internet Information Services-funktioner för RMS” i ”Teknisk referens för RMS”.

Du kan antingen använda standardwebbplatsen i IIS eller skapa en ny webbplats. Om du vill etablera RMS på en annan webbplats än standardwebbplatsen måste du skapa webbplatsen innan du utför etableringsprocessen. Om du använder standardwebbplatsen för andra syften skapar du en ny webbplats för RMS så att konfigurationen av standardwebbplatsen inte ändras.

När du klickar på **Administration av Windows RMS** på **Start**-menyn visas sidan **Global administration**. På den här sidan kan du starta etableringsprocessen på en webbplats. När du etablerar RMS på den första servern måste du ange följande information:

-   Namnen på de databaser som ska användas som konfigurations-, loggnings- och katalogtjänstdatabaser för RMS.
    Om SQL Server-instansen har ett annat namn än det lokala servernamnet måste du konfigurera den som en SQL Server-fjärrinstans även om allt är installerat på en enda server.
    Under etableringen måste den användare som är inloggad för tillfället ha behörighet att skapa databaser på databasservern.
-   Ange det konto som ska användas som RMS-tjänstkonto. För en lokal konfiguration går det att använda det lokala systemkontot men av säkerhetsskäl rekommenderar vi att du inte gör det. Undvik att köra tjänster med de behörigheter som det lokala systemkontot har.
    För en installation som omfattar en SQL Server-instans eller mer än en RMS-server måste du ange ett domänkonto. Domänkontot som används måste ha sökbehörigheter för Active Directory, och det kommer att användas till att skapa den IIS-programpool som administrationskonsolen körs under. Om du inte uppgraderar eller använder en befintlig databas krävs rättighet att skapa databaser för RMS-tjänstkontot. Om du använder befintliga databaser måste kontot ha läs- och skrivbehörighet till var och en av RMS-databaserna.
-   Ange den URL som ska användas för webbplatsen. Standardvärdet är namnet på den webbplats du etablerar (t.ex. Standardwebbplats, om du etablerar en server med en standardinstallation av IIS). Du kan ange en anpassad URL för åtkomst till en annan webbplats, t.ex. en URL som möjliggör belastningsutjämning eller både intranät- och Internet-åtkomst. Du måste kontrollera att den anpassade URL:en fungerar och lägga till webbplatsnamnet i DNS så att både sidan **Global administration** och sidan **Etablera** hittar de virtuella rotkatalogerna. Kontrollera att den nya URL:en är tillgänglig både från Internet och från företagets nätverk om URL:en är för en Internet-aktiverad distribution.
-   Välj med vilken metod rotinstallationens privata nyckel (som används för registrering) ska skyddas. Normalt används den programvarubaserade krypteringen där den krypterade privata nyckeln lagras i RMS-konfigurationsdatabasen. Du måste ange ett starkt lösenord för kryptering av värdet i databasen om du använder standardkonfigurationen.
    Har du däremot en HSM (Hardware Security Module) installerad och konfigurerad på datorn kan du också välja att använda en CSP (Cryptographic Service Provider) med denna HSM och lagra privata nycklar i t.ex. ett smartkort. I RMS krävs att en fullständig RSA-provider används. Endast sådana provider ingår i listan över CSP:er. Du bör använda en HSM för att skydda den privata RMS-nyckeln.
    Om du skyddar den privata RMS-nyckeln med det programvarubaserade CSP-alternativet och ett lösenord lagrar du lösenordet i ett säkert arkiv för framtida användning. Lagra också en säkerhetskopia av konfigurationsdatabasen tillsammans med lösenordet. När du gör det kan du återställa RMS även om SQL-databasen skulle skadas. Om du av någon anledning ändrar lösenordet gör du en ny säkerhetskopia av konfigurationsdatabasen som lagrar den privata nyckeln som skyddas med det aktuella lösenordet och placerar sedan lösenordet och säkerhetskopian i det säkra arkivet. Mer information om hur du säkerhetskopierar och återställer konfigurationsdatabasen finns i ”Säkerhetskopiera och återställa systemet för RMS” i ”Planera en RMS-distribution”.
-   Ange det namn som ska användas i serverlicensieringscertifikatet. Som standard är det serverns namn.
-   Ange en proxyserver (inklusive adress och port) som ska användas för Internet-anslutning, om det är aktuellt.
-   Ange en e-postadress som andra RMS-administratörer kan använda för att kontakta en administratör om det uppstår problem vid underregistrering av en licensieringsserver. När du har etablerat rotinstallationen kan du ändra den här adressen.
-   Välj en princip för återkallande av serverlicensieringscertifikat som anger vem, utöver Microsofts registreringstjänst, som kan återkalla rotinstallationens serverlicensieringscertifikat. Om återkallning av tredje part aktiveras måste du ange sökväg till och namn på den fil som innehåller den offentliga nyckeln för den tredje parten.

Om du har valt alternativet onlineregistrering genereras ett nyckelpar och den offentliga nyckeln skickas till Microsofts registreringstjänst när du klickar på **Skicka** på sidan **Etablering** (efter att du har angett alla aktuella alternativ). (Stäng inte sidan med felmeddelanden om felmeddelanden visas. När du har åtgärdat felen öppnar du kommandotolken. Skriv `IISReset` så stoppas IIS och startas om. Återgå till föregående sida, ange etableringsinformationen igen och tryck på **Skicka**.) I Microsofts registreringstjänst skapas ett serverlicensieringscertifikat som returneras till konfigurationsdatabasen inom några minuter. Eftersom det här är den första servern i den domän där RMS är installerat är det i det här steget av processen som rotinstallationsservern registreras.

Om du har valt alternativet offlineregistrering registrerar du servern på Microsofts registreringstjänst manuellt när etableringsprocessen är slutförd. Registreringsprocessen måste vara slutförd innan du börjar att använda servern. Mer information finns i ”Så här registrerar du en rotcertifikatserver manuellt” i ”Använda en RMS-server” i dokumentationen.

När du har etablerat och registrerat en server ändras länkarna på sidan **Global administration**. Länken **Etablera RMS på den här webbplatsen** ändras till länken **Administrera RMS på den här webbplatsen**, länken **Lägg till den här servern i ett kluster** ersätts med länken **Ändra RMS-tjänstkonto** och länken **Ta bort RMS från den här webbplatsen** läggs till på sidan.

Den första servern skapar rotinstallationen av RMS. Rotinstallationen kan bestå av en enskild server eller av ett kluster. När du har slutfört installationen och etableringen av den första servern kan du installera ytterligare servrar och konfigurera stöd för redundans och belastningsutjämning för certifierings- och licensieringstjänsterna.

När konfigurationen är färdig måste du registrera tjänstens anslutningspunkt i rotcertifikatklustret i Active Directory så att tjänsten kan hittas med RMS-aktiverade klienter. Mer information finns i ”Registrera RMS-tjänstens anslutningspunkt” i ”Använda en RMS-server”. Om inte anslutningspunkten registreras kan inte RMS-klienten användas med RMS.

| ![](images/Cc747756.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du måste slutföra installationen och etableringen av RMS på den första servern innan du installerar av RMS på någon annan server. RMS har funktioner för innehållsskydd för Active Directory-grupper vars medlemskap sträcker sig över flera skogar. Om det inte finns flera skogar eller funktioner för det i organisationen kan du optimera prestanda i processen för utfärdande av användarlicenser på RMS-servern genom att modifiera klusterprincipen **MaxCrossForestCalls** i RMS-konfigurationsdatabasen. Den här principen anger hur många gånger ett gruppmedlemskap kan korsa skogsgränser. Standardvärdet är 10. Om du vill ändra det värdet till 0 använder du följande SQL-kommando:`update DRMS_ClusterPolicies set PolicyData=0 där PolicyName='MaxCrossForestCalls'` |

I följande avsnitt hittar du detaljerade instruktioner om vad som krävs för att slutföra de åtgärder som är tillgängliga från sidan Global administration i RMS:

-   Information om hur du använder installationsguiden till att installera den första servern finns i ”Så här installerar du RMS med Service Pack 1” i ”Använda en RMS-server”.
-   Information om hur du etablerar den första servern finns i ”Så här etablerar du den första rotcertifikatservern” i ”Använda en RMS-server”.
-   Information om hur du lägger till servrar till rotinstallationen och skapar ett kluster finns i ”[Lägga till servrar för hantering av certifiering och licensiering](https://technet.microsoft.com/089ceb62-2a96-444f-ab42-1d5deaabd0c3)”.
