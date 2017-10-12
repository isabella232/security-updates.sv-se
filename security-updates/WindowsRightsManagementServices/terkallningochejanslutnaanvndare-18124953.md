---
TOCTitle: Återkallning och ej anslutna användare
Title: Återkallning och ej anslutna användare
ms:assetid: 'a9cf0541-9101-4e90-9c56-7c1b9a8deca6'
ms:contentKeyID: 18124953
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747631(v=WS.10)'
---

Återkallning och ej anslutna användare
======================================

Användare som publicerar skyddat innehåll och senare vill arbeta med det igen måste ha en användarlicens för att göra detta. Vid onlinepublicering erhålls användarlicensen via samma funktion som används för alla mottagare av skyddat innehåll, men som standard ges författaren fullständiga rättigheter att bestämma över hur innehållet får användas. Om publiceringslicensen innehåller ett villkor som kräver en lista över återkallade certifikat hämtas listan från nätverket med det RMS-aktiverade programmet.

En användare som inte är ansluten till företagets nätverk kommer dock att få svårt att erhålla en återkallelselista. För att tillgodose ett sådant behov utfärdar det klientlicensieringscertifikat som används för offlinepublicering en särskild typ av licens, som kallas ägarlicens, utöver publiceringslicensen. En ägarlicens ger användaren möjlighet att arbeta med innehållet sedan det har skyddats. Även om den principmall för rättigheter som har tillämpats på innehållet kräver en lista över återkallade certifikat innehåller ägarlicenser aldrig krav på listor över återkallade certifikat. På så sätt kan användare som inte är anslutna fortsätta att arbeta med sitt innehåll efter att ha publicerat det, utan att behöva hämta någon lista över återkallade certifikat.
