---
TOCTitle: 'RMS-administrationsproblem'
Title: 'RMS-administrationsproblem'
ms:assetid: '97013c08-d3fa-4ea0-8914-995b6c97f900'
ms:contentKeyID: 18124827
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747605(v=WS.10)'
---

RMS-administrationsproblem
==========================

När du har etablerat RMS på servern kan du stöta på problem under den dagliga administrationen. Du kan använda informationen i följande avsnitt till att lösa några av de problemen.

Du får meddelandet ”SQL Server saknas eller åtkomst nekad” när du försöker att öppna webbplatsen Administration av RMS.
-----------------------------------------------------------------------------------------------------------------------

Om du har installerat RMS med en SQL Server 2005-installation som databasserver kan det hända att SQL Server-tjänsten inte startas. I SQL Server 2005 är MSSQLSERVER-tjänsten inte konfigurerad så att den startas automatiskt när servern startas. Om du har startat om SQL-servern efter RMS-installationen och inte har konfigurerat tjänsten till att startas om automatiskt kommer RMS inte att fungera. Du har då bara åtkomst till sidan Global administration av RMS.

När du har startat MSSQLSERVER-tjänsten måste du starta om IIS på RMS-servern för att RMS-funktionerna ska återställas.

Offlineregistreringen kan inte slutföras
----------------------------------------

Om filen med registreringsbegäran inte är komplett eller om den har ändrats innan den skickades till webbplatsen för registreringstjänsten kan offlineregistreringen inte slutföras. Filen med registreringsbegäran kan ha blivit skadad av ett skadligt program, användarfel eller systemfel.

Beroende på vilken information som saknas kan filen ändå accepteras på registreringswebbplatsen och ett serverlicensieringscertifikat skickas tillbaka, eller så kan registreringsbegäran nekas och ett felmeddelande visas.

Om du får tillbaka ett serverlicensieringscertifikat anges det vilka fel som finns och vilka uppgifter som saknas i filen med registreringsbegäran. Du får också ett felmeddelande i RMS när du försöker importera certifikatet.

Om du inte kan slutföra registreringsprocessen bör du kontrollera att datorn med Internetuppkoppling inte har några virus, exportera filen med registreringsbegäran från RMS-servern igen och använda ett annat lagringsmedium för att flytta den till datorn med Internetuppkoppling. Om du får samma fel igen kontaktar du Microsofts kundservice.

Inga loggfiler skapas
---------------------

För loggningstjänsten i RMS krävs både tjänsten Message Queuing (även kallad MSMQ) och tillgång till loggningsdatabasen. Om inga loggfiler skapas kan det bero på att någon av komponenterna inte har konfigurerats på rätt sätt eller att kommunikationen mellan komponenterna störs.

Kontrollera att RMS-servern och databasservern är anslutna till nätverket. Om de är anslutna kan du använda följande procedur till att kontrollera inställningarna för RMS-loggningstjänsten och att alla programvaruberoenden är korrekt konfigurerade.

Först kontrollerar du att konfigurationen för Message Queuing är korrekt. Message Queuing måste vara installerat med Active Directory-integrering aktiverat.

**Så här kontrollerar du att Message Queuing har installerats och konfigurerats korrekt**
1.  I **Kontrollpanelen** klickar du på **Lägg till eller ta bort program**. Klicka på **Lägg till/ta bort Windows-komponenter** så öppnas guiden **Windows-komponenter**.

2.  I guiden **Windows-komponenter** markerar du kryssrutan **Programserver** och klickar på **Information**.

3.  Markera kryssrutan **Message Queuing** och klicka sedan på **Information**.

4.  Om kryssrutan **Active Directory-integration** är markerad går du vidare till nästa test och kontrollerar att Message Queuing körs. Om kryssrutan inte är markerad går du igenom steg 5 till 9.

5.  Klicka på **Start**, peka på **Alla Program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** och öppna sidan Global administration.

6.  Klicka på **Ta bort RMS från den här webbplatsen** bredvid den webbplats där RMS är etablerat och klicka sedan på **OK**.

7.  Välj **Lägg till eller ta bort program** på **Kontrollpanelen**, klicka på **Lägg till/ta bort Windows-komponenter**, klicka på **Programserver**, klicka på **MSMQ**.

8.  Klicka på **Information**, markera kryssrutan **Active Directory-integration** och klicka sedan på **OK** om du vill aktivera **Active Directory-integration**.

9.  Öppna sidan **Global administration**. Klicka på **Etablera RMS på den här webbplatsen** bredvid namnet på den webbplats där du vill etablera RMS.

Steg två är att kontrollera att Message Queuing körs på servern.

**Så här kontrollerar du att Message Queuing körs på servern**
1.  I **Kontrollpanelen** klickar du på **Administrationsverktyg** och sedan på **Tjänster**.

2.  Bläddra nedåt i listan över tjänster tills du hittar **Message Queuing**-tjänsten.

3.  Tjänsten ska anges som **Startad** i **Status**-kolumnen. Om den inte är det högerklickar du på tjänsten och klickar på **Starta**.

