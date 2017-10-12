---
TOCTitle: Identifiering av aktiveringstjänsten
Title: Identifiering av aktiveringstjänsten
ms:assetid: 'e178d81b-b35c-4958-87ef-e077e2204b32'
ms:contentKeyID: 18124949
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747697(v=WS.10)'
---

Identifiering av aktiveringstjänsten
====================================

Med aktiveringstjänsten utfärdas lockboxar och RMS-datorcertifikat för RMS-klienter av version 1.0. Tjänsten är bakåtkompatibel med RMS version 1.0. Aktiveringsproxytjänsten finns i rotcertifikatklustret för RMS, och därifrån vidarebefordras begäran om RMS-datoraktivering till aktiveringstjänsten från klientdatorer i företagets nätverk.

Vid en begäran om RMS-datoraktivering hämtas först URL:en med RMS version 1.0-klienten från Active Directory till den virtuella katalogen Certification på rotcertifikatservern, där aktiveringsproxytjänsten finns. Därefter läggs sökvägen till aktiveringsproxytjänsten till.

URL:en för den virtuella katalogen Certification på rotcertifikatservern sparas i Active Directory på följande sätt:

http://*servernamn*/\_wmcs/Certification

När en begäran om RMS-datoraktivering skickas från en klient läggs namnet på programfilen för aktiveringsproxytjänsten till i URL:en på följande sätt:

http://*servernamn*/\_wmcs/Certification/Activation.asmx

För klienter som inte är anslutna till företagets nätverk används UDDI till att identifiera aktiveringstjänsten. Mer information finns i ”[Publicering av tjänster som tillhandahålls av Microsoft](https://technet.microsoft.com/7ee8cb4d-1b46-48be-8a4c-5ff6a458231a)” tidigare i det här avsnittet.

| ![](images/Cc747697.note(WS.10).gif)Obs!                                     |
|-----------------------------------------------------------------------------------------------------------|
| Om du har aktiverat SSL på en RMS-server kommer dessa URL:er att använda anslutningsprotokollet https://. |
