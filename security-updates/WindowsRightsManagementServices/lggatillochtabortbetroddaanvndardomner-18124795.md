---
TOCTitle: Lägga till och ta bort betrodda användardomäner
Title: Lägga till och ta bort betrodda användardomäner
ms:assetid: '7c440b15-01c4-49f1-b43c-00f67f3388c1'
ms:contentKeyID: 18124795
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747571(v=WS.10)'
---

Lägga till och ta bort betrodda användardomäner
===============================================

Som standard går det inte att behandla begäran i RMS från användare vars rättighetskontocertifikat har utfärdats på en annan RMS-installation. Men du kan lägga till användardomäner i listan över betrodda användardomäner, så att det går att bearbeta en sådan begäran.

För varje betrodd domän kan du också lägga till och ta bort specifika användare och grupper. Dessutom kan du ta bort en betrodd användardomän, men du kan inte ta bort rotcertifikatklustret för den aktuella Active Directory-skogen från de betrodda användardomänerna. Varje RMS-server i en distribution, inklusive rotcertifikatservern, har förtroende för rotcertifikatklustret i den egna skogen.

Gör så här om du vill hantera betrodda användardomäner:

-   Lägg till Microsoft® .NET Passport-tjänsten i listan över betrodda domäner om du vill hantera externa användare i allmänhet. På så sätt går det att bearbeta licensieringsbegäran med en RMS-server i företaget med ett rättighetskontocertifikat som utfärdats av Microsoft .NET Passport-tjänsten.
-   Lägg till en organisation i listan över betrodda användardomäner om du vill skapa förtroende för externa användare från en RMS-installation i den aktuella organisationen. På så sätt går det att använda RMS-servern till att bearbeta begäran med rättighetskontocertifikat som har utfärdats av en RMS-server i den andra organisationen.
-   På samma sätt kan du lägga till en RMS-installation som tillhör en annan Active Directory-skog i listan över betrodda användardomäner, om du vill bearbeta licensieringsbegäran från användare i den egna organisationen som tillhör den aktuella skogen. Det gör att en RMS-server i en skog kan användas till att bearbeta licensieringsbegäran med ett rättighetskontocertifikat som har utfärdats med en RMS-server i den andra skogen.
-   Du kan ange vilka e-postdomäner som är betrodda för varje betrodd användardomän. Du kan ange vilka e-postanvändare eller domäner som inte är betrodda för betrodda Passport-domäner.

Om du vill lägga till en RMS-installation i listan över betrodda användardomäner måste du importera serverlicensieringscertifikatet för den RMS-installation du vill lägga till. Administratören måste först exportera serverlicensieringscertifikatet från den server eller det kluster som du vill skapa förtroende för och skicka certifikatfilen till dig. Du kan sedan importera filen genom att ange filens plats. Den inloggade användaren måste ha behörighet till den delade mappen för att kunna spara filen. Informationen om privata nycklar överförs inte när du konfigurerar en betrodd användardomän.

Stegvisa instruktioner om hur du etablerar betrodda användardomäner finns i ”[Så här lägger du till en betrodd användardomän](https://technet.microsoft.com/ed672e58-6272-4ac0-a434-d1d938037e93)” senare i det här avsnittet.
