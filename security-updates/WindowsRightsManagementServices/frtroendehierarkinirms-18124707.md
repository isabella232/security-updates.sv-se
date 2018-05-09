---
TOCTitle: Förtroendehierarkin i RMS
Title: Förtroendehierarkin i RMS
ms:assetid: '2d44182f-a653-4383-aba1-dade53f7cf9a'
ms:contentKeyID: 18124707
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720232(v=WS.10)'
---

Förtroendehierarkin i RMS
=========================

I RMS-systemet ingår komponenterna Microsofts registreringstjänst, RMS-servrarna i organisationen, klientdatorer och användare. För varje komponent utfärdas ett certifikat som fastställer komponentens identitet i systemet. En förtroendehierarki definierar förtroendeförhållandet mellan dessa certifikat och därmed mellan de enheter som innehar dem. Den definierar också förtroendeförhållandet mellan betrodda enheter och de licenser som de utfärdar till andra betrodda enheter.

Förtroendehierarkin kopplar certifikat och licenser i en förtroendekedja som RMS alltid kan följa från ett visst certifikat eller en viss licens hela vägen upp till ett betrott nyckelpar. I förtroendekedjan ingår det aktuella certifikatet, certifikatet för den enhet som utfärdat det aktuella certifikatet, certifikatet för denna enhet och så vidare längs kedjan upp till förtroenderoten.

I RMS är förtroenderoten, eller ”förtroendeankaret”, ett Microsoft-nyckelpar. Denna gemensamma förtroenderot gör det möjligt för ett företag att bygga upp ett förtroendesystem som omfattar betrodda enheter, t.ex. användare och partners, både inom och utanför företaget.

I följande figur framgår förtroendehierarkin i ett företag. Förtroendekedjan går tillbaka till de Microsoft-tjänster som utfärdar bascertifikaten.

![](images/Cc720232.6c169175-94fb-4ec0-93bc-12748aae3ac4(WS.10).gif "Förtroendehierarkin")
1.  Till varje klientdator utfärdas en unik lockbox som innehåller den offentliga Microsoft-rotnyckeln.
2.  När en licensbegäran tas emot i RMS valideras enheterna genom att sökvägen i förtroendehierarkin följs tillbaka till förtroenderoten.
3.  RMS kontrollerar äktheten för den betrodda enheten som angetts i licensen.
4.  En kontroll görs av att den betrodda enhetens certifikat är utfärdat med en server som ingår i förtroendehierarkin.

På varje nivå i certifikatkedjan valideras licensen eller certifikatet och dess koppling till en känd förtroenderot via en förtroendekedja verifieras. Varje licens eller certifikat i kedjan kontrolleras av RMS och det valideras att följande villkor uppfylls:

-   Licensens eller certifikatets XrML är giltig.
-   Utfärdarens signatur är giltig.
-   Licensens semantik är lämplig för det avsedda användningsområdet.
-   Uppställda villkor (som t.ex. giltighetsdatum) uppfylls.
-   Licensen har inte blivit återkallad.
-   Licensens signaturnyckel och den certifierade utfärdarens nyckel överensstämmer.
