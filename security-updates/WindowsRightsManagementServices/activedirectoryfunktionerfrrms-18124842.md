---
TOCTitle: 'Active Directory-funktioner för RMS'
Title: 'Active Directory-funktioner för RMS'
ms:assetid: '9589127d-19b3-44f1-b7a1-01992e78218a'
ms:contentKeyID: 18124842
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747604(v=WS.10)'
---

Active Directory-funktioner för RMS
===================================

I RMS används Active Directory i följande syften:

-   **Tillhandahålla användarautentisering.**Active Directory tillhandahåller de katalogtjänster som används till att autentisera användare i RMS. Mer information om autentisering och RMS finns i avsnittet ”[RMS säkerhetsmodell](https://technet.microsoft.com/665db831-366d-4dca-9bb3-cc2912481fe1)” senare i det här avsnittet.
-   **Avgöra gruppmedlemskap och individuella användarkontoidentiteter.**Active Directory tillhandahåller information om gruppmedlemskap som används i RMS till att bevilja användarlicenser för RMS-skyddat innehåll när publiceringslicensen beviljar rättigheter till grupper i stället för individuella användarkonton. För att minska antalet LDAP-frågor som skickas till Active Directory sparas informationen både i ett lokalt cacheminne i RMS och i en central katalogtjänstdatabas. Mer information finns i ”[Cacheminnet för Active Directory i RMS](https://technet.microsoft.com/c721a2eb-2fe9-4346-b426-3cc169b97265)” och ”[Katalogtjänstdatabasen i RMS](https://technet.microsoft.com/6f6b8586-5d17-4a40-94a3-4dc738195301)” tidigare i det här avsnittet.
-   **Spara URL:er för tjänstidentifiering.**En begäran om en tjänst (t.ex. om en användarlicens, en publiceringslicens eller underregistrering av en licensieringsserver) måste skickas till URL:en för den körbara modulen för den webbtjänst där begäran beviljas. Alla begäran om tjänster inleds med en Active Directory-fråga om URL:en till webbtjänsten Server (Server.asmx), som i sin tur tillhandahåller URL:en för begäran om tjänsten. Mer information finns i ”[Publicering och identifiering av tjänster i RMS](https://technet.microsoft.com/336c0d55-fd7f-4aa9-b3e6-bfd6565b1086)” senare i det här avsnittet.
