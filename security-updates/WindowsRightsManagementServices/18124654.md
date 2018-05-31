---
TOCTitle: Identifiering av kontocertifieringstjänsten
Title: Identifiering av kontocertifieringstjänsten
ms:assetid: '293a2f91-4712-45ec-8b74-7533f4144cbd'
ms:contentKeyID: 18124654
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720224(v=WS.10)'
---

Identifiering av kontocertifieringstjänsten
===========================================

Med kontocertifieringstjänsten beviljas rättighetskontocertifikat åt användare. Rättighetskontocertifikaten gäller endast för specifika datorer eller enheter och det krävs att den användare som skickar begäran om certifikatet har ett giltigt datorcertifikat.

Kontocertifieringstjänsten körs endast på rotcertifikatservern eller –klustret. När en klient ska begära kontocertifiering hämtas först URL:en från Active Directory för den virtuella katalogen Certification på den rotcertifikatserver där kontocertifieringstjänsten hör hemma. Därefter läggs sökvägen till i kontocertifieringstjänsten.

Till exempel sparas URL-adressen till katalogen Certification på rotcertifikatservern på följande sätt i Active Directory:

http://*servernamn*/\_wmcs/Certification

När en klient begär ett rättighetskontocertifikat lägger den till namnet på programfilen för kontocertifieringstjänsten till URL:en på följande sätt:

http://*servernamn*/\_wmcs/Certification/Certification.asmx

| ![](images/Cc720224.note(WS.10).gif)Obs!                                     |
|-----------------------------------------------------------------------------------------------------------|
| Om du har aktiverat SSL på en RMS-server kommer dessa URL:er att använda anslutningsprotokollet https://. |
