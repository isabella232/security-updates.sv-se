---
TOCTitle: 'Så här lägger du till en kluster-URL i ett extranät'
Title: 'Så här lägger du till en kluster-URL i ett extranät'
ms:assetid: '12c83186-ce9e-4100-bbd1-d87a885331c7'
ms:contentKeyID: 18124631
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720193(v=WS.10)'
---

Så här lägger du till en kluster-URL i ett extranät
===================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Det är viktigt att du registrerar URL:en i DNS (Domain Name System) och att du kontrollerar att den är tillgänglig från Internet. Du måste ange HTTPS för kluster-URL:en om du har aktiverat SSL för webbtjänstfiler.

Om du lägger till en kluster-URL i ett extranät på en RMS-server som redan används, måste de aktuella RMS-klienterna skaffa nya klientlicensieringscertifikat för att få åtkomst till extranätets kluster för licensiering.

Lägga till en kluster-URL i ett extranät
----------------------------------------

#### Så här lägger du till en kluster-URL i ett extranät

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill lägga till en kluster-URL i ett extranät.

2.  Klicka på **Inställningar för extranätets kluster-URL** vid **Administrationslänkar**.

3.  Ange från vilken URL externa användare kan hämta licenser vid **Extranätets kluster-URL**. Du kan också välja mellan HTTP och HTTPS.

4.  Klicka på **Skicka**.
