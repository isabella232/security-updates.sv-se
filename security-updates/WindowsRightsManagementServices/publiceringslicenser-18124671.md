---
TOCTitle: Publiceringslicenser
Title: Publiceringslicenser
ms:assetid: '187228fc-370b-4e23-a53a-21bb296b84a1'
ms:contentKeyID: 18124671
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720211(v=WS.10)'
---

Publiceringslicenser
====================

I RMS-aktiverade program kan användarna tilldela filer och information särskilda användarrättigheter som ligger i linje med företagets principer. Användarrättigheterna definieras i publiceringslicenser som anger vilka användare som får läsa innehållet och i vilken utsträckning de får ändra och distribuera innehållet.

Publiceringslicenser kan utfärdas av RMS-aktiverade klientprogram, rotcertifikatservern eller en RMS-licensieringsserver. När publiceringslicenser utfärdas av RMS-aktiverade program beviljas programmet ett klientlicensieringscertifikat av RMS-servern. Det kallas offlinepublicering. Det här är en vanlig publiceringsmetod eftersom de som använder RMS-aktiverade program kan skapa skyddat innehåll utan att anslutas till RMS-servern. Om det RMS-aktiverade klientprogrammet inte använder klientlicensieringscertifikat måste användaren ansluta till en RMS-server och få en publiceringslicens för det skyddade innehållet.

En publiceringslicens innehåller den symmetriska innehållsnyckeln för dekryptering av innehållet som krypteras med användarens offentliga nyckel. På detta sätt säkerställs att endast servern kan dekryptera innehållet och utfärda användarlicenser.

En publiceringslicens signeras av den privata nyckeln för den server som utfärdat licensen eller klientlicensieringscertifikatets privata nyckel.
