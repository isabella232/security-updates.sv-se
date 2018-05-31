---
TOCTitle: Säkerhet vid normal drift
Title: Säkerhet vid normal drift
ms:assetid: '98f3d584-6320-4aa1-9959-7133cfdb6df7'
ms:contentKeyID: 18124832
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747609(v=WS.10)'
---

Säkerhet vid normal drift
=========================

När du har installerat och etablerat RMS fungerar RMS-webbtjänsterna som IIS-program. Eftersom de använder olika systemresurser krävs autentisering och auktorisering. Alla systemresurser kräver autentisering för att kunna konfigureras. På resten av den här sidan beskrivs hur du skapar auktorisering i RMS.

RMS-webbtjänsterna körs i en IIS-programpool. Varje programpool i IIS har en unik identitet som kan motsvara ett domänanvändarkonto, ett lokalt användarkonto, det lokala nätverkstjänstkontot eller det lokala systemkontot. Vart och ett av dessa konton har olika grader av auktorisering i systemet. När RMS har etablerats kan du välja att köra RMS-webbtjänsterna under det lokala systemkontot eller under ett domänanvändarkonto. Det aktuella kontot utgör då programpoolsidentiteten för RMS-programpoolen. Programpoolen för sidan Global administration är ”DRMS Application Pool”. Programpoolen för den webbplats som du etableras kallas "\_DRMSAppPool1". Loggningstjänsten i RMS körs som en separat Windows-tjänst under samma konto som anges för programpoolsidentiteten för RMS.

De resurser som krävs för RMS-webbtjänsternas åtkomst inkluderar flera olika filer och mappar i systemet, databaser och lagrade procedurer i SQL, det lokala registret, Active Directory, sammanställningscachen, minnet och andra processer som körs på systemet. För loggningstjänsten i RMS behövs också åtkomst till loggningskön i det lokala systemet. Var och en av dessa resurser har en egen DACL som definierar vem som är auktoriserad att komma åt resursen och vad det går att göra med den.

Alla nödvändiga behörigheter är tilldelade den lokala RMS-tjänstgruppen som RMS skapade under etableringen vilket förenklar tilldelandet av rättigheter och hantering av tjänstekonton. Eftersom RMS-tjänstgruppen tillhör den här gruppen har den också alla behörigheter som tilldelats gruppen.

I följande lista summeras de behörigheter som beviljas RMS-tjänstgruppen:

-   Läsbehörighet till de virtuella rotkatalogerna
-   Skrivbehörighet till sammanställningscachens katalog
-   Skrivbehörighet till systemets temporära katalog
-   Skrivbehörighet till loggningskön
-   Läsbehörighet till Active Directory

Du bör vara medveten om att i Microsoft SQL Server 2000 används en något annorlunda metod för att tilldela behörigheter än i Windows Server 2003. Under etableringen av RMS skapas inloggningsreferenser för RMS-tjänstkontot på SQL-servern. Om du valde att etablera RMS med det lokala systemkontot skapas SQL Server-inloggningsreferenser med formatet *DOMÄN\\datornamn*, där *DOMÄN* är namnet på den Active Directory-domän som datorn tillhör och *datornamn* är namnet på servern. En SQL-roll med namnet rms\_service skapas och tilldelas alla nödvändiga behörigheter. Inloggningsreferenserna för RMS-tjänstkontot läggs till i den aktuella gruppen. Inga behörigheter tilldelas RMS-tjänstkontot explicit.

Dessutom tilldelar SQL Server en databasägare (DBO) till varje databas. Databasägarskap tilldelas på följande sätt under etableringen:

-   DBO för konfigurationsdatabasen tilldelas det domänanvändarkonto som användes vid etableringen av RMS.
-   DBO för katalogtjänst- och loggningsdatabaser tilldelas RMS-tjänstkontot.

De behörigheter som tilldelas de resurser som har skapats av RMS har valts med omsorg och med tanke på systemets säkerhet under skapandet av RMS. Normalt finns det inte någon anledning att ändra de behörigheter som har tilldelats någon resurs under etableringen. Om du vill ändra användarkontot eller lösenordet för tjänstkontot efter etableringen kan du göra det från webbsidan Global administration av RMS. Mer information finns i ”Så här ändrar du RMS-tjänstkontot” i ”Använda en RMS-server”.
