---
TOCTitle: Betrodda publiceringsdomäner
Title: Betrodda publiceringsdomäner
ms:assetid: 'bca1c33a-d3ef-42b5-adbe-6e104979a71f'
ms:contentKeyID: 18124873
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747738(v=WS.10)'
---

Betrodda publiceringsdomäner
============================

Som standard utfärdas inte användarlicenser av RMS-servrar mot publiceringslicenser som utfärdats av en RMS-server i ett annat kluster. Det finns dock tillfällen när samma server eller kluster inte kan utfärda både publicerings- och användarlicenser för ett skyddat innehåll. Det kan t.ex. inträffa när ett RMS-kluster tas ur bruk och ersätts av ett annat, exempelvis när två företag går samman. I ett sådant fall måste ett RMS-kluster ha möjlighet att utfärda användarlicenser mot publiceringslicenser som skapats av ett annat RMS-kluster.

Du kan konfigurera ett RMS-kluster så att de publiceringslicenser som utfärdats av ett annat RMS-kluster blir betrodda. Därmed kan användarlicenser utfärdas från klustret mot dessa licenser genom att en betrodd publiceringsdomän implementeras. Det åstadkoms genom att importera den andra serverns licensieringscertifikat och privata nyckel och sedan lägga till den i listan över betrodda domäner. De privata nycklar som importeras används endast för att dekryptera signerade publiceringslicenser och inte för att signera nya licenser.

Mer information om betrodda användardomäner och stegvisa instruktioner finns i ”Lägga till och ta bort betrodda publiceringsdomäner” och ”Upprätta principer för förtroenden” i ”Använda en RMS-server”.
