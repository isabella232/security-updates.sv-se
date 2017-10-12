---
TOCTitle: 'RMS-klientregistrering'
Title: 'RMS-klientregistrering'
ms:assetid: '9c1d07bf-7235-4694-8291-ac2e5b221f4a'
ms:contentKeyID: 18124834
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747613(v=WS.10)'
---

RMS-klientregistrering
======================

Klientdatorer kan registreras via publiceringstjänsten och erhålla ett RMS-klientlicensieringscertifikat som ger användare möjlighet att publicera RMS-skyddat innehåll när deras dator inte är ansluten till företagets nätverk. När så är fallet är det klientdatorn och inte publiceringstjänsten som signerar och utfärdar de publiceringslicenser som innehåller information om användarrättigheter för RMS-skyddat innehåll som publiceras från den datorn.

RMS-publiceringstjänsten utfärdar klientlicensieringscertifikat.

Klientregistreringen sker i följande tre steg:

1.  Klientdatorn skickar användarens rättighetskontocertifikat i en begäran om registrering till publiceringstjänsten på rotcertifikatservern eller klustret eller på en licensieringsserver eller ett licensieringskluster.
2.  På servern valideras att klientregistrering är tillåtet baserat på nätverksadministratörens inställningar och att rättighetskontocertifikatet inte finns med i någon exkluderingslista i konfigurationsdatabasen. Mer information om hur du skapar exkluderingslistor finns i ”Hantera exkluderingsprinciper” i ”Använda en RMS-server”.
3.  Publiceringstjänsten skapar ett nyckelpar för klientdatorn. Den skapar ett klientlicensieringscertifikat och infogar den offentliga nyckeln i certifikatet. Den privata nyckeln krypteras med rättighetskontocertifikatets offentliga nyckel och infogas sedan i certifikatet.
4.  Publiceringslicensen utfärdar ett klientlicensieringscertifikat till klientdatorn.
