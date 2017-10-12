---
TOCTitle: 'RMS-innehållsnycklar'
Title: 'RMS-innehållsnycklar'
ms:assetid: '63c814bf-2809-477e-a2db-d90370442075'
ms:contentKeyID: 18124748
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720284(v=WS.10)'
---

RMS-innehållsnycklar
====================

När en användare publicerar RMS-skyddat innehåll skapas en symmetrisk innehållsnyckel i det RMS-aktiverade programmet som används till att kryptera innehållet. I RMS används AES (Advanced Encryption Standard) till att skapa innehållsnyckeln.

Innehållsnyckeln bifogas i publiceringslicensen och innehållsnyckeln krypteras med den offentliga nyckeln för den RMS-server som utfärdat licensen.

När denna server tar emot en begäran om en användarlicens dekrypterar den innehållsnyckeln med serverns privata nyckel och krypterar sedan innehållsnyckeln på nytt med användarens offentliga nyckel (som bifogats som en del av begäran). Innehållsnyckeln finns sedan i användarlicensen.
