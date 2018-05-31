---
TOCTitle: Hantera exkluderingsprinciper
Title: Hantera exkluderingsprinciper
ms:assetid: 'ee31e099-e095-4648-95da-0009fbeb48cb'
ms:contentKeyID: 18124959
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747730(v=WS.10)'
---

Hantera exkluderingsprinciper
=============================

Du kan implementera exkluderingsprinciper på serversidan som nekar certifikat- och licensbegäran baserade på rättighetskontocertifikatet eller lockbox-versionen. Med exkluderingsprinciper nekas nya certifikat- och licensbegäran som skickas från komprometterade enheter, men till skillnad från återkallningar blir inte enheterna ogiltiga av exkluderingsprinciper. Administratörer kan också exkludera potentiellt skadliga och komprometterade program så att RMS-skyddat innehåll inte kan dekrypteras med dem. Dessutom kan administratörer exkludera vissa versioner av Windows-operativsystem och förhindra att rättighetsskyddat innehåll används på de klientdatorer där dessa Windows-operativsystem körs.

När en enhet har exkluderats ingår enheten i exkluderingslistan i de användarlicenser som utfärdas av RMS-servern. Om du efter en tid bestämmer dig för att ta bort en enhet som tidigare har lagts till i en exkluderingsprincip tar du bort enheten på sidan Exkluderingsprinciper på administrationswebbplatsen. Då tas enheten bort från exkluderingslistan. Enheterna behandlas då inte som exkluderade i alla nya certifierings- och licensieringsbegäran.

Såvida du inte exkluderar en enhet av misstag bör du inte ta bort en enhet från en exkluderingsprincip förrän du är säker på att alla certifikat som utfärdades innan exkluderingsprincipen skapades har upphört att gälla. Annars kommer både gamla och nya certifikat att tillåta att innehållet dekrypteras, vilket kanske inte är vad som avsågs.

Följande avsnitt innehåller information om hur du hanterar exkluderingsprinciper. Stegvisa instruktioner om hur du exkluderar enheter finns i ”[Aktivera exkluderingsprinciper](https://technet.microsoft.com/bbb1ce50-bc11-41cf-b75b-a6756141908f)” senare i det här avsnittet.

Avsnittet behandlar:

-   [Exkludera lockbox-versioner](https://technet.microsoft.com/e287f026-aab2-43ab-93bc-48087da82f36)
-   [Exkludera rättighetskontocertifikat](https://technet.microsoft.com/cba5e901-942c-4d06-9865-e6c4648c95e6)
-   [Exkludera Windows-versioner](https://technet.microsoft.com/8b8a184d-ac0e-4a43-822c-d2fae2faf484)
-   [Exkludera program](https://technet.microsoft.com/b68ae4b2-b9ba-44ae-90cb-c88df600ec86)