Steg tre är att kontrollera att loggningstjänsten har behörighet att skriva händelser till loggningsdatabasen. Loggningstjänsten i RMS körs via RMS-tjänstkontot. Kontrollera att RMS-tjänstkontot har en giltig inloggning till databasservern och att den har behörigheter för att skapa databaser och skriva information till filerna.

När de här kraven är uppfyllda stänger du och startar om loggningstjänsten i RMS med hjälp av snapin-modulen Tjänster. När loggningstjänsten har startats om ska loggningsfiler skapas på databasservern. Om du använder en SQL-server som databasserver gör du enligt följande för att kontrollera att loggfiler skapas.

**Så här kontrollerar du att loggfiler skapas på SQL-servern**
1.  Gå till loggningsdatabasen i SQL Server Enterprise Manager, expandera **Databaser** och expandera databasen som innehåller RMS-loggningsdatabasen.

2.  Klicka på loggningsdatabasen, klicka på **Tabeller**, högerklicka på **DRMS\_log\_master** och klicka sedan på **Öppna tabell - returnera alla rader**. Om loggfiler skapas ser du en eller flera loggfiler.

Återställa konfigurationsdatabasen
----------------------------------

RMS fungerar inte utan en korrekt fungerande konfigurationsdatabas. Om du har några problem med konfigurationsdatabasen, t.ex. skadade databaser eller hårddiskproblem på servern, kan du återställa RMS-funktionerna genom att återställa en säkerhetskopia av konfigurationsdatabasen. Om du vill återställa RMS-konfigurationsdatabasen från en säkerhetskopia behöver du följande information:

-   Namnet på den senaste säkerhetskopian av databasen.
-   Namnet på den dator där säkerhetskopian av databasen ska återställas.
-   Det kontonamn och lösenord som användes vid den ursprungliga etableringen av RMS.
-   Det lösenord som ursprungligen användes för det programvarubaserade skyddet av nycklar (om den metoden användes).

För återställning från den säkerhetskopierade databasen krävs inget nytt serverlicensieringscertifikat eller någon ny privat nyckel eftersom RMS behåller alla inställningar (som kommer från den säkerhetskopierade konfigurationsdatabasen).

Du kan återställa en säkerhetskopierad databas genom att utföra följande steg.

**Så här återställer du en säkerhetskopierad databas**
1.  Klicka på **Start**, peka på **Alla Program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** och öppna sidan **Global administration**.

2.  Klicka på **Ta bort RMS från den här webbplatsen** bredvid den webbplats där RMS är etablerat och klicka sedan på **OK**.

3.  Återställ de säkerhetskopierade databasfilerna för konfigurationsdatabasen. Om du dessutom säkerhetskopierade loggningsdatabasen och vill behålla datahistoriken ska du även återställa loggningsdatabasen.

    -   Om systemet återställs efter ett omfattande systemfel återställer du registret med hjälp av säkerhetskopian av systemtillståndet innan du återställer de säkerhetskopierade databasfilerna.

