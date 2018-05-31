---
TOCTitle: 'Så här installerar du Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) för att få databasfunktioner i RMS'
Title: 'Så här installerar du Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) för att få databasfunktioner i RMS'
ms:assetid: 'c9b9cd08-98c4-424f-b3fc-d685f57c002e'
ms:contentKeyID: 18124895
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747667(v=WS.10)'
---

Så här installerar du Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) för att få databasfunktioner i RMS
=============================================================================================================

Installera Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) för att få databasfunktioner i RMS
--------------------------------------------------------------------------------------------------

#### Så här installerar du Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) för att få databasfunktioner i RMS

1.  Logga in med ett domänkonto som är medlem av den lokala administratörsgruppen på den server där du vill installera Microsoft SQL Server 2000 Desktop Engine (MSDE 2000).

2.  Hämta MSDE 2000 från [Microsofts webbplats](http://www.microsoft.com/) (http://www.microsoft.com/) och spara det lokalt på datorn.

3.  Kör filen MSDE2000A.exe och extrahera MSDE 2000-installationspaketet till en mapp. Som standard kommer den här mappen att heta MSDERelA men du kan ange ett annat namn.

4.  Öppna en kommandoprompt och navigera till den plats där du sparade MSDE 2000-installationen.

5.  Skriv in nedanstående kommando, så installeras Microsoft SQL Server 2000 Desktop Engine med en konfiguration som fungerar med RMS. Ersätt *lösenord* med ett eget starkt lösenord:

    **Setup.exe /i setup\\sqlrun10.msi INSTANCENAME=RMS DISABLEAGENTSTARTUP=1 SAPWD=***lösenord*

    | ![](images/Cc747667.Important(WS.10).gif)Viktigt!                                                                                                                                                                                       |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | MSDE-tjänsten måste startas efter att den har installerats. Du kan starta tjänsten från **Tjänster** i **Kontrollpanelen**. Vi rekommenderar att tjänsten konfigureras så att den startas automatiskt. På så sätt är MSDE-databasen alltid tillgänglig när RMS körs. |

Etablera inte RMS på en server förrän du har installerat en databas som stöder RMS-konfigurationsdatabasen.

Vi rekommenderar att Microsoft SQL Server Desktop Engine endast används tillsammans med RMS-databaser i testmiljö, eftersom Microsoft SQL Server Desktop Engine inte innehåller alla verktyg som behövs för att fungera med en databas i företagsskala. Eftersom MSDE inte har funktioner för fjärrnätverk måste du installera det på samma server som RMS och du kan då inte lägga till fler RMS-servrar i RMS-klustret. Dessutom anger villkoren för användning av Microsoft SQL Server Desktop Engine att du inte får använda SQL Server-klientverktygen till att ändra en Microsoft SQL Server Desktop Engine-databas. Med den här begränsningen kan du inte säkerhetskopiera eller återställa RMS-konfigurationsdatabasen, visa loggningsinformation eller ändra data som lagrats i konfigurationsdatabasen direkt.
