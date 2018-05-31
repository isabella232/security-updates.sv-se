---
TOCTitle: 'Använda RMS-skyddat innehåll'
Title: 'Använda RMS-skyddat innehåll'
ms:assetid: '3cf6d64b-1187-433c-bbb2-c68069bc3c30'
ms:contentKeyID: 18124706
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720251(v=WS.10)'
---

Använda RMS-skyddat innehåll
============================

När en användare använder skyddat innehåll sker två processer obemärkt för användaren. Först begärs en användarlicens från det RMS-skyddade programmet när användaren öppnar dokumentet. Därefter kontrolleras användarlicensen för att avgöra om den kräver en återkallelselista och om något certifikat som ingår i programmets eller rättighetskontocertifikatets förtroendekedja har återkallats. När båda processerna har genomförts återges det RMS-skyddade innehållet, förutsatt att alla rättigheter och återkallelser medger detta.

Om en återkallelselista krävs letar programmet efter en lokal kopia av listan som inte har överskridit sista giltighetsdatum. Om det är nödvändigt hämtar programmet ett aktuellt exemplar av listan. Programmet tillämpar sedan alla eventuella återkallelsevillkor som är relevanta i den aktuella situationen.

Om inget återkallelsevillkor blockerar åtkomst av innehållet återger programmet innehållet och användaren kan utöva de rättigheter han eller hon har beviljats.

Du kan konfigurera RMS så att licensbegäran från autentiserade externa användare kan behandlas. Detta medför att användare kan dela skyddat innehåll via Internet.

I detta avsnitt behandlas följande:

-   [Skaffa en användarlicens](https://technet.microsoft.com/0b6cde34-418a-4dee-9d27-b65b93b535ac)
-   [Användarlicenser och externa användare](https://technet.microsoft.com/02db9bda-180e-438f-863d-26252083a471)
