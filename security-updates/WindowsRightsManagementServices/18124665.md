---
TOCTitle: Användarnycklar
Title: Användarnycklar
ms:assetid: '12dad6e2-64e7-4bab-bde7-b72f90f5cb05'
ms:contentKeyID: 18124665
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720202(v=WS.10)'
---

Användarnycklar
===============

Varje RMS-användare har ett nyckelpar som består av två 1024-bitars RSA-nycklar. Användarens nyckelpar sparas i konfigurationsdatabasen för RMS så att varje användare alltid har samma nyckelpar i hela RMS-systemet.

Ett rättighetskontocertifikat innehåller användarens offentliga nyckel. Nyckeln används till att kryptera innehållsnyckeln i en användarlicens så att bara en viss användare kan använda det RMS-skyddade innehållet med hjälp av den här licensen.

Rättighetskontocertifikatet innehåller också användarens privata nyckel som krypteras med en klientdators offentliga nyckel. På så sätt säkerställs att ett rättighetskontocertifikat endast kan användas på den dator som certifikatet har utfärdats för och att varje rättighetskontocertifikat för en viss användare alltid kommer att innehålla samma nyckelpar. Användarens privata nyckel krävs för att användaren ska kunna använda innehåll som har skyddats med hjälp av RMS.
