---
TOCTitle: Planera systemåterställning
Title: Planera systemåterställning
ms:assetid: 'a7779ffd-7a94-4e13-b846-0ffd00608e02'
ms:contentKeyID: 18124859
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747718(v=WS.10)'
---

Planera systemåterställning
===========================

Systemfel kan uppstå av många olika oförutsedda anledningar: maskinvarufel, belastning, strömtoppar, programvarufel och annat. I en väl genomförd distribution ingår också en plan för hur systemet snabbt ska återställas om något inträffar. I ett RMS-system är regelbunden säkerhetskopiering av den privata servernyckeln och RMS-databaserna, och då särskilt konfigurationsdatabasen, ett grundläggande krav på skydd för RMS-funktionerna. Det bevarar principmallarna för rättigheter, nycklar och andra data som krävs för åtkomst till befintliga licenser och redan publicerat innehåll. Om den befintliga RMS-installationen inte fungerar kan du installera RMS på andra servrar och sedan etablera RMS genom att ange att det är den säkerhetskopierade konfigurationsdatabasen som ska användas. Den nya installationen är då identisk med den befintliga installationen vid den tidpunkt då den säkerhetskopierades.

Avsnittet behandlar:

-   [Förbereda systemåterställning](https://technet.microsoft.com/885c047f-1e3b-4bf5-8248-3a4505759cbb)
-   [Säkerhetskopiera RMS](https://technet.microsoft.com/c29894da-ee00-428c-8d48-80d8e5a83678)
-   [Säkerhetskopiera och återställa RMS-systemet](https://technet.microsoft.com/c11f3ac1-e512-402b-bf13-9ff21f5fe745)
-   [Säkerhetskopiera och återställa principmallar för rättigheter](https://technet.microsoft.com/a6ed3328-4128-45e8-9236-3de484b460de)
