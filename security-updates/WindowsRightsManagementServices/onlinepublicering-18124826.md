---
TOCTitle: Onlinepublicering
Title: Onlinepublicering
ms:assetid: '962c4e83-cf34-4c61-9589-31d24b0299fb'
ms:contentKeyID: 18124826
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747694(v=WS.10)'
---

Onlinepublicering
=================

I följande figur beskrivs processen vid onlinepublicering.

![](images/Cc747694.897e47b6-fffe-4b11-bc9f-be58539b9f19(WS.10).gif)

Processen vid onlinepublicering sker i följande steg:

1.  Användaren skapar ett dokument och använder det RMS-aktiverade programmet till att ange användare och tillämpa rättigheter och villkor på innehållet.
2.  Det RMS-aktiverade programmet genererar en symmetrisk innehållsnyckel och skickar en begäran om en publiceringslicens till certifikatservern eller till en licensieringsserver. I begäran ingår innehållsnyckeln och information om hur innehållet får användas.
3.  På licensieringsservern genereras en publiceringslicens, innehållsnyckeln krypteras med serverns offentliga nyckel och publiceringslicensen lämnas sedan ut till det RMS-aktiverade programmet.
4.  Programmet krypterar filen med innehållsnyckeln och binder publiceringslicensen till filen.
5.  Det RMS-aktiverade programmet på användarens dator skickar en begäran – som innehåller användarens rättighetskontocertifikat till RMS-servern (som utfärdat publiceringslicensen) – om en användarlicens för dokumentet.
6.  Användarens identitet valideras på RMS-servern. Om användaren godkänns genereras en användarlicens som lämnas ut till det RMS-aktiverade programmet på användarens dator.
7.  Dokumentet öppnas i det RMS-aktiverade programmet och användaren beviljas de användarrättigheter som anges i användarlicensen.
