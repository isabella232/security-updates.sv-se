---
TOCTitle: Identifiering av licensieringstjänsten
Title: Identifiering av licensieringstjänsten
ms:assetid: '4eabbb76-b359-443a-b737-098c5659e9c6'
ms:contentKeyID: 18124715
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720269(v=WS.10)'
---

Identifiering av licensieringstjänsten
======================================

Med licensieringstjänsten i RMS utfärdas användarlicenser som ger autentiserade användare rättighet att använda skyddat innehåll.

Denna tjänst körs på rotcertifikatservern eller –klustret och på licensieringsservrar. När en klient ska begära en licens hämtar den först URL:en för den virtuella katalogen Licensing från Active Directory på rotcertifieringsklustret, där licensieringstjänsten hör hemma. Därefter lägger den till sökvägen till licensieringstjänsten.

URL:en för den virtuella katalogen Licensing på rotcertifieringsklustret sparas i Active Directory på följande sätt:

http://*servernamn*/\_wmcs/Licensing

När en server begär en användarlicens lägger den till namnet på programfilen för licensieringstjänsten till URL:en på följande sätt:

http://*servernamn*/\_wmcs/Licensing/License.asmx

Tjänsten finns antingen på RMS-servern eller det .NET Passport-konto som utfärdat publiceringslicensen. URL:en finns med i publiceringslicensen.

| ![](images/Cc720269.note(WS.10).gif)Obs!                                     |
|-----------------------------------------------------------------------------------------------------------|
| Om du har aktiverat SSL på en RMS-server kommer dessa URL:er att använda anslutningsprotokollet https://. |
