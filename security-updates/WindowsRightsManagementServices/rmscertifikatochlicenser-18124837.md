---
TOCTitle: 'RMS-certifikat och licenser'
Title: 'RMS-certifikat och licenser'
ms:assetid: '91916ecb-9e5d-49e8-ab65-ef2c56339b83'
ms:contentKeyID: 18124837
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747600(v=WS.10)'
---

RMS-certifikat och licenser
===========================

För de olika komponenter som ingår en RMS-installation används betrodda anslutningar som implementeras med en uppsättning certifikat. Att kontrollera giltigheten för dessa certifikat är en central funktion i RMS-tekniken. Allt RMS-skyddat innehåll publiceras med en licens som anger vilka regler som gäller för användning av innehållet och varje användare av innehållet får en unik licens som kan läsa, tolka och följa dessa användningsregler. I denna betydelse är en licens en särskild typ av certifikat.

I RMS används ett XML-språk till att uttrycka användningsrättigheter för RMS-skyddat innehåll: eXtensible rights Markup Language (XrML), version 1.2.1. Mer information finns i avsnittet ”XrML”.

De certifikat och licenser som förekommer i RMS är sammanlänkade i en hierarki så att det alltid går att följa en kedja från ett visst certifikat eller en viss licens, via betrodda certifikat, upp till ett betrott nyckelpar. Mer information finns i ”[Förtroendehierarkin i RMS](https://technet.microsoft.com/2d44182f-a653-4383-aba1-dade53f7cf9a)” senare i det här avsnittet.

Avsnittet behandlar:

-   [Översikt av RMS-certifikat och -licenser](https://technet.microsoft.com/637ccfca-318e-4346-85b5-0945b058fb9c)
-   [Serverlicensieringscertifikat](https://technet.microsoft.com/0b35fbcd-25a9-4587-898d-9a30fd1d3c5b)
-   [Klientlicensieringscertifikat](https://technet.microsoft.com/bfb36387-3e15-4cde-8b8f-482219569a64)
-   [RMS-datorcertifikat](https://technet.microsoft.com/1841d53e-d01b-47c3-9d43-3805ceefed5a)
-   [Rättighetskontocertifikat](https://technet.microsoft.com/2ff315cc-211d-4e6e-85e8-56867c2abd94)
-   [Publiceringslicenser](https://technet.microsoft.com/187228fc-370b-4e23-a53a-21bb296b84a1)
-   [Användarlicenser](https://technet.microsoft.com/6e609db3-49b3-4cac-a34c-8a96da627067)
