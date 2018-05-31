---
TOCTitle: Återkalla RMS
Title: Återkalla RMS
ms:assetid: '72689f90-f3c5-4b61-94ea-d825f3199b3b'
ms:contentKeyID: 18124778
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747622(v=WS.10)'
---

Återkalla RMS
=============

Återkallning är en funktion som gör det möjligt att återkalla en handling, t.ex. ett certifikat eller en licens, som tidigare utfärdats. Huvudsyftet med återkallning är att enheter som inte längre är betrodda ska kunna förhindras att delta i ett RMS-system. Återkallning kan t.ex. vara aktuellt av följande anledningar:

-   När du vill hindra en enhet eller identitet i förtroendekedjan som har förlorat sitt existensberättigande från att använda innehåll, t.ex. när en anställd lämnar företaget och inte längre ska kunna läsa RMS-skyddat innehåll.
-   När du vill förhindra att ett visst RMS-aktiverat program kan användas till att öppna innehåll om programmet inte längre är betrott.
-   När du vill förhindra att inte längre önskvärt innehåll, som redan distribuerats och licensierats för användning, ska kunna användas.

Återkallning tillämpas på klienten för att hindra användare från att använda innehåll trots att en användarlicens har utfärdats för det. När du aktiverar återkallning tillämpas den varje gång en användare försöker använda skyddat innehåll, oavsett om användaren har ett lokalt sparat exemplar av användarlicensen eller begär en ny licens direkt från RMS-servern.

I avsnittet ges en översikt av återkallningsfunktionen. Information om hur du använder återkallning tillsammans med RMS finns i ”Hantera återkallning” i ”Använda en RMS-server”.

Avsnittet behandlar:

-   [Så här fungerar återkallning i RMS](https://technet.microsoft.com/469e3938-a59b-4c92-9779-ead64e724d00)
-   [Listor över återkallade certifikat i RMS](https://technet.microsoft.com/688d4dfa-c928-4b2f-8116-2f9e87d2b6f7)
-   [Återkallning i principmallar för rättigheter](https://technet.microsoft.com/287c5b92-fcb5-4295-9c2b-4e37e643beb2)
-   [Återkallning och ej anslutna användare](https://technet.microsoft.com/a9cf0541-9101-4e90-9c56-7c1b9a8deca6)
