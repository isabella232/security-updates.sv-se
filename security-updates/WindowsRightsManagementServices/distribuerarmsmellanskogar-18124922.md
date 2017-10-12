---
TOCTitle: Distribuera RMS mellan skogar
Title: Distribuera RMS mellan skogar
ms:assetid: 'd531dfdc-efff-4eb0-8d99-f1fd19d7a963'
ms:contentKeyID: 18124922
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747685(v=WS.10)'
---

Distribuera RMS mellan skogar
=============================

Om organisationen omfattar flera Active Directory-skogar och du vill att hela organisationen ska kunna använda RMS måste du konfigurera nätverket på ett sådant sätt att RMS kan identifiera och autentisera användarkonton och distributionsgrupper som tillhör olika skogar.

I RMS används Active Directory till att identifiera användare och distributionsgrupper. Om organisationens Active Directory-distribution innehåller flera skogar används kontaktobjekt till att identifiera användare och grupper som tillhör andra skogar än RMS-servern. För det här krävs tre saker:

1.  RMS-certifikatservrarna måste finnas i en annan skog och varje fjärrgrupp måste ha ett definierat kontaktobjekt.
2.  Schematillägg måste finnas i skogar med kontaktobjekt som tillåter att de pekar tillbaka på de skogar som innehåller de faktiska objekten.
3.  Kontaktobjektattributen måste vara synkroniserade så att de pekar på de skogar som innehåller de faktiska objekten.

Anta t.ex. att grupper definieras och hanteras i en skog, medan användare definieras och hanteras i en annan skog. En användare vill tilldela rättigheter till innehåll baserat på medlemskap i en viss grupp. I det här exemplet är *RMS\_Server\_U* den server i skogen som innehåller användarkonton och *RMS\_Server\_G* är den server i skogen som innehåller gruppkonton. En betrodd användardomän har upprättats mellan de två RMS-servrarna. För att *RMS\_Server\_U* ska kunna expandera det gruppmedlemskap som har angetts i publiceringslicensen mellan skogar måste det finnas ett kontaktobjekt i den lokala Active Directory-skogen som representerar den aktuella gruppen i den andra skogen. En fråga kan ställas i RMS om kontaktobjektets attribut så att det upptäcks att objektet tillhör en grupp i en annan skog. Sedan söks en RMS-server i den skogen och det fastställs om det finns ett förtroendeförhållande mellan den och den andra RMS-servern. När *RMS\_Server\_U* ställer en fråga till Active Directory om den grupp som anges i publiceringslicensen identifieras att gruppen tillhör en annan skog med hjälp av kontaktobjektet. När *RMS\_Server\_U* skickar vidare frågan till den RMS-server som anges i domänens anslutningspunkt används den anslutningspunkten till att identifiera *RMS\_Server\_G* som RMS-certifikatserver för domänen. *RMS\_Server\_U* skickar då en fråga till *RMS\_Server\_G* om gruppmedlemskapet.

Det attribut som RMS ställer frågan till är **msExchOriginatingForest**. Det här attributet installeras som standard i Active Directory-schemat när en Exchange Server 2003 är installerad i skogen. Det här attributet måste finnas i skogen för varje Active Directory-schema som deltar i RMS. Om du inte använder Exchange Server 2003 kan du lägga till de här schematilläggen om du hämtar administrationsverktyget för RMS. Verktygslådan innehåller en schemafil och instruktioner för hur du lägger till den i Active Directory.

De här attributen måste vara synkroniserade så att kontaktobjektet pekar på faktiska objekt i de andra skogarna. När attributet har lagts till i Active Directory-schemat måste du konfigurera attributet så att det fullständigt kvalificerade domännamnet (FQDN) i den skog där gruppen finns används, t.ex. ab.fabrik.se.

Det kan du göra med Microsoft Identity Integration Server (MIIS) 2003 eller Identity Integration Feature Pack (IIFP) och hanteringsagenten för den globala adresslistan i Active Directory.

Du måste se till att den lokala RMS-installationen har tillräckliga behörigheter för sökning i det externa Active Directory och för anrop av de .NET-fjärrgränssnitt som finns i den externa RMS-installationen.

Det konto som används för RMS-tjänstkontot i varje skog måste även ha läs- och körbehörighet till Active Directory för att hantera gruppexpandering mellan skogar. Läsbehörighet för Active Directory beviljas automatiskt i RMS till alla autentiserade användare med domänreferenser. Om du vill öka säkerheten kan du ta bort den behörigheten i DACL-listan (Discretionary Access Control List) och ersätta den med individuella tjänstkonton som finns i de olika skogarna.

