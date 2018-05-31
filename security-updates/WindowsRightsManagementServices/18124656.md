---
TOCTitle: Rättighetskontocertifikat
Title: Rättighetskontocertifikat
ms:assetid: '2ff315cc-211d-4e6e-85e8-56867c2abd94'
ms:contentKeyID: 18124656
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720230(v=WS.10)'
---

Rättighetskontocertifikat
=========================

En organisation måste ange vilka användare som ska vara betrodda enheter i deras RMS-system. Det görs genom att utfärda rättighetskontocertifikat som knyter användarkonton till enskilda datorer. Användarens rättighetskontocertifikat måste finnas med i varje begäran om klientlicensieringscertifikat och användarlicenser. Ett klientlicensieringscertifikat ger en användare rättighet att publicera RMS-skyddat innehåll, t.ex. filer och e-post, när denne är offline. En användarlicens ger användare rättighet att använda RMS-skyddat innehåll. Varje rättighetskontocertifikat innehåller användarens offentliga nyckel, som används till att kryptera information som är avsedd för den användaren.

Det finns två typer av rättighetskontocertifikat: Standardcertifikat och temporära certifikat. Du kan ange giltighetstiden för båda typerna. Giltighetstiden för standardcertifikat anges i dagar (365 dagar om inget annat anges). Giltighetstiden för temporära certifikat anges i minuter (15 minuter om inget annat anges). Ett temporärt kontocertifikat ger en användare rättighet att tillfälligt använda innehåll, t.ex. i en informationskiosk, när denne inte har tillgång till sin egen dator. Detta förhindrar att en annan användare kan använda innehållet på samma dator vid ett senare tillfälle.
