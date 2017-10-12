---
TOCTitle: Inaktivera RMS
Title: Inaktivera RMS
ms:assetid: 'dbcacce7-434d-48a7-a11d-ef9690d78b44'
ms:contentKeyID: 18124939
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747767(v=WS.10)'
---

Inaktivera RMS
==============

Med inaktivering avses hela processen när du tar bort en RMS-server och alla tillhörande databaser från organisationen. I den här processen kan du ta bort RMS från infrastrukturen utan att förlora åtkomsten till RMS-skyddad information. Följande är möjliga anledningar till varför en organisation kan behöva ta bort en RMS-server från infrastrukturen:

-   Överflyttning av en koncepttestad RMS-server från pilotmiljö till produktionsmiljö.
-   Förenkling av arkitekturen där licensieringsservrar tas bort och konsolideras i RMS-rotklustret.
-   Sammanfogning av RMS-servrar (t.ex. efter ett företagsköp eller samgående) där två RMS-infrastrukturer ska integreras.
-   Beslut att sluta använda RMS till att skydda innehåll.

En aktiv RMS-server är integrerad med både en databasserver och Active Directory och medför naturligtvis att stora mängder innehåll skyddas med en nyckel som finns på RMS-servern. Därför innebär en borttagning av RMS ur organisationen fler steg än att bara ta bort programmet från servern. I det här avsnittet förklaras de stegen så att du kan inaktivera RMS-servern om det blir nödvändigt.

Avsnittet behandlar:

-   [Introduktion till inaktiveringsprocessen](https://technet.microsoft.com/57bd9949-9433-437b-93ed-ffb2dff9992e)
-   [Aktivera inaktiveringstjänsten](https://technet.microsoft.com/45226e85-b50d-41cc-aca7-0f603f8509d5)
-   [Ange behörigheter för virtuella kataloger](https://technet.microsoft.com/45112111-9608-45b1-9a86-7b313d0a1579)
-   [Ta bort RMS-skydd från innehåll](https://technet.microsoft.com/c30361e3-50d2-4474-a87d-d38de502cf9e)
-   [Ta bort webbtjänsten (Inaktivera RMS)](https://technet.microsoft.com/68b4e2b0-b1b7-4b0a-8c1a-82ac27c1f12e)
-   [Ta bort RMS-program](https://technet.microsoft.com/d1dc8a8b-f8de-487f-87b4-2174d449f0bc)
-   [Alternativ till att inaktivera RMS](https://technet.microsoft.com/4d32f35e-997d-4d10-ab66-efe217e853f7)
