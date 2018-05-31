---
TOCTitle: Betrodda användardomäner
Title: Betrodda användardomäner
ms:assetid: 'a09b883f-f455-4c46-a4fd-d37b689e1d24'
ms:contentKeyID: 18124838
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747618(v=WS.10)'
---

Betrodda användardomäner
========================

Som standard utfärdas inte användarlicenser i RMS till användare vars rättighetskontocertifikat har utfärdats med en annan användardomän. En användardomän är en RMS-installation som består av ett rotcertifikatkluster, valfria licensieringsservrar eller kluster och tillhörande databaser.

Du kan konfigurera RMS så att begäran av den här typen kan behandlas genom att serverlicensieringscertifikatet för en annan användardomän importeras och läggs till i listan över betrodda användardomäner. När du gör det kan användare vars kontocertifikat utfärdats av den betrodda användardomänen begära användarlicenser i din installation. En sådan begäran om användarlicenser behandlas som om det vore en begäran från en intern användare.

| ![](images/Cc747618.note(WS.10).gif)Obs!                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------|
| Rotcertifikatklustret finns automatiskt med i listan över betrodda användardomäner för alla RMS-servrar som ingår i samma installation. |

Du kan tillåta användare från olika användardomäner att dela skyddat innehåll. Detta beskrivs i följande exempel:

-   Ditt företag har ett nära samarbete med ett annat företag och ska kunna dela konfidentiella dokument som du vill skydda. Det andra företaget använder också RMS. De båda företagen kan lägga till varandras RMS-installationer i sina respektive listor över betrodda användardomäner, så att användare i båda företagen kan arbeta tillsammans med skyddat innehåll och skicka det via Internet eller ett extranät.
-   Det går bara att ha en RMS-installation i varje Active Directory-skog. Ditt företag har distribuerat mer än en Active Directory-skog och alla kör RMS. Användarna vill kunna dela skyddat innehåll med andra oavsett vilken skog de tillhör. Du kan tillåta det genom att lägga till de andra skogarnas RMS-installationer i listan över betrodda användardomäner i varje skog.
-   Användare på ditt företag samarbetar med användare på ett annat företag med konfidentiella dokument som de vill skydda. Det andra företaget använder inte RMS. Användare på det andra företaget kan skaffa .NET Passport-konton, så kan du lägga till .NET Passport i listan över betrodda domäner för din RMS-installation. Användare på båda företagen kan nu arbeta med skyddat innehåll och skicka det via Internet.

Mer information om betrodda användardomäner och stegvisa instruktioner finns i ”Lägga till och ta bort betrodda användardomäner” och ”Upprätta principer för förtroenden” i ”Använda en RMS-server”.