Vilka behörigheter som krävs för RMS-tjänstkontot beror på om det finns Active Directory-förtroendeförhållanden mellan den lokala och den externa skogen eller inte. I följande lista beskrivs de förtroendemodeller och behörigheter som krävs:

-   **Ett dubbelriktat förtroende finns**. Den lokala RMS-skogen har förtroende för, och är betrodd i, den skog som gruppen tillhör. RMS-tjänstkontot för RMS-servern i båda skogarna kan vara vilket giltigt domänkonto som helst i skogen. Kontrollera att du lägger till det lokala RMS-tjänstkontot i DACL-listan i mappen \\Inetpub\\wwwroot\\\_wmcs\\drmRemote på alla RMS-servrar i den skog som gruppen tillhör.
-   **Ett enkelriktat förtroende finns**. Den lokala RMS-skogen har förtroende för, men är inte betrodd i, den skog som gruppen tillhör. RMS-tjänstkontot för alla RMS-servrar i organisationen ska vara från ett giltigt domänkonto i den betrodda skogen. Lägg till det kontot i DACL-listan i mappen \\Inetpub\\wwwroot\\\_wmcs\\drmRemote på alla Windows RMS-servrar i den skog som gruppen tillhör.
-   **Inget förtroende finns**. Skogarna i organisationen kan inte autentisera användare och grupper från andra skogar. Du bör inte använda gruppexpansion mellan skogar om de skogar som ingår inte har något förtroendeförhållande. Men om det krävs för driften kan du göra det möjligt genom att konfigurera RMS-tjänstkontot som ett giltigt domänkonto i båda skogarna, med samma användarnamn och lösenord för båda. Dessutom måste ett lokalt datorkonto skapas på varje RMS-frontserver som också har exakt samma användarnamn och lösenord som de domänkonton som används som RMS-tjänstkonton i båda skogarna. Det ger automatiskt den lokala tjänsten tillräckliga behörigheter att autentisera både till det externa Active Directory och till den externa RMS-servern.

Använda principer för förtroenden i RMS
---------------------------------------

När RMS distribueras i en organisation med flera skogar måste en RMS-certifikatserver distribueras i varje skog som tillhandahåller användarkonton som deltar i RMS-systemet. Om du vill att användare i olika skogar ska kunna dela RMS-skyddat innehåll behöver du konfigurera principerna för RMS-förtroenden så att de certifikat och licenser som genereras av den andra RMS-servern blir betrodda. Det finns två typer av principer för förtroenden som kan användas med RMS: Betrodda användardomäner och betrodda publiceringsdomäner. Med betrodda användardomäner har RMS-servern förtroende för de rättighetskontocertifikat som genereras av andra RMS-certifikatservrar och utfärdar användarlicenser för användare med rättighetskontocertifikat från en annan server. Med betrodda publiceringsdomäner kan RMS-servern generera användarlicenser som baseras på de publiceringslicenser som hör till den andra licensieringsservern.

Här följer några alternativ för hur du kan använda principer för förtroenden i flera skogar:

-   Ett RMS-certifikatkluster i varje skog med ett enda licensieringskluster som delas av alla användare. RMS-licensieringsklustret konfigureras då med en betrodd användardomän som innehåller alla RMS-certifikatkluster. RMS-klienterna konfigureras med hjälp av en registernyckel till att ansluta till licensieringsklustret för att få användarlicenser.
-   Ett RMS-certifierings- och licensieringskluster i varje skog med en betrodd användardomän konfigurerad på varje kluster med förtroende för RMS-servrarna i de andra skogarna. Varje användare använder då RMS-servern i den egna skogen till att få användarlicenser och kan identifiera sin licensieringsserver via anslutningspunkten i Active Directory.
-   Om den som använder RMS-skyddat innehåll tillhör en skog som inte har åtkomst till den skog där innehållet publicerades kan en betrodd publiceringsdomän etableras så att innehållet kan licensieras och användas. För betrodda publiceringsdomäner krävs att den privata nyckel som användes av RMS-servern till att publicera innehållet importeras.

Mer information om hur du konfigurerar principer för förtroenden finns i ”Hantera förtroenden och principer för förtroenden” i ”Använda en RMS-server”.
