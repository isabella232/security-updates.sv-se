---
TOCTitle: Användarlicenser
Title: Användarlicenser
ms:assetid: '6e609db3-49b3-4cac-a34c-8a96da627067'
ms:contentKeyID: 18124768
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747612(v=WS.10)'
---

Användarlicenser
================

För att kunna använda RMS-skyddat innehåll måste varje användare ha en användarlicens. Användarlicensen anger vilka behörigheter en viss användare har för att använda det RMS-skyddade innehållet. En användarlicens utfärdas av den server som utfärdat motsvarande publiceringslicens.

Varje användare som tar emot RMS-skyddat innehåll och som har angetts i publiceringslicensen för innehållet kan begära en användarlicens. Ett RMS-aktiverat program använder sedan funktionerna i RMS till att läsa, tolka och tillämpa de användningsrättigheter som bifogas innehållet.

En användarlicens innehåller den symmetriska innehållsnyckeln för dekryptering av innehållet och den krypteras med användarens offentliga nyckel. På så sätt säkerställs att endast den användare som skickat begäran kan använda det RMS-skyddade innehållet. En användarlicens signeras av den privata nyckeln för den server som utfärdar användarlicensen.
