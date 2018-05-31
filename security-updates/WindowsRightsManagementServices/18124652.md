---
TOCTitle: Klientlicensieringsnycklar
Title: Klientlicensieringsnycklar
ms:assetid: '28781125-2692-4ff9-99b1-e09227d72966'
ms:contentKeyID: 18124652
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720221(v=WS.10)'
---

Klientlicensieringsnycklar
==========================

Med klientlicensieringscertifikat kan användare publicera RMS-skyddat innehåll när de inte är anslutna till det RMS-aktiverade nätverket. Ett klientlicensieringscertifikat har ett nyckelpar som består av två 1024-bitars RSA-nycklar.

I RMS-klienten används klientlicensieringscertifikatets offentliga nyckel vid utfärdandet av en publiceringslicens för följande uppgifter:

-   För kryptering av den symmetriska innehållsnyckeln.
-   För signering av publiceringslicenser som har utfärdats lokalt när användaren inte är ansluten till nätverket.
