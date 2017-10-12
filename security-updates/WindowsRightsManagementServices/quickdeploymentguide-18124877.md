---
TOCTitle: Quick deployment guide
Title: Quick deployment guide
ms:assetid: 'b8fb69b6-3e0b-4836-8c05-8bd93f522a7c'
ms:contentKeyID: 18124877
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747735(v=WS.10)'
---

Quick deployment guide
======================

Den här guiden är avsedd som hjälp att snabbt konfigurera en server där RMS med Service Pack 1 körs så att du kan utvärdera den och avgöra om du vill utföra en vidare distribution över hela organisationen.

**Steg 1 - Förbereda för RMS**

RMS är beroende av andra komponenter som måste installeras och konfigureras innan du kan använda tjänsten. När du har utfört följande steg kommer infrastrukturen att uppfylla grundkraven för RMS.

1.  Konfigurera en dator där Windows Server 2003 körs och anslut sedan datorn till en Active Directory-domän. (För mindre organisationer som bara har en server kan datorn också fungera som domänkontrollant för Active Directory. Men i sådana fall måste datorn användas med Windows Server 2003 Standard Edition, Windows Server 2003 Enterprise Edition eller Windows Server 2003 Datacenter Edition. Det går inte att använda Windows Server 2003 Web Edition som domänkontrollant.)
2.  Konfigurera servern så att den fungerar som **programserver**. Det gör du genom att klicka på **Start**, välja **Kontrollpanelen** och sedan dubbelklicka på **Lägg till eller ta bort program**. Klicka på **Lägg till eller ta bort Windows-komponenter** i **Lägg till eller ta bort program** och kontrollera att följande tjänster är aktiverade under **Programserver**:
    -   **ASP.NET**
    -   **Internet Information Services (IIS)**
    -   **Message Queuing**

    Acceptera standardalternativen för alla tjänster. Ingen ytterligare konfiguration krävs.
