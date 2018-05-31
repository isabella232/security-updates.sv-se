---
TOCTitle: Användarlicenser och externa användare
Title: Användarlicenser och externa användare
ms:assetid: '02db9bda-180e-438f-863d-26252083a471'
ms:contentKeyID: 18124626
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720176(v=WS.10)'
---

Användarlicenser och externa användare
======================================

I RMS kan författare dela skyddat innehåll med autentiserade externa användare via Internet. RMS ger samma skydd för publicering mot interna och externa användare i och med att de rättigheter som bifogas innehållet måste licensieras av en RMS-server. Det här medför att företag kan dela ut och arbeta tillsammans med konfidentiella dokument, t.ex. kontrakt, via Internet.

Externa användare får normalt tillgång till RMS via Internet. (Om en extern användare kan ansluta direkt till det interna nätverket, t.ex. via en VPN-anslutning, är han eller hon funktionellt helt likställd med en intern användare.) Oavsett om användaren finns på det företag som publicerar innehållet eller utanför det, är processen då användarlicensen anskaffas i allt väsentligt densamma som beskrivs i ”[Skaffa en användarlicens](https://technet.microsoft.com/0b6cde34-418a-4dee-9d27-b65b93b535ac)” tidigare i det här avsnittet. Användaren behöver inte befinna sig i samma nätverk som användaren eller ha ett användarkonto i nätverket för att kunna begära en användarlicens.

Allt som krävs är att:

-   Användaren har ett giltigt rättighetskontocertifikat.
-   Användaren har tillgång till den RMS-licensieringsserver som utfärdat publiceringslicensen. Servern kan finnas i ett intranät eller extranät.
-   Den RMS-installation där användarens kontocertifikat utfärdats finns med i listan över betrodda domäner i den RMS-installation som utfärdar användarlicensen.

Följande typer av externa användare kan skaffa användarlicenser:

-   Användare vars konton är en del av en annan Active Directory-skog som också har en RMS-installation. RMS-installationen i den andra skogen måste vara definierad som en betrodd användardomän för denna installation.
-   Användare på ett annat företag som också kör en RMS-installation som har lagts till i listan över betrodda användardomäner för denna installation.
-   Användare som har rättighetskontocertifikat som baseras på .NET Passport när Microsoft RMS Certification Service finns med i listan över betrodda användardomäner för denna installation.

Du kan lägga till ett annat företag eller en annan RMS-installation i ditt företag i listan över betrodda domäner. När du har lagt till en domän kan du definiera vilka e-postdomäner som ska vara betrodda i domänen och välja om säkerhetsidentifierare (SID:er) ska vara betrodda eller ej i domänen.

Ett annat företag eller en annan RMS-installation i ditt företag kan lägga till din RMS-installation i sin lista över betrodda domäner så att deras RMS-servrar kan behandla begäran om användarlicenser från dina användare.

Mer information om hur du skapar betrodda användardomäner mellan RMS och andra organisationer finns i ”[Betrodda användardomäner](https://technet.microsoft.com/a09b883f-f455-4c46-a4fd-d37b689e1d24)” senare i det här avsnittet och ”Lägga till och ta bort betrodda publiceringsdomäner” i ”Använda en RMS-server”.