4.  Om de databaser som återställs är från en enskild rotcertifikatserver ändrar du följande registernyckel innan du etablerar tjänsten:

    -   På datorer där 32-bitarsversionen av Windows Server 2003 körs:
        `HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\1.0\`
    -   På datorer där 64-bitarsversionen av Windows Server 2003 körs:
        `HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\DRMS\1.0\`

    Lägg till följande värde och låt det vara tomt:

    `GicURL`

    På så sätt åsidosätts identifieringen av rotcertifikatservern via Active Directory, så att du kan komma åt etableringssidorna för rotcertifikatservern.

5.  Om du skyddade den privata RMS-nyckeln med en HSM återställer du även säkerhetsmiljön så att det går att hämta nycklarna.

6.  Använd någon av följande metoder:

    -   Klicka på Etablera RMS på den här webbplatsen bredvid den webbplats där du vill etablera RMS om du vill återställa databasen för en enskild server och inte för ett kluster.
        eller
    -   Klicka på Lägg till den här servern i ett kluster bredvid den webbplats där du vill etablera RMS om du vill återställa databasen för ett kluster.

7.  Ange det RMS-tjänstkonto som användes vid den ursprungliga etableringen av servern.

8.  Ange vilken säkerhetskopierad konfigurationsdatabas du vill använda (inklusive databasens namn och namnet på den dator där databasen finns).

9.  Ange det lösenord som användes vid den ursprungliga etableringen av servern.

10. Klicka på **Skicka**.

Etableringsprocessen startas och RMS etableras på nytt på servern.

Mer information finns i Planera systemåterställning, och Säkerhetskopiera och återställa systemet för RMS, i Planera en RMS-distribution.

Lösenordet för RMS-tjänstkontot har upphört att gälla
-----------------------------------------------------

Om RMS slutar att fungera kan det bero på att RMS-tjänstkontots lösenord har upphört att gälla. Kontrollera det i IIS Manager. Om RMS-programpoolen stoppas och du inte kan starta om den kan RMS-tjänstkontot ha upphört att gälla.

Om RMS-tjänstkontot upphör att gälla måste du först ändra lösenordet på varje RMS-server som använder det konto vars lösenord har upphört att gälla, och sedan starta om IIS. Mer information finns i ”Ändra RMS-tjänstkontots lösenord” i ”Använda en RMS-server”.

Återställa en tidigare RMS-installation
---------------------------------------

Om det uppstår fel på maskinvaran eller programvaran på RMS-servern kan du återställa den genom att använda en tidigare installerad konfigurationsdatabas till att etablera en ny serverinstans.

| ![](images/Cc747605.note(WS.10).gif)Obs!                                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Den här processen gäller bara om det uppstår fel på servern där RMS körs. Om det uppstår fel på servern med konfigurationsdatabasen läser du ”Återställa konfigurationsdatabasen” tidigare i avsnittet. Om RMS-servern även är databasserver måste du återställa hela servern från en säkerhetskopia. |

Använd samma konfigurationsdatabas som vid den ursprungliga installationen.

**Så här återställer du en tidigare RMS-installation**
1.  Logga in på den dator som du vill konfigurera som RMS-server med ett konto som har administratörsbehörigheter. Kontrollera att datorn uppfyller systemkraven för RMS. Mer information om systemkraven för RMS finns i ”Maskinvarukrav” för RMS i ”Planera en RMS-distribution”.

2.  Om du skyddar de privata RMS-nycklarna med en HSM måste du kontrollera att den är korrekt konfigurerad och att samma inställningar och säkerhetsmiljö används som i den tidigare RMS-installationen.

3.  Installera RMS på datorn.

4.  Klicka på **Start**, peka på **Alla Program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** och öppna sidan **Global administration**, när du har slutfört RMS-installationen.

5.  Klicka på **Lägg till den här servern i ett kluster** bredvid den webbplats där du vill etablera RMS.

6.  Skriv in namnet på och lösenordet för det RMS-tjänstkonto som normalt används för de vanligaste åtgärderna i RMS vid **RMS-tjänstkonto**. Använd formatet domännamn\\användarnamn. Kontot måste vara ett domänkonto.

7.  Skriv in databasserverns namn och namnet på konfigurationsdatabasen för den ursprungliga RMS-installationen som du återställer vid **Konfigurationsdatabas**.

8.  Välj önskat skydd av den privata nyckeln i klustret vid **Skydd av privat nyckel**. Om det programvarubaserade standardskyddet för nycklar användes anger du det lösenord som användes vid kryptering av den privata nyckeln när det första klustret etablerades.

9.  Klicka på **Skicka**.

Klienterna kan inte öppna RMS-skyddat innehåll på grund av att behörigheterna upphört att gälla
-----------------------------------------------------------------------------------------------

Om en användares behörighet inte är giltig längre kan han eller hon inte använda RMS-skyddat innehåll. Om systemklockan på RMS-server går före systemklockan på RMS-klienten kan användaren också få problem att använda RMS-skyddat innehåll, även om behörigheten inte har gått ut. Om systemklockorna på de två datorerna inte är synkroniserade kan följande felmeddelande visas när innehållet ska öppnas på klientdatorn:

**Din behörighet har upphört att gälla och du kan inte öppna det här meddelandet. Vill du öppna med en annan inloggning?**

Både klientlicensen och innehållslicensen är giltiga, men skillnaden i tid gör att klienten tolkar innehållslicensen som ogiltig och returnerar det här felmeddelandet till användaren. Det kan få användare att tro att de har problem med sina RMS-kontocertifikat eller med de rättigheter som beviljats dokumentet. Så fort klockan på klienten har nått det giltiga tidsintervallet för publiceringslicensen kommer användaren att kunna öppna innehållet.

Du bör se till att både klienter och servrar i RMS-systemet synkroniseras efter samma tidstjänst.

Felmeddelandet ”Åtkomst nekad” visas när händelser ska loggas i programhändelseloggen i RMS
-------------------------------------------------------------------------------------------

Komponenter som körs från en ASP-sida, t.ex. RMS, skapas som standard under kontot IUSR\_COMPUTERNAME. Det kontot tillhör gruppen Gäster, och de säkerhetsbehörigheter som krävs för att skriva till programhändelseloggen gör att gästkonton hindras från att skriva data till den.

Du kan komma förbi problemet genom att ändra den registernyckel som styr över funktionen i registereditorn.

| ![](images/Cc747605.Caution(WS.10).gif)Varning!                                                                              |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du ändrar registret på ett felaktigt sätt kan du skada systemet. Säkerhetskopiera alla viktiga data på datorn innan du ändrar registerinställningarna. |

Ange värdet för följande registernyckel till 0 i stället för 1 och starta om datorn så att inställningarna börjar att gälla.

`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\EventLog\Application`

Namn: `RestrictGuestAccess`

Typ: `REG_DWORD`

| ![](images/Cc747605.note(WS.10).gif)Obs!               |
|-------------------------------------------------------------------------------------|
| På så sätt kan alla gästkonton användas till att skriva till programhändelseloggen. |

Mer information om vad som kan orsaka det här felet finns i en artikel om hur du aktiverar loggning från ASP-sidor på [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=44167).
