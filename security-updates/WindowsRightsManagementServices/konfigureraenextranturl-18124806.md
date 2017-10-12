---
TOCTitle: 'Konfigurera en extranät-URL'
Title: 'Konfigurera en extranät-URL'
ms:assetid: '88fec9ff-c96c-4d20-8856-0485e7507572'
ms:contentKeyID: 18124806
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747661(v=WS.10)'
---

Konfigurera en extranät-URL
===========================

Om du vill hantera extranätanvändare i RMS-installationen kan du lägga till en licensieringsserver eller ett licensieringskluster som enbart hanterar extranätanvändning.

När du etablerar en extranät-licensieringsserver anger du en kluster-URL för den på samma sätt som du gör för alla RMS-servrar. Den URL som du anger är normalt en intern URL som extranätanvändare inte kommer åt. Denna URL används för identifiering av tjänster i RMS. Den måste vara en giltig URL i organisationen.

Om du lägger till en kluster-URL i ett extranät på en RMS-server som redan används måste de befintliga RMS-klienterna få nya klientlicensieringscertifikat för att få åtkomst till extranätets licensieringskluster.

Mer information finns i ”[Så här lägger du till en kluster-URL i ett extranät](https://technet.microsoft.com/12c83186-ce9e-4100-bbd1-d87a885331c7)” senare i det här avsnittet.
