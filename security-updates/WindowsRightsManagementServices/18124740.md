---
TOCTitle: 'Vanliga frågor om RMS: Intern och extern åtkomst'
Title: 'Vanliga frågor om RMS: Intern och extern åtkomst'
ms:assetid: '59c2c51f-6c20-450c-a334-0e1486292074'
ms:contentKeyID: 18124740
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747577(v=WS.10)'
---

Vanliga frågor om RMS: Intern och extern åtkomst
================================================

Vanliga frågor om intern och extern åtkomst till RMS
----------------------------------------------------

-   [Vilka ändringar måste jag göra för brandväggen för att RMS-klienter utanför brandväggen ska ges åtkomst till RMS-servrar?](#bkmk_37)
-   [Hur fungerar extranät-scenariot?](#bkmk_38)
-   [Om en användare skapar rättighetsskyddat innehåll och ger det till någon som inte har åtkomst till RMS-installationen, kan den personen då använda innehållet?](#bkmk_39)
-   [Vad krävs för att en kund ska kunna läsa ett rättighetsskyddat e-postmeddelande som jag skickar via Outlook 2003 eller Outlook 2007?](#bkmk_40)
-   [Hur kan organisationer som har egna RMS-servrar utbyta rättighetsskyddat innehåll?](#bkmk_41)
-   [Jag har skickat ett e-postmeddelande som är RMS-skyddat till en extern organisation som inte har funktioner för Outlook. Kan mottagaren svara på meddelandet om det öppnats med hjälp av tilläggskomponenten Rights Management med Internet Explorer?](#bkmk_42)

<span id="BKMK_37"></span>
#### Vilka ändringar måste jag göra för brandväggen för att RMS-klienter utanför brandväggen ska ges åtkomst till RMS-servrar?

Brandväggen måste tillåta SOAP-begäran (Simple Object Access Protocol) från externa datorer till RMS-servern över HTTP (TCP-port 80) eller HTTPS (TCP-port 443).

<span id="BKMK_38"></span>
#### Hur fungerar extranät-scenariot?

Publiceringslicenser innehåller två URL:er som är bundna till innehållet. En är intranät-URL:en som anges när RMS-klustret etableras. Den andra är en extranät-URL som kan anges av RMS-administratören. Med hjälp av extranät-URL:en kan klienten hämta användarlicenser utanför brandväggen. En extranät-URL kan inte användas till att skapa nytt rättighetsskyddat innehåll. För att det ska fungera måste RMS-klientregistret åsidosättas.

<span id="BKMK_39"></span>
#### Om en användare skapar rättighetsskyddat innehåll och ger det till någon som inte har åtkomst till RMS-installationen, kan den personen då använda innehållet?

Om användaren inte har någon anslutning till RMS-installationen när det skyddade innehållet öppnas för första gången kan användaren inte använda innehållet.

Observera att Office 2003 och senare automatiskt får användarlicenser för rättighetsskyddad e-post när det synkroniseras så att e-posten kan läsas utan nätverksanslutning. Trots att användarlicenser för e-postmeddelanden cachelagras automatiskt i Outlook 2003 och senare versioner så har bifogade dokument skapade i Excel 2007, Excel 2003, Word 2007, Word 2003, PowerPoint 2007 eller PowerPoint 2003 samma rättigheter som det e-postmeddelande de bifogades i. De synkroniseras inte automatiskt när e-postmeddelandet hämtas och måste öppnas separat när datorn är ansluten till nätverket för att få en användarlicens.

<span id="BKMK_40"></span>
#### Vad krävs för att en kund ska kunna läsa ett skyddat e-postmeddelande som jag skickar via Outlook 2003 eller Outlook 2007?

Mottagaren måste använda antingen Outlook 2003, Outlook 2007 eller tilläggskomponenten Rights Management for Internet Explorer. Om ett förtroendeförhållande etablerats mellan RMS-installationen i din och mottagarens organisation kan mottagaren läsa e-postmeddelandet utan ytterligare åtgärder. Förtroendeförhållandet etableras genom att de RMS-serverlicensieringscertifikat som innehåller de offentliga nycklarna utbyts.

Om mottagarens organisation inte har en RMS-infrastruktur eller om inget förtroendeförhållande har etablerats kan du be kunden att etablera ett Windows Live-ID. Skicka sedan e-postmeddelandet till mottagaren genom att ange de rättigheter som tilldelats kundens inloggningsuppgifter för Windows Live-ID. Med det här tillvägagångssättet används Microsoft IRM-tjänsten som finns på Internet till att hämta en användarlicens. IRM-tjänsten tillhandahålls kostnadsfritt så att du kan använda IRM på prov, och den är endast avsedd för test av RMS. Om du väljer att skydda innehåll med hjälp av den här tjänsten måste du vara medveten om att den kan avslutas utan föregående meddelande i framtiden.

<span id="BKMK_41"></span>
#### Hur kan organisationer som har egna RMS-servrar utbyta rättighetsskyddat innehåll?

I RMS används betrodda användardomäner där användarcertifikat som genereras i en RMS-installation är betrodda i en annan.

<span id="BKMK_42"></span>
#### Jag har skickat ett e-postmeddelande som är RMS-skyddat till en extern organisation som inte har funktioner för Outlook. Kan mottagaren svara på meddelandet om det öppnats med hjälp av tilläggskomponenten Rights Management med Internet Explorer?

E-postmottagaren kan svara på ett rättighetsskyddat e-postmeddelande precis som vanligt, men originaltexten i det mottagna meddelandet fortsätter att vara rättighetsskyddad för de ursprungliga mottagarna. Hur e-postmeddelandet paketeras bestäms i klientprogrammet. Det ursprungliga e-postmeddelandet kan bifogas i svaret som en krypterad bifogad fil eller så kan det tas bort helt, vilket exempelvis görs i Outlook 2003 och Outlook 2007.
