---
TOCTitle: 'RMS-loggningsdatabasen'
Title: 'RMS-loggningsdatabasen'
ms:assetid: '8ba147f3-16e4-4d9a-ac8f-f05ba2ba11bb'
ms:contentKeyID: 18124813
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747669(v=WS.10)'
---

RMS-loggningsdatabasen
======================

För varje rotcertifierings- eller licensieringskluster installerar RMS-installationsprogrammet en loggningsdatabas i samma databasserverinstans där konfigurationsdatabasen finns. Installationsprogrammet skapar också en privat meddelandekö för loggning i Message Queuing. Tjänsten för loggningslyssnare överför information från denna meddelandekö till loggningsdatabasen.

RMS-tjänstgruppen har körrättigheter för loggningsdatabasens sparade procedurer.

Loggningslyssnartjänsten skickar stora mängder information till loggningsdatabasen, vilket kan göra det lämpligt för administratörer att skapa filter så att bara information som anses nödvändig inom företaget sparas i loggningsdatabasen.
