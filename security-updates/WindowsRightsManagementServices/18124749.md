---
TOCTitle: Identifiering av publiceringstjänsten
Title: Identifiering av publiceringstjänsten
ms:assetid: '5d500841-a202-4865-b5d2-d0775d4e1bbc'
ms:contentKeyID: 18124749
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747580(v=WS.10)'
---

Identifiering av publiceringstjänsten
=====================================

Med publiceringstjänsten i RMS utfärdas publiceringslicenser som är till för att skydda innehåll. Den utfärdar också klientlicensieringscertifikat som tillåter användare att publicera innehåll utan att vara anslutna till företagets nätverk.

Publiceringstjänsten är tillgänglig på rotcertifieringsklustret eller på licensieringsservrar. RMS-aktiverade program begär den här tjänsten när en användare publicerar RMS-skyddat innehåll. När programmet ska göra en begäran om publicering hämtar den först URL:en till den virtuella katalogen Licensing på servern, där publiceringstjänsten hör hemma, från Active Directory. Därefter läggs sökvägen till i publiceringstjänsten.

URL:en för den virtuella katalogen Licensing för t.ex. en server sparas i Active Directory på följande sätt:

http://*servernamn*/\_wmcs/Licensing

När en server begär en publiceringslicens lägger den till namnet på programfilen för publiceringstjänsten till URL:en på följande sätt:

http://*servernamn*/\_wmcs/Licensing/Publish.asmx

Om RMS upptäcker att rättighetskontocertifikatet baseras på autentisering av Windows-användare identifieras publiceringstjänsten av Active Directory-skogen. Detta gäller både interna användare och externa användare som ansluter till företagets nätverk via ett virtuellt privat nätverk (VPN).

Om RMS upptäcker att rättighetskontocertifikatet baseras på Microsoft® .NET Passport finns publiceringstjänsten på det .NET Passport-konto som anges i det RMS-skyddade innehållet.

| ![](images/Cc747580.note(WS.10).gif)Obs!                                     |
|-----------------------------------------------------------------------------------------------------------|
| Om du har aktiverat SSL på en RMS-server kommer dessa URL:er att använda anslutningsprotokollet https://. |
