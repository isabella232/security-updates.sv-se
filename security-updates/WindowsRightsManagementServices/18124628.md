---
TOCTitle: 'RMS-datoraktivering'
Title: 'RMS-datoraktivering'
ms:assetid: '09a0d631-9860-477f-9d10-df61b3bfe125'
ms:contentKeyID: 18124628
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720182(v=WS.10)'
---

RMS-datoraktivering
===================

Datoraktivering är en nödvändig förutsättning för att en användare ska kunna publicera eller använda RMS-skyddat innehåll på en klientdator. Datoraktivering är beteckningen på den process där en klientdator erhåller en unik lockbox och ett motsvarande RMS-datorcertifikat. Lockboxen innehåller datorns privata nyckel och datorcertifikatet innehåller datorns offentliga nyckel. Eftersom lockboxen innehåller datorns privata nyckel utgör lockboxen den centrala säkerhetsenheten för kryptering och dekryptering. Varje användare på datorn har ett unikt maskincertifikat som skapas i datoraktiveringsprocessen.

Den datoraktiveringsprocess som används i RMS-klienten för Service Pack 1 ser annorlunda ut jämfört med datoraktiveringsprocessen i version 1. RMS-klienten för Service Pack 1 är ”självaktiverande”. När RMS-klienten installeras av en inloggad användare, eller när en inloggad användare använder en RMS-funktion för första gången, startas aktiveringsprocessen på klienten, där flera uppsättningar nycklar skapas med den API-kryptering som finns i Windows. De här nycklarna används till en serie krypteringar som genererar ett datorcertifikat som kopplar ihop användaren, datorn och RMS-klienten i RMS-förtroendehierarkin.
