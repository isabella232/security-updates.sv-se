---
TOCTitle: Så här fungerar RMS
Title: Så här fungerar RMS
ms:assetid: 'd7ddcc38-b7e3-4a2a-9506-7db44f7cb56e'
ms:contentKeyID: 18124925
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747763(v=WS.10)'
---

Så här fungerar RMS
===================

Begreppet ”Rights Management Services (RMS)” omfattar alla server- och klienttekniker som krävs för hantering av informationsrättigheter i en organisation. RMS-certifierings- och licensieringsservrarna i organisationen certifierar betrodda enheter i RMS-systemet, tillsammans med de Microsoft-baserade RMS-tjänsterna (för registrering, aktivering och RMS-kontocertifieringstjänsterna). Dessutom utfärdar RMS-licensieringsservrarna i organisationen publicerings- och användarlicenser som styr hur RMS-skyddat innehåll används av RMS-klientprogrammen. RMS-klienttekniker, inklusive RMS-klienter, lockbox och RMS-aktiverade program, körs på klientdatorer och gör det möjligt för användare att skapa, publicera och använda RMS-skyddat innehåll.

De olika klient- och serverteknikerna i Windows RMS samverkar och tillhandahåller följande funktioner:

-   **Skapa RMS-skyddat innehåll**. Användare som är betrodda enheter i ett RMS-system kan enkelt skapa och hantera skyddade filer med program och verktyg som är försedda med RMS-funktioner. Dessutom kan RMS-aktiverade program använda centralt definierade och officiellt auktoriserade principmallar för rättigheter som hjälper användare att tillämpa en fördefinierad uppsättning företagsanvändarprinciper. RMS-aktiverade program utvecklas av Microsoft och andra utvecklingsföretag och kan användas tillsammans med RMS-installationer.
-   **Licensiering och distribution av RM-skyddat innehåll**. Certifikat som utfärdas med servrarna i ett RMS-system identifierar de betrodda enheter som kan publicera och använda RMS-skyddat innehåll. Användare som är betrodda enheter i ett RMS-system kan dela ut åtkomsträttigheter och villkor till innehåll som de skapar och vill skydda. De här användarprinciperna anger vem som kan använda innehållet och vad som får göras med det. Författare kan begära publiceringslicenser som binder användarprinciperna till det aktuella innehållet. De kan sedan distribuera innehållet t.ex. genom att skicka det till andra användare i organisationen, lägga det på interna servrar om det ska vara tillgängligt för hela organisationen eller distribuera det till betrodda externa partner.
    I RMS-systemet verifieras de betrodda enheterna genom en publiceringslicensbegäran, i en process som användarna själva kan övervaka. Därefter utfärdas en licens med de aktuella åtkomsträttigheterna och villkoren för innehållet. I det RMS-aktiverade programmet genereras sedan symmetriska nycklar som används till att kryptera innehållet. När innehållet har skyddats med den här funktionen kan bara de användare som har angetts i publiceringslicenserna dekryptera och använda innehållet. De användarna måste också vara betrodda enheter i RMS-systemet.
-   **Hämta licenser för dekryptering av RMS-skyddad information och framtvinga användarprinciper**. Användare som är betrodda enheter kan använda RMS-skyddat innehåll med betrodda klienter. Klienterna är RMS-aktiverade datorer och program som gör det möjligt för användare att visa och arbeta med RMS-skyddat innehåll, bevara innehållets integritet och framtvinga användarprinciper. När en användare vill ha åtkomst till RMS-skyddat innehåll skickas förfrågningar till en RMS-server som utfärdar användarlicenser för den användare som vill använda innehållet.
    På RMS-servern utfärdas unika användarlicenser som kan läsas och tolkas på RMS-klienten, i en process som är överskådlig för användaren. På RMS-klienten kontrolleras innehållets certifikatkedja och listan över återkallat innehåll granskas om det behövs för att fastställa att alla kriterier som fastställer innehållets giltighet är uppfyllda. Därefter tillämpas de användarrättigheter och villkor som anges för användaren i enlighet med publiceringslicensen. Om alla rättigheter och villkor för användning har uppfyllts använder det RMS-aktiverade programmet den innehållsnyckel som utfärdats på RMS-servern till att dekryptera innehållet. Åtkomsträttigheterna och villkoren är beständiga och kan framtvingas oavsett vart innehållet skickas.
-   Mer information om hur du skapar RMS-skyddat innehåll finns i ”RMS-aktiverade program” i ”Teknisk referens för RMS”.
-   Mer information om hierarkin av betrodda enheter i ett RMS-system finns i ”Förtroendehierarki” i ”Teknisk referens för RMS”.
-   Mer information om hur du publicerar och använder RMS-skyddat material finns i ”Publicering” i ”Teknisk referens för RMS”.
-   Mer information om processen med publicering och användning av RMS-skyddat innehåll finns i ”Publicera” i ”Teknisk referens för RMS”.
