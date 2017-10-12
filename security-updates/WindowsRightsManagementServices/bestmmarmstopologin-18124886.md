---
TOCTitle: 'Bestämma RMS-topologin'
Title: 'Bestämma RMS-topologin'
ms:assetid: 'bf516f7d-b3a1-4e7f-971f-bfab1db41812'
ms:contentKeyID: 18124886
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747651(v=WS.10)'
---

Bestämma RMS-topologin
======================

I den grundläggande RMS-topologin tillhandahålls alla RMS-tjänster för en organisation av RMS-rotcertifikatservern eller RMS-rotcertifikatklustret i varje Active Directory-skog. Den här RMS-topologin fungerar väl både i stora och små organisationer. I en distribuerad RMS-topologi kan en eller flera licensieringsservrar (kallas ibland avdelningslicensieringsservrar) tillhandahålla vissa eller alla licensieringstjänster för specifika användare och grupper i organisationen. Rotcertifikatservern (eller rotcertifikatklustret) fortsätter att tillhandahålla kontocertifierings- och aktiveringsproxytjänster för hela organisationen, men den distribuerade RMS-topologin är designad för organisationer med specifika licensieringsbehov som vill kontrollera RMS inom olika segment av organisationen.

Även om det bara finns två grundläggande topologier för RMS kan komponenterna i topologierna variera. Om du vill definiera de komponenter som är lämpliga för er organisation och skapa en lämplig topologi för distributionen av RMS måste du:

-   Utvärdera organisationens krav och målsättningar.
-   Definiera hur hanteringen av rättigheter ska användas.
-   Analysera beräknade trafikmönster och beräknad belastning så att en lämplig tjänstnivå kan implementeras.

Att definiera topologin och fatta de nödvändiga beslut som krävs för implementeringen av utformningen är en omfattande process som sträcker sig genom hela planeringsarbetet för RMS-distributionen.

Avsnittet behandlar:

-   [Identifiera kärnkomponenter](https://technet.microsoft.com/c9ec225b-0e51-42f5-aff6-0aecb62e3b27)
-   [Sätta upp mål för topologin](https://technet.microsoft.com/8275a04d-3e5b-40b0-be9d-2f31b7aeca6b)
-   [Definiera omfattningen av RMS-implementeringen](https://technet.microsoft.com/4b5fe1be-643e-47c4-bf9b-50d1e97108fb)
-   [Utvärdera utrymmeskrav](https://technet.microsoft.com/89f0138c-946d-47d7-a286-041d4d9606a8)
-   [Tillhandahålla redundans och belastningsutjämning](https://technet.microsoft.com/162d547c-78a7-4848-b43e-58e481832af2)
-   [Utvärdera överflyttningskrav](https://technet.microsoft.com/cec07f45-dc52-4004-860b-5cc33e5fc209)
-   [Planera databasserver-infrastrukturen](https://technet.microsoft.com/b12354bd-3143-4d1f-b5aa-450c4550653c)
-   [Planera distribution mellan skogar](https://technet.microsoft.com/2dfb40b7-95b1-4362-b32e-72867544b705)
-   [Planera för externa RMS-användare](https://technet.microsoft.com/107e1338-4dcf-4ed5-a49d-e875cc883db1)
-   [Planera en grundläggande RMS-topologi](https://technet.microsoft.com/fec3201e-201f-4faf-910e-fa44132af83d)
-   [Planera en distribuerad RMS-topologi](https://technet.microsoft.com/8773a1e0-6ac3-41f5-9866-5890cef08d04)
