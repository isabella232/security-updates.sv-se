---
TOCTitle: RMS säkerhetsmodell
Title: RMS säkerhetsmodell
ms:assetid: '665db831-366d-4dca-9bb3-cc2912481fe1'
ms:contentKeyID: 18124761
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747598(v=WS.10)'
---

RMS säkerhetsmodell
===================

När RMS-systemet används utnyttjas ett flertal resurser, bl.a. databasservern, Active Directory, meddelandekön och den lokala hårddisken. Dessutom skapar installationsprogrammet för RMS särskilda resurser som krävs för driften, t.ex. SOAP-poster, webbsidor, köer för loggningsmeddelanden med flera. Installationsprogrammet för RMS konfigurerar DACL-listor på de resurser det skapar och gör tillgängliga samt konfigurerar IIS-autentisering för varje resurs.

I det här avsnittet beskrivs hur säkerheten för de resurser som används i ett RMS-system konfigureras och hur systemet får tillgång till resurser under de olika faser då det tas i bruk: Installationsfas, etableringsfas och normal drift.

Avsnittet behandlar:

-   [Säkerhetsgrupper i RMS](https://technet.microsoft.com/25749a83-8c12-48ec-96ad-296d31fd55d4)
-   [Säkerhetslägen i RMS](https://technet.microsoft.com/d7792293-5bb2-4232-9d48-e81e87ab6219)
-   [Säkerhet vid RMS-installation](https://technet.microsoft.com/0a3d40b2-f27e-4e63-baff-a9c8433f5f91)
-   [Säkerhet vid etablering](https://technet.microsoft.com/9f1282c5-5642-4870-a9a4-c3a485f8ff76)
-   [Säkerhet vid normal drift](https://technet.microsoft.com/98f3d584-6320-4aa1-9959-7133cfdb6df7)
