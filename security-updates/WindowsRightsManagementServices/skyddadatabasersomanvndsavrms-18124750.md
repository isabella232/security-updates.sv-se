---
TOCTitle: Skydda databaser som används av RMS
Title: Skydda databaser som används av RMS
ms:assetid: '65802f9a-81bc-4398-968a-00c9b1dca2fa'
ms:contentKeyID: 18124750
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720285(v=WS.10)'
---

Skydda databaser som används av RMS
===================================

Med RMS skapas och används tre databaser med olika säkerhetskrav enligt följande:

-   **Katalogtjänster**. I den här databasen cachelagras resultaten från Active Directory-gruppmedlemskapsfrågor. Eftersom den bara innehåller Active Directory-information krävs ingen ytterligare säkerhet än den säkerhet som konfigureras automatiskt under etableringen av RMS.
-   **Loggning**. Informationen i den här databasen är känsligare än informationen i katalogtjänstdatabasen, eftersom den kan äventyra användarnas sekretess om den hamnar hos obehöriga. Microsoft har lagt stor vikt vid att se till att ingen personlig information loggas i databasen och att den information som loggas skyddas med lämpliga säkerhetsmetoder. Inga ytterligare ändringar av databasens säkerhet behövs, såvida inte databasen flyttas till en annan dator där SQL Server körs. Om databasen flyttas till en annan server bör du kontrollera att samma skyddsmekanismer används i den nya miljön.
-   **Konfiguration**. Det här är den viktigaste och mest värdefulla resursen i RMS-distributionen med undantag för serverns privata nycklar. Den innehåller känslig och viktig information som måste skyddas omsorgsfullt. Utöver konfigurationsinformation innehåller den alla certifikat och nycklar, serverns krypterade privata nyckel (såvida du inte använder den rekommenderade maskinvarukrypteringen) och hashvärdet för den privata nyckelns lösenord.

När konfigurationsdatabasen skapas i RMS skyddas den med hjälp av behörigheter som begränsar åtkomsten till databasen.

Höja databassäkerheten
----------------------

Du kan använda de steg som beskrivs nedan till att höja den allmänna säkerheten för de databaser som finns i nätverks- och servermiljön:

-   Kör databasservern på en dator där Windows Server 2003 körs, eftersom det som standard är säkrare än Windows 2000 Server. Även om du kan låsa Windows 2000 Server-baserade datorer är det en tidskrävande process, och om du gör fel kan användare med skadligt uppsåt komma åt databasen.
-   Begränsa den fysiska åtkomsten till databasservern.
-   Kontrollera att databasbehörigheter och DACL-listor till databasfiler endast beviljar behörig personal åtkomst. De standardbehörigheter och DACL-listor som konfigureras med RMS är säkra. Var försiktig när du ändrar standardinställningar.
-   Kör inga onödiga tjänster på databasservern, t.ex. Microsoft Internet Information Services (IIS), Message Queuing och Terminal Services.
-   Kör inga andra databaser på databasservern utöver RMS-databaserna.

Skydda SQL Server-databaser genom att konfigurera antingen SSL eller IPSec (Internet Protocol Security) för kryptering av kanaler. Genom att kryptera databaskommunikationen förhindrar du att användare med skadligt uppsåt kommer över eller ändrar loggade data.

Mer information om konfigurering av SSL för SQL Server 2000 finns på webbplatsen för MSDN ([http://go.microsoft.com/fwlink/?LinkId=17060](http://go.microsoft.com/fwlink/?linkid=17060)).

Mer information om konfigurering av IPsec för SQL Server 2000 finns på webbplatsen för MSDN ([http://go.microsoft.com/fwlink/?LinkId=17061](http://go.microsoft.com/fwlink/?linkid=17061)).

Mer information om hur du skyddar Microsoft Windows Server 2003-familjen med operativsystem finns i "Windows Server 2003 Security Guide" som kan erhållas från Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkId=36719](http://go.microsoft.com/fwlink/?linkid=36719)).