3.  Konfigurera en databasserver med ett av följande databasprogram:
    -   Microsoft® SQL Server 2000 med SP3a. Det här kan vara en lokal installation av SQL Server 2000 eller en fjärrinstallation som finns i samma domän.
    -   Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) Release A. Det här programmet måste installeras lokalt. Du kan hämta MSDE 2000 från [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=17799) (http://go.microsoft.com/fwlink/?LinkID=17799).

    Vi rekommenderar att Microsoft SQL Server Desktop Engine endast används tillsammans med RMS-databaser i testmiljö, eftersom Microsoft SQL Server Desktop Engine inte innehåller alla verktyg som behövs för att fungera med en databas i företagsskala. Eftersom MSDE inte har funktioner för fjärrnätverk måste du installera det på samma server som RMS och du kan då inte lägga till fler RMS-servrar i RMS-klustret. Dessutom anger villkoren för användning av Microsoft SQL Server Desktop Engine att du inte får använda SQL Server-klientverktygen till att ändra en Microsoft SQL Server Desktop Engine-databas. Med den här begränsningen kan du inte säkerhetskopiera eller återställa RMS-konfigurationsdatabasen, visa loggningsinformation eller ändra data som lagrats i konfigurationsdatabasen direkt.
4.  Ge tjänsten ett namn som användarna ser när de ansluter till tjänsten via intranätet (t.ex. http://certifiering.konto.se). Konfigurera DNS (Domain Name System) så att den URL:en matchas mot RMS-datorns IP-adress. Du bör använda ett fullständigt kvalificerat domännamn till kluster-URL:en så att klienter i andra DNS-zoner kan identifiera IP-adressen till RMS-servern eller -servrarna.
5.  Skapa ett administratörskonto för användning med RMS.
6.  Du är nu klar att installera RMS SP1. Fler instruktioner om det här steget finns i ”Så här installerar du RMS med Service Pack 1” i ”Använda en RMS-server”.

**Vanliga extrafunktioner**

Följande funktioner är valfria. Om du väljer att använda dem bör du kontrollera att du gjort alla förberedelser innan du startar installations- och etableringsprocessen för RMS:

-   Du kan konfigurera RMS så att en HSM (Hardware Security Module) används för lagring av privata nycklar. Kontrollera att enheterna är korrekt konfigurerade och att säkerhetsmiljön har definierats om du tänker använda en HSM.
-   Du kan hämta ett serverlicensieringscertifikat automatiskt under etableringsprocessen om RMS-datorn är ansluten till Internet. Om organisationen använder proxyserver till att ansluta till Internet kontrollerar du proxyinställningarna i Internet Explorer, t.ex. eventuella autentiseringskrav, och sparar dem för senare användning.
-   Om du kör RMS på en domänkontrollant och tänker använda ett användarkonto till att köra RMS-tjänsterna kontrollerar du att Säkerhetsprincip för domänkontrollant är konfigurerat så att användarkontot beviljas behörigheter att logga in lokalt. Mer information om hur du konfigurerar Säkerhetsprincip för domänkontrollant finns i Hjälp- och supportcenter i Windows Server 2003.

**Steg 2 - Etablera den första RMS-servern**

Etablering är den process då en webbplats konfigureras med RMS så att användare kan börja använda tjänsten. Du etablerar organisationens rotcertifikatserver genom att följa instruktionerna nedan:

1.  Logga in på datorn med ett domänanvändarkonto som även har administratörsbehörigheter på den lokala datorn. Om du installerar RMS på en domänkontrollant loggar du in som domänadministratör.
2.  Klicka på **Start**, peka på **Alla Program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** och öppna sidan **Global administration**. På den här sidan finns en lista över de webbplatser som är tillgängliga på den aktuella servern.
3.  Klicka på den webbplats där du vill etablera RMS och klicka sedan på **Etablera RMS på den här webbplatsen**. När sidan öppnas står det **Etablera RMS-rotcertifikatservern** längst upp på sidan.
4.  Fyll i aktuell information om organisationen på sidan.
    -   Skriv namnet på den tjänst som du konfigurerade i steg 4 ovan i rutan **Kluster-URL** (t.ex. certifiering.konto.se). Klicka på HTTPS-protokollet i listan över protokoll om du vill använda SSL med installationen. På så sätt aktiveras SSL. Däremot innebär inte alternativet att SSL krävs för RMS-webbtjänster. Det måste du konfigurera separat med IIS.
    -   Om servern ansluts till Internet via en proxyserver kompletterar du informationen i området **RMS-proxyinställningar** med den information som du har hämtat från Internet Explorer enligt beskrivningen i stycket med extrafunktioner i föregående procedur.
    -   I området **Internet-anslutning för server** väljer du alternativet **Online** om du vill att servern ska anslutas till Microsofts registreringstjänst via Internet och på så sätt få ett serverlicensieringscertifikat automatiskt under etableringsprocessen. Välj alternativet **Offline** om du vill ansluta manuellt till Microsofts registreringstjänst, hämta serverlicensieringscertifikatet och sedan importera det efter etableringen av RMS.
5.  Klicka på **Skicka**.
    Efter cirka 60 till 90 sekunder är etableringen slutförd och du kan återgå till sidan **Global administration** där du administrerar den nyetablerade RMS-servern.
6.  På sidan **Global administration** klickar du på **Administrera RMS på den här webbplatsen** så öppnas **administrationshemsidan** för RMS-servern.
    Om du valde Offline i området Internet-anslutning för server i steg 4 slutför du proceduren i ”Så här registrerar du en rotcertifikatserver manuellt” innan du fortsätter.
7.  Klicka på länken **RMS-tjänstens anslutningspunkt** på sidan Hemsida för Global administration.

| ![](images/Cc747735.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nästa steg i proceduren är att registrera en anslutningspunkt för tjänsten. Då krävs det att du använder ett domänkonto med tillräcklig behörighet för att få skapa ett behållarobjekt under tjänstbehållaren i Active Directory-skogens konfigurationsbehållare. Den fördefinierade säkerhetsgruppen **Företagsadministratörer** är ett exempel på ett konto med tillräckliga behörigheter. |

1.  På sidan för **RMS-tjänstens anslutningspunkt** klickar du på knappen för **registrering av URL**. På så sätt registreras RMS-tjänstens anslutningspunkt i Active Directory så att RMS-aktiverade program kan användas till att upptäcka RMS-tjänsterna för licensiering, aktiveringsproxy och certifiering.  

**Steg 3 - Testa RMS**

Innan du kan använda RMS fullt ut måste du installera Microsoft Windows Rights Management Services-klienten och ett RMS-aktiverat program på klientdatorerna. Användarna måste tillhöra Active Directory-domänen och klientdatorerna måste kopplas till domänen. Dessutom måste alla domänanvändare ha e-postadresser som är definierade i Active Directory. Så här testar du RMS:

1.  Logga in på klientdatorn som giltig domänanvändare.
2.  Installera RMS-klienten för Service Pack 1.
3.  Installera ett RMS-aktiverat program.
4.  Skapa en RMS-skyddad fil, tilldela alla rättigheter att läsa (men inte att skriva till) filen och spara den sedan i en utdelad mapp som användarna har fullständig åtkomst till.
5.  Logga in på datorn som en annan användare. Öppna filen och försök ändra den. Om RMS har installerats på rätt sätt kan du inte ändra filen.
