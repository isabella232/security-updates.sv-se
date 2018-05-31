---
TOCTitle: Aktivera och inaktivera loggning
Title: Aktivera och inaktivera loggning
ms:assetid: '50ccd827-2d39-41e7-a395-3d5f5836869b'
ms:contentKeyID: 18124731
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747565(v=WS.10)'
---

Aktivera och inaktivera loggning
================================

Du aktiverar och inaktiverar loggning för det aktuella klustret eller den aktuella servern från sidan **Loggningsinställningar**. När du inaktiverar loggning skickar inte RMS-webbtjänsterna några data till loggningsmeddelandekön. Även lyssnartjänsten för loggning stoppas. Det går inte att aktivera och inaktivera loggning med administrationsverktyget Tjänster i Windows Server 2003.

RMS-loggningsmeddelanden skickas med Message Queuing till databasservern. Om det inte finns någon anslutning till databasservern lagras loggningsmeddelandena i ett lokalt cacheminne med Message Queuing tills anslutningen har återställts. Första gången du aktiverar loggning måste du kontrollera att RMS-servern är ansluten till databasservern och att databastjänsten har startats. Om du använder SQL Server som databasserver kan du kontrollera att loggningsmeddelandena skrivs till databasen med hjälp av följande steg:

-   Gå till loggningsdatabasen i SQL Server Enterprise Manager, expandera **Databases** och expandera databasen som innehåller RMS-loggningsdatabasen.
-   Klicka på loggningsdatabasen, klicka på **Tabeller**, högerklicka på **DRMS\_log\_master** och klicka sedan på **Öppna tabell - returnera alla rader**. Om loggfiler skapas ser du en eller flera loggfiler.
