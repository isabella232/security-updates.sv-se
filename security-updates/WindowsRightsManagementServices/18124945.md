---
TOCTitle: Säkerhetsplanering för RMS
Title: Säkerhetsplanering för RMS
ms:assetid: 'eb0fa784-1246-44aa-be31-2c332db7d09c'
ms:contentKeyID: 18124945
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747719(v=WS.10)'
---

Säkerhetsplanering för RMS
==========================

Precis som med andra servrar i organisationen måste du väga in säkerheten vid distributionsplaneringen. RMS implementeras som en webbtjänst. Det betyder att du kontrollerar åtkomsten till RMS på samma sätt som med andra webbtjänster genom att använda åtkomstlistor (ACL) och SSL (Secure Sockets Layer).

RMS kan också implementeras som en del av en åtkomstkontrollerad domän om det finns behov i din RMS-distribution av ett extra kontrollager för känslig information.

I RMS används ett system med privata nycklar för att kryptera innehåll. Därför måste den privata RMS-nyckeln säkerhetskopieras och hanteras som en del i säkerhetsplanen.

Avsnittet behandlar följande ämnen:

-   [Bestämma åtkomstkrav](https://technet.microsoft.com/eb2ce9a5-0430-4811-bd40-4a94a84426a8)
-   [Definiera krav för nyckelhantering](https://technet.microsoft.com/f0e08fb8-bf5e-4278-a09f-daa57696e786)
