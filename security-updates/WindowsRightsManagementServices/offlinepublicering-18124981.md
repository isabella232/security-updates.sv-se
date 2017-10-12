---
TOCTitle: Offlinepublicering
Title: Offlinepublicering
ms:assetid: 'f6384ed2-f917-442e-aa63-c1394a1c4d06'
ms:contentKeyID: 18124981
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747741(v=WS.10)'
---

Offlinepublicering
==================

Offlinepublicering skiljer sig från onlinepublicering med tanke på det tillvägagångssätt som publiceringslicensen hämtas av det RMS-aktiverade programmet.

För att kunna publicera innehåll offline måste en användare först skaffa ett klientlicensieringscertifikat medan denne har tillgång till rotcertifikatservern via nätverket.

Processen vid offlinepublicering sker i följande steg:

1.  Användaren skapar dokumentet i ett RMS-aktiverat program och anger sedan vilka rättigheter och villkor som gäller för innehållet.
2.  När användaren sparar filen ger klientlicensieringscertifikatet den lokala datorn eller enheten tillstånd att utfärda och signera en publiceringslicens för filen.
    Publiceringslicensen innehåller två kopior av innehållsnyckeln: En som är krypterad med klientlicensieringscertifikatets offentliga nyckel och en som är krypterad med den offentliga nyckeln för den server som utfärdat klientlicensieringscertifikatet. Licensen innehåller också serverns URL. De båda offentliga nycklarna och URL:en kommer från klientlicensieringscertifikatet.
3.  Klientlicensieringscertifikatet används på datorn till att skapa en ägarlicens, som är en särskild typ av användarlicens som ger författare rättigheten att använda det RMS-skyddade innehållet när de är offline. I klientlicensieringscertifikatet används den privata nyckeln till att dekryptera den symmetriska innehållsnyckeln från publiceringslicensen. Sedan krypteras den på nytt till ägarlicensen.
4.  Programmet krypterar filen med innehållsnyckeln och binder publiceringslicensen till filen. Det är bara från den RMS-server som utfärdade publiceringslicensen, eller en server som tillhör en betrodd publiceringsdomän, som licenser att dekryptera den här filen kan utfärdas.
