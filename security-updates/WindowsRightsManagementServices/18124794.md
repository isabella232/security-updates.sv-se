---
TOCTitle: Sätta upp mål för topologin
Title: Sätta upp mål för topologin
ms:assetid: '8275a04d-3e5b-40b0-be9d-2f31b7aeca6b'
ms:contentKeyID: 18124794
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747652(v=WS.10)'
---

Sätta upp mål för topologin
===========================

Ett av de viktigaste stegen vid topologidesign är att sätta upp lämpliga mål. Några av de nyckelområden som du bör tänka på när du designar RMS-topologin är:

-   **Administrativa kostnader**. Platstopologin ska minimera de administrativa kostnaderna. Det här omfattar centraliserad serverhantering när så är möjligt och en minimering av antalet använda servrar.
-   **Nätverkets svarstid**. Nätverkets svarstid i kommunikationen mellan klienterna och servern kommer att vara märkbar för användarna i form av en fördröjning när de öppnar e-postmeddelanden och dokument. Svarstiden bör vara mindre än två sekunder i båda riktningarna i minst 90 procent av alla tillfällen.
-   **Tillförlitlighet**. Nätverket mellan klienterna och servern måste vara så tillförlitligt att felfrekvensen, d.v.s. förlorade eller skadade transaktioner, för en enskild HTTP-begäran inte överstiger 5 procent.

Det här är bara allmänna riktlinjer. Du måste själv sätta upp egna mål baserade på organisationens krav och resurser. Att sätta upp mål är det första steget till att bestämma om en topologi motsvarar organisationens behov. Det finns många faktorer som påverkar hur väl de här målen uppfylls, bl.a. antalet användare, licensbegäran, frågor och meddelanden samt andra faktorer som påverkar RMS-trafiken. Dessutom kan den planerade distributionsstrategin (inklusive i vilka domäner och skogar RMS ska distribueras) ha stor inverkan på hur väl topologimålen uppfylls. Under processen med att skapa en topologi måste du ha de här målen i åtanke och bedöma hur varje steg i processen påverkar dem.
