---
TOCTitle: Klientlicensieringscertifikat
Title: Klientlicensieringscertifikat
ms:assetid: 'bfb36387-3e15-4cde-8b8f-482219569a64'
ms:contentKeyID: 18124889
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747744(v=WS.10)'
---

Klientlicensieringscertifikat
=============================

Ett klientlicensieringscertifikat ger en användare rättighet att publicera RMS-skyddat innehåll utan att denne är ansluten till företagets nätverk.

För att kunna erhålla ett klientlicensieringscertifikat skickar användaren en begäran om klientregistrering från en klientdator till rotcertifikatservern eller en licensieringsserver. Servern lämnar sedan ut ett klientlicensieringscertifikat för denna dator.

Ett klientlicensieringscertifikat innehåller den offentliga och den privata nyckeln för klientlicensiering som krypteras med den offentliga nyckeln för den användare som begärt certifikatet. Certifikatet innehåller också den offentliga nyckeln för den server som utfärdat certifikatet, som signeras av den privata nyckeln för denna server. Den privata nyckeln för klientlicensiering används för att signera publiceringslicenser som användaren skapar.
