---
TOCTitle: 'RMS-kryptering och nycklar'
Title: 'RMS-kryptering och nycklar'
ms:assetid: '6ed69817-dab0-4845-b2a4-74203f95f7cf'
ms:contentKeyID: 18124775
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747615(v=WS.10)'
---

RMS-kryptering och nycklar
==========================

Skyddat innehåll är alltid krypterat. De certifikat och licenser som används i RMS kan också ha krypterat innehåll som endast kan dekrypteras med en viss enhet. I RMS-aktiverade program används en innehållsnyckel till att kryptera information. Alla servrar, klientdatorer och användarkonton i RMS SP1 har ett nyckelpar som består av två 1024-bitars RSA-nycklar. Nycklarna används till att kryptera den innehållsnyckel som finns i publicerings- och användarlicenser samt till att signera RMS-certifikat och licenser. Det säkerställer att servern bara beviljar åtkomst till behöriga användare och datorer.

Avsnittet behandlar:

-   [RMS-nyckeldefinitioner](https://technet.microsoft.com/b052305c-1db7-434a-bad9-26d704156776)
-   [RMS-servernycklar](https://technet.microsoft.com/5f4100a1-9aa5-42af-85c8-4bc691022f06)
-   [RMS-datornycklar](https://technet.microsoft.com/56e59ec2-f681-4ca2-98c7-72218ab9e9d9)
-   [Klientlicensieringsnycklar](https://technet.microsoft.com/28781125-2692-4ff9-99b1-e09227d72966)
-   [Användarnycklar](https://technet.microsoft.com/12dad6e2-64e7-4bab-bde7-b72f90f5cb05)
-   [RMS-innehållsnycklar](https://technet.microsoft.com/63c814bf-2809-477e-a2db-d90370442075)
