---
TOCTitle: Definiera principer för förtroenden
Title: Definiera principer för förtroenden
ms:assetid: 'e8d78300-4b26-4f15-9e4f-5ae9eb827ef9'
ms:contentKeyID: 18124966
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747711(v=WS.10)'
---

Definiera principer för förtroenden
===================================

Gör så här om du vill definiera betrodda användar- och publiceringsdomäner:

-   **Betrodda användardomäner**. När du lägger till en användardomän kan RMS bearbeta begäran för användarlicenser från användare vars rättighetskontocertifikat har utfärdats med en RMS-installation i en annan Active Directory-skog, d.v.s. i ett annat rotcertifikatkluster. Du lägger till en betrodd användardomän genom att importera serverlicensieringscertifikatet för den installation som du vill skapa förtroende för.
-   **Betrodda publiceringsdomäner**. Genom att lägga till en publiceringsdomän kan en RMS-server utfärda användarlicenser mot publiceringslicenser som har utfärdats av en annan RMS-server. Du lägger till en betrodd publiceringsdomän genom att importera serverlicensieringscertifikatet och den privata nyckeln för den server som du vill skapa förtroende för.

Mer information finns i ”[Lägga till och ta bort betrodda användardomäner](https://technet.microsoft.com/7c440b15-01c4-49f1-b43c-00f67f3388c1)” och ”[Lägga till och ta bort betrodda publiceringsdomäner](https://technet.microsoft.com/d87b502d-5497-4ccd-badf-f6807d587cee)” senare i det här avsnittet. Stegvisa instruktioner finns i ”[Upprätta principer för förtroenden](https://technet.microsoft.com/6c2be3c2-1837-4de4-a72e-3ba3eec3321d)” senare i det här avsnittet.
