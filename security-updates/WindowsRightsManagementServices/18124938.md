---
TOCTitle: 'RMS-loggningslyssnartjänsten'
Title: 'RMS-loggningslyssnartjänsten'
ms:assetid: 'e81ea57d-1a7d-4c02-abfc-dbc1597e176b'
ms:contentKeyID: 18124938
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747709(v=WS.10)'
---

RMS-loggningslyssnartjänsten
============================

Loggningslyssnartjänsten installeras med RMS-installationsprogrammet. Den körs både på rotcertifieringsservrar och licensieringsservrar. På varje RMS-webbtjänst loggas alla begäran och svar som tas emot och skickas. Den loggade informationen skickas sedan till kön för loggningsmeddelanden med hjälp av Message Queuing. Loggningslyssnartjänsten överför sedan denna information från kön till loggningsdatabasen för klustret.

Du kan aktivera och inaktivera loggning på webbplatsen Administration. När du inaktiverar loggning upphör loggningen av webbtjänsternas begäran och svar och loggningslyssnartjänsten inaktiveras.
