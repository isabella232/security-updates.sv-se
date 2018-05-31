---
TOCTitle: Webbplatsen Administration av RMS
Title: Webbplatsen Administration av RMS
ms:assetid: 'f003c1d9-9a17-4e50-9e1e-5d67677552a0'
ms:contentKeyID: 18124977
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747796(v=WS.10)'
---

Webbplatsen Administration av RMS
=================================

Varje rotkluster och licensieringskluster har en administrationswebbplats som du kan använda till hantering av RMS. Webbplatsen är bara tillgänglig på den RMS-server som du administrerar eller via en Fjärrskrivbord-anslutning.

I det här avsnittet beskrivs vilka möjligheter som finns på webbplatsen för administration. Instruktioner för hur du kan använda webbplatsen till att administrera RMS finns i "Så här gör du i RMS" och "Hantera RMS" i "RMS: Åtgärder" i den här dokumentationssamlingen.

**Obs!   **Konfigurering av kluster ska ske globalt. Du kan sköta konfigureringen av kluster på valfri server i klustret via webbplatsen för administration.

Öppna webbsidan **Global administration** om du vill göra något av följande:

-   Etablera RMS för en webbplats.
-   Etablera en server och lägga till den i ett kluster.
-   Ta bort RMS från en webbplats.
-   Gå till administrationssidorna för klustret.

Öppna webbsidan **Administration** för ett kluster om du vill göra något av följande:

-   **Visa klusterinformation.**Du kan t.ex. visa följande information som rör klustret: Installations-URL, server-URL, certifikatnamn, server för konfigurationsdatabasen, namn på konfigurationsdatabasen samt förfallodatum för certifikat.
-   **Registrera eller förnya serverlicensieringscertifikatet.**Du kan registrera eller förnya serverlicensieringscertifikatet för klustret.
-   **Upprätta principer för förtroenden.**Klicka på länken om du vill öppna webbsidan Principer för förtroenden där du kan lägga till eller ta bort betrodda användardomäner och betrodda publiceringsdomäner. Lägga till eller ta bort användare från exkluderingslistan i en betrodd användardomän. Exportera ditt serverlicensieringscertifikat till en fil som kan importeras av en annan RMS-installation.
-   **Konfigurera principmallar för rättigheter.**Klicka på länken om du vill öppna webbsidan Principmallar för rättigheter, där du kan skapa och ändra principmallar för rättigheter för företaget.
-   **Konfigurera loggning.**Klicka på länken om du vill öppna webbsidan Loggningsinställningar, där du kan aktivera och inaktivera loggning samt visa loggningsservern och -databasen.
-   **Ange extranätets kluster-URL.**Klicka på länken om du vill öppna webbsidan Inställningar för extranätets kluster-URL, där du kan ange URL som ska användas för åtkomst av rotklustrets certifieringstjänster från extranätet.
-   **Ange RMS-proxyinställningar.**Klicka på länken och öppna sidan RMS-proxyinställning, där du anger proxyserverns adress, autentiseringstyp och det användarnamn som ska användas när RMS-servern ansluts till Internet via en proxyserver.
-   **Hålla reda på antalet distribuerade rättighetskontocertifikat.**Klicka på länken om du vill öppna webbsidan med certifieringsrapporter för rättighetskontocertifikat där du kan se hur många rättighetskontocertifikat som distribuerats med rotklustret. Det här antalet kan du använda till grund för att uppskatta hur många licenser för klientåtkomst du behöver.
-   **Hantera säkerhetsinställningar.**Klicka på länken om du vill öppna webbsidan Säkerhetsinställningar. Där kan du lägga till och ta bort medlemmar i gruppen RM-ansvariga, som har full kontroll över allt licensierat innehåll, samt ange nytt lösenord för den privata nyckeln.
-   **Visa och konfigurera inställningar för kontocertifikat.**Klicka på länken om du vill öppna webbsidan Certifieringsinställningar, där du kan ange hur länge ett certifikat ska vara giltigt och ange kontaktuppgifter för administratörer.
-   **Aktivera exkluderingsprinciper.**Klicka på länken om du vill öppna webbsidan Exkluderingsprinciper, där du kan aktivera exkluderingsprinciper som baseras på lockbox-version, Windows-version, kontocertifikat och program.
-   **Registrera RMS-tjänstens anslutningspunkt.**Klicka på länken om du vill öppna webbsidan RMS-tjänstens anslutningspunkt, där du kan registrera och avregistrera RMS-tjänstens anslutningspunkt för klustret.

Administratörer kan utföra andra uppgifter, t.ex. övervaka händelser och hantera Active Directory, Internet Information Services (IIS) samt SQL Server, med hjälp av Microsoft Management Console (MMC).
