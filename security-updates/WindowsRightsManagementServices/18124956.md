---
TOCTitle: Bestämma åtkomstkrav
Title: Bestämma åtkomstkrav
ms:assetid: 'eb2ce9a5-0430-4811-bd40-4a94a84426a8'
ms:contentKeyID: 18124956
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747790(v=WS.10)'
---

Bestämma åtkomstkrav
====================

Vid den här delen av planeringsfasen bör du ha bestämt omfattningen av din RMS-implementering. När du ska ange säkerheten i RMS-systemet bör du också överväga metoder för att begränsa omfattningen till vissa deltagare och säkerställa att de data som skyddas med RMS också skyddas genom traditionell informationssäkerhetspraxis. Du bör också se till att endast betrodda administratörer har åtkomst till administration och konfiguration av RMS-servern. Följande åtkomstsäkerhetsmetoder kan användas med RMS:

-   **Åtkomstlistor (ACL)**. Alla webbtjänster i RMS samt administrationswebbplatsen kan skyddas med åtkomstlistor. För att säkerställa att endast användare med behörighet att använda RMS-tjänsten kan göra det, kan du använda åtkomstlistor till att begränsa möjligheten för användare att ansluta till certifierings- och licensieringstjänsterna i RMS. Det kan vara användbart om du vill att vissa grupper ska kunna skapa skyddat innehåll eller om du bara vill att vissa grupper ska få licenser för skyddat innehåll.
-   **Klientautentisering**. Du kan också kräva smartkort eller annan klientautentisering när användare försöker få användarlicenser eller certifikat. Det kan minska risken för att obehöriga användare öppnar innehåll via behöriga användares sessioner.
-   **SSL (Secure Sockets Layer)**. Du kan också kräva en SSL-anslutning mellan RMS-klienterna och RMS-servern för att skapa ett extra säkerhetslager. Vi rekommenderar att du aktiverar SSL och kräver 128-bitars-kryptering för varje RMS-webbtjänstfil. De här filerna har filnamnstillägget .asmx och finns i de virtuella katalogerna Licensiering, Certifiering och Admin. Om du vill öppna **administrationswebbsidorna för RMS** från en webbläsare på en fjärrdator måste du aktivera SSL. Men även om du aktiverar SSL går det inte att öppna sidan **Global administration** från en fjärrdator.
    Information om hur du konfigurerar SSL på servrar finns i hjälpen för IIS.

I vissa organisationer kan det finnas behov av ett licensieringssystem för en avdelning som är skild från andra avdelningar, och som har extra säkerhet. I sådana fall kan en RMS-server användas till att etablera hanteringsprinciper för informationsrättigheter. Om en avdelning eller någon annan del av organisationen kontrollerar mycket känslig information kan du konfigurera en separat licensieringsserver eller ett separat licensieringskluster som gör det möjligt för avdelningen att hantera licensiering och publicering av innehåll oberoende av resten av organisationen. En licensieringsserver är underregistrerad under rotcertifikatservern (eller rotcertifikatklustret) som tillhandahåller certifiering och andra tjänster för varje licensieringsserver. Men licensieringsservrar tillhandahåller sina egna licensierings- och publiceringstjänster.

Användarkonton, åtkomstlistor och fysisk säkerhet är viktiga delar i distributionen. Kontrollera att du har utvärderat och implementerat alla säkerhetsmetoder och den aktuella säkerhetsmodellen på ett lämpligt sätt innan du implementerar RMS i en produktionsmiljö.
