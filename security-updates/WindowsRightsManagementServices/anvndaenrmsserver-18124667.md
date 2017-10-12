---
TOCTitle: 'Använda en RMS-server'
Title: 'Använda en RMS-server'
ms:assetid: '1533426b-89c2-43e0-8068-ca97ddab8606'
ms:contentKeyID: 18124667
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720205(v=WS.10)'
---

Använda en RMS-server
=====================

Rubriken Använda en RMS-server syftar på de hanteringsåtgärder som du utför när RMS har distribuerats i organisationen. I avsnittet finns information om hur du hanterar RMS-servern, procedurer vid vanliga administrativa åtgärder, resurser för mer information samt metodtips.

I det här avsnittet

-   [Hantera RMS](https://technet.microsoft.com/9b573c55-c14c-436c-b3c5-7ba445de1562)
-   [Så här gör du i RMS](https://technet.microsoft.com/82032075-f361-438f-a2c4-93ab29ae6cff)
-   [RMS-resurser](https://technet.microsoft.com/d91221cf-e38e-4add-b7b9-50e63aad9a28)

Termer som används i den här guiden
-----------------------------------

**kontocertifiering**  
En process där användarkonton associeras med nyckelpar i rättighetskontocertifikatet.

<!-- -->

**kontocertifieringstjänst**  
En RMS-webbtjänst som används till att skapa och distribuera rättighetskontocertifikat. Se även kontocertifiering.

<!-- -->

**aktiveringsproxytjänst**  
En RMS-webbtjänst där datoraktivering av klienter av RMS-version 1.0 hanteras. Används till att vidarebefordra begäran om datoraktivering till Microsofts aktiveringstjänst. Aktiveringstjänsten genererar en unik lockbox och ett motsvarande RMS-datorcertifikat för klientdatorn, som sedan skickas tillbaka med aktiveringsproxytjänsten på RMS-servern till den klient som skickat begäran. Se även lockbox.

<!-- -->

**administrationstjänst**  
En RMS-webbtjänst som omfattar administrationswebbplatsen, där du hanterar RMS och uppdaterar klustrets konfigurationsdatabas.

<!-- -->

**programmanifest**  
Ett XML-dokument med en beskrivning av modulerna i ett associerat RMS-aktiverat program och vad som kan köras i programmiljön. Alla program som skriver till RMS-klientens API:er för att skapa eller använda RMS-skyddad information måste tillhandahålla ett manifest vid körning.

<!-- -->

**attribut**  
En egenskap för ett objekt i Active Directory. För varje objektklass definierar schemat vilka attribut en instans av klassen måste ha och vilka ytterligare attribut den kan ha.

<!-- -->

**bindning**  
Metoden som gör det möjligt att använda rättigheter i ett RMS-system. RMS-klienten validerar villkoren i en användarlicens mot de rättigheter som begärs. Om villkoren uppfylls beviljas rättigheterna.

<!-- -->

**certifikat**  
Ett digitalt dokument som används för autentisering och för att skydda information i öppna nätverk. Ett certifikat binder på ett säkert sätt en offentlig nyckel till den enhet som innehar motsvarande privata nyckel. Certifikat signeras digitalt av certifikatutfärdaren (CA) och kan utfärdas för en användare, dator eller tjänst. Se även privat nyckel, offentlig nyckel.

<!-- -->

**Klientregistrering**  
Processen där ett klientlicensieringscertifikat skapas, med vilket användarens dator eller enhet skapar publiceringslicenser som bearbetas av en licensieringsserver.

<!-- -->

**klientlicensieringscertifikat**  
Ett certifikat som skapas med en RMS-server och placeras på RMS-klientdatorer med vilka användare kan publicera skyddat innehåll offline utan att vara anslutna till det RMS-aktiverade nätverket. Klientlicensieringscertifikatet innehåller den nyckel som används på RMS-klienten till att signera publiceringslicenser digitalt.

<!-- -->

**villkor**  
En uppsättning specifika restriktioner och parametrar som är en del av den grupp med rättigheter som ingår i en publiceringslicens. Villkor är tvingande när de används. Ett tidsvillkor är ett vanligt villkor som gör att användare kan ange ett förfallodatum för RMS-skyddad information.

<!-- -->

**konfigurationsdatabas**  
Den databas som innehåller RMS-konfigurationsinformationen för en server eller ett kluster.

<!-- -->

**använda innehåll**  
Att dekryptera och komma åt skyddat innehåll med hjälp av användarrättigheter.

<!-- -->

**innehållsnyckel**  
Den nyckel som används för kryptering och dekryptering av skyddat innehåll vid publicering och användning. Kallas också för symmetrisk nyckel. I RMS används 128-bitars AES-innehållsnycklar.

<!-- -->

**ägare av innehåll**  
Den person eller organisation som upprättar åtkomstprincipen för skyddat innehåll.

<!-- -->

**dekryptering**  
En process som gör krypterade data läsbara igen genom att konvertera krypterad text till vanlig text.

<!-- -->

**digital signatur**  
Ett sätt för upphovsmakaren av ett meddelande, en fil eller annan digitalt kodad information att binda sin identitet till informationen. Processen där information signeras digitalt innefattar att informationen omvandlas tillsammans med viss hemlig information som innehas av avsändaren, till en tagg som kallas en signatur. Digitala signaturer används i miljöer med offentliga nycklar och ger oavvislighet och integritetstjänster.

<!-- -->

**DRMRemote, tjänst**  
En RMS-webbtjänst som tillhandahåller tjänster via .NET Remoting, vilket används för kommunikation mellan olika RMS-servrar.

<!-- -->

**kryptering**  
En process där information konverteras till en form som endast kan läsas av en specifik mottagare. Kryptering är ett effektivt sätt att skydda information. Mottagaren måste ha en hemlig nyckel eller ett lösenord för att kunna dechiffrera en fil som har krypterats. Se även kryptering av offentlig nyckel.

<!-- -->

**registrering**  
En process där rotcertifikatservern erhåller ett serverlicensieringscertifikat som har signerats i Microsofts registreringstjänst.

<!-- -->

**registreringsbegäran**  
En begäran om ett serverlicensieringscertifikat som skickas från RMS-rotcertifikatservern till Microsofts registreringstjänst.

<!-- -->

**exkludering**  
Processen där RMS-servern avslår en klients användarlicensbegäran baserat på en exkluderingsprincip. Se även exkluderingslista.

<!-- -->

**exkluderingslista**  
En lista över enheter som nekas licenser av RMS-licensieringstjänsten.

<!-- -->

**exkluderingsprincip**  
Inställningar i RMS-konfigurationsdatabasen som kontrollerar hur exkludering tillämpas i en organisation.

<!-- -->

**XML (extensible markup language)**  
Det XML-baserade format som används av RMS för alla licenser det finns funktioner för: maskincertifikat, rättighetskontocertifikat, CLC, användarlicenser, publiceringslicenser, serverlicensieringscertifikat, som är dokument som anger vilken RMS-princip som ska tillämpas på det skyddade innehållet.

<!-- -->

**utfärdarlicens**  
Data som anger vilken RMS-princip som ska användas för skyddat innehåll.

<!-- -->

**licensieringskluster**  
En eller flera servrar som kör licensierings- och publiceringstjänsterna i RMS utanför rotcertifikatklustret. För de här servrarna används en gemensam databas och anslutnings-URL, och de ska distribueras bakom en program- eller maskinvarubaserad belastningsutjämnare om mer än en server används. Till skillnad från ett certifikat- eller rotkluster kan RMS-servrar i ett licensieringskluster inte användas till användarcertifiering.

<!-- -->

**licensieringsserver**  
En server som kör licensierings- och publiceringstjänsterna i RMS utanför rotcertifikatklustret.

<!-- -->

**licensieringstjänst**  
En RMS-webbtjänst som utfärdar användarlicenser.

<!-- -->

**lockbox**  
Den programvarumodul där autentiseringen sker av korrekt användning av skyddat innehåll, där kryptering och dekryptering av information görs samt där bearbetning med betrodd programvara skyddas från ändring och observation. Kallas även för säker lagring eller säker databas.

<!-- -->

**loggningstjänst**  
En lyssnartjänst i RMS som överför loggade data från meddelandekön till loggningsdatabasen för RMS-servern eller RMS-klustret.

<!-- -->

**datoraktivering**  
Processen där en unik lockbox och ett unikt datorcertifikat hämtas till en dator med RMS version 1.0. I RMS version 1.0 SP1 är datoraktiveringen den process då datorcertifikat hämtas för varje användare vid datorn.

<!-- -->

**manifest**  
Ett signerat XML-dokument som identifierar de bibliotek och program som kan, som inte kan och som eventuellt kan läsas in i utrymmet för programprocessen.

<!-- -->

**Microsofts aktiveringstjänst**  
En Microsoft-baserad webbtjänst som utfärdar RMS-datorcertifikat och lockbox-versioner efter begäran från RMS-klienter av version 1.0.

<!-- -->

**Microsofts registreringstjänst**  
En Microsoft-baserad webbtjänst som utfärdar ett serverlicensieringscertifikat till rotcertifikatservern i en RMS-distribution.

<!-- -->

**precertifiering**  
En funktion i RMS-certifieringstjänsten som gör det möjligt att använda ett program till att begära ett rättighetskontocertifikat från RMS-servern för en användare. Rättighetskontocertifikatet som erhålls via precertifiering innehåller bara användarens offentliga nyckel.

<!-- -->

**säkerhetsobjekt**  
En enhet (t.ex. en användare, grupp eller hanterare av skyddat innehåll) med en etablerad roll i RMS-säkerhetsschemat, och mot vilken objekt kan säkras.

<!-- -->

**privat nyckel**  
Den hemliga delen av ett krypteringsnyckelpar som används med en algoritm för offentlig nyckel. Privata nycklar används normalt vid dekryptering av symmetriska sessionsnycklar, digital signering av data eller dekryptering av data som har krypterats med tillhörande offentliga nyckel. Se även offentlig nyckel, kryptering av offentlig nyckel.

<!-- -->

**etablering**  
Att konfigurera en RMS-server så att den fungerar i en organisation.

<!-- -->

**offentlig nyckel**  
Den offentliga delen av ett krypteringsnyckelpar som används med en algoritm för offentlig nyckel. Offentliga nycklar används normalt vid kryptering av sessionsnycklar, verifiering av digitala signaturer eller kryptering av data som kan dekrypteras med tillhörande privata nyckel. Se även privat nyckel, kryptering av offentlig nyckel.

<!-- -->

**kryptering av offentlig nyckel**  
En krypteringsmetod där två krypteringsnycklar används som är matematiskt relaterade. Den ena nyckeln kallas den privata nyckeln och är konfidentiell. Den andra kallas den offentliga nyckeln och delas fritt ut till alla potentiella deltagare. I ett typiskt scenario använder avsändaren mottagarens offentliga nyckel till att kryptera meddelandet. Mottagaren är den enda som har den relaterade privata nyckeln och kan dekryptera meddelandet. Det komplicerade förhållandet mellan den offentliga och den privata nyckeln innebär, under förutsättning att nycklarna är tillräckligt långa, att det är omöjligt att avgöra vilken som är vilken. Metoden kallas även asymmetrisk kryptering. Se även privat nyckel, offentlig nyckel.

<!-- -->

**publiceringslicens**  
Den licens som skapas vid publicering av RMS-skyddat innehåll. Den anger bland annat vilka som har tillgång till innehållet, vilka rättigheter som har beviljats och under vilka villkor innehållet kan användas. Kallas även utfärdarlicens.

<!-- -->

**publiceringstjänst**  
En RMS-tjänst som signerar publiceringslicenser och utfärdar klientlicensieringscertifikat. Se även klientlicensieringscertifikat, publiceringslicens.

<!-- -->

**RAC**  
Se definitionen för rättighetskontocertifikat.

<!-- -->

**återkallning**  
En process där berörda enheter läggs till i en lista över ogiltiga licenser.

<!-- -->

**lista över återkallade certifikat**  
Ett XrML-baserat dokument med en lista över de certifikat och licenser som har återkallats av utfärdaren. Se även återkallning.

<!-- -->

**rättighet**  
En åtgärd där specifika användare beviljas åtkomst till innehåll som skyddas med RMS-teknik. Dessa rättigheter kan begränsas ytterligare med hjälp av villkor.

<!-- -->

**rättighetskontocertifikat (RAC)**  
Ett certifikat där datorcertifikatet från RMS-aktiveringen används till att binda användarkonton och nycklar till specifika datorer eller grupper av datorer. Certifikatets komponenter gör det möjligt för användarna att använda skyddat innehåll. Kallas även GIC (gruppidentitetcertifikat) i RMS SDK.

<!-- -->

**hantering av rättigheter**  
En teknik som ger ett beständigt skydd av digitala data med hjälp av kryptering, certifikat och autentisering. Godkända mottagare och användare måste erhålla en licens innan de kan använda de skyddade filerna enligt de rättigheter och företagsregler som har angetts av ägaren av innehållet.

<!-- -->

**Rights Management Services-klient**  
En uppsättning RMS-API:er som måste installeras på alla klientdatorer i ett RMS-system. De krävs för datoraktivering och för användning av RMS-aktiverade program.

<!-- -->

**principmall för rättigheter**  
Principmall för rättigheter beskriver en standarduppsättning med användare, rättigheter och villkor som kan tillämpas på RMS-skyddat innehåll. När en användare använder en principmall för rättigheter på innehåll blir de rättigheter och villkor som beskrivs i mallen en del av publiceringslicensen.

<!-- -->

**RMS-aktivering**  
En process där en lockbox placeras på en slutanvändares dator i RMS-version 1.0. Det här kan bara utföras med RMS-aktiveringstjänsten och är avgörande vid användning av RMS-tekniken. I RMS version 1.0 med SP1 är det här processen där ett datorcertifikat hämtas för datoranvändaren och där det inte krävs någon anslutning till RMS-aktiveringstjänsten. Kallas även för aktivering.

<!-- -->

**RMS-certifieringstjänst**  
En Microsoft-baserad webbtjänst som utfärdar rättighetskontocertifikat till användare baserat på användarnas Microsoft .NET Passport-inloggningsuppgifter.

<!-- -->

**RMS-klient**  
En uppsättning RMS-API:er som måste installeras på alla klientdatorer i ett RMS-system. De krävs för datoraktivering och för användning av RMS-aktiverade program.

<!-- -->

**RMS-datorcertifikat**  
Det certifikat som placeras på en slutanvändares dator vid RMS-aktivering. Den offentliga nyckeln i det här certifikatet används till att kryptera användarens privata nyckel som finns i användarens rättighetskontocertifikat.

<!-- -->

**RMS-aktiverat program**  
Ett program som har utökats med ett SDK för Rights Management Services, så att användare kan ange vilka rättigheter som ska gälla för det innehåll de skapar.

<!-- -->

**RMS-aktiverad dator**  
En dator med en installerad RMS-klientkomponent som har genomgått RMS-datoraktivering så att den kan användas till att bearbeta innehåll som skyddas med RMS-teknik.

<!-- -->

**RMS-skyddat innehåll**  
Digital information som skyddas med RMS-teknik.

<!-- -->

**rotcertifikatkluster**  
En eller flera servrar i en RMS-distribution som hanterar administrerings-, registrerings-, kontocertifierings-, aktiveringsproxy-, licensierings- och publiceringstjänster. För servrarna används en gemensam databas och anslutnings-URL och de ska distribueras bakom en program- eller maskinvarubaserad belastningsutjämnare. Det kan bara finnas ett rotcertifikatkluster i varje Active Directory-skog.

<!-- -->

**rotcertifikatserver**  
Den primära servern i en RMS-distribution som hanterar administrerings-, registrerings-, kontocertifierings-, aktiveringsproxy-, licensierings- och publiceringstjänster. Det kan bara finnas en rotcertifikatserver i varje Active Directory-skog.

<!-- -->

**förtroenderot**  
En betrodd enhet som utgör grunden för att upprätta förtroende för andra certifikat. Alla certifikatutfärdare och slutanvändaren måste lita på roten.

<!-- -->

**säkerhets-ID (SID)**  
En datastruktur i Windows som identifierar alla Windows-användare, grupper och datorkonton. Varje konto i ett nätverk tilldelas ett unikt SID när kontot skapas. Interna processer i Windows hänvisar till kontots SID istället för dess användar- eller gruppnamn.

<!-- -->

**serverlicensieringscertifikat**  
Ett certifikat som upprättar RMS-serverns referenser, vilket får servern att fungera och gör att den kan tillhandahålla giltiga certifierings- och licensieringstjänster. Licensieringscertifikatet innehåller den offentliga nyckel som används till att kryptera innehållsnycklar i publiceringslicenser.

<!-- -->

**servertjänst**  
En RMS-webbtjänst som är avsedd att användas med en annan tjänst.

<!-- -->

**anslutningspunkt för tjänst**  
Ett Active Directory-objekt som hänvisar till sökvägen till rotcertifikatklustret i en RMS-distribution. Den här informationen används i RMS-klienten till att hitta RMS-tjänsterna.

<!-- -->

**underregistrering**  
En del av etableringsprocessen av en licensieringsserver där licensieringsservern erhåller ett serverlicensieringscertifikat från rotcertifikatklustret.

<!-- -->

**underregistrering, begäran**  
En begäran om ett serverlicensieringscertifikat som skickas från en licensieringsserver till rotcertifikatklustret.

<!-- -->

**underregistrering, tjänst**  
En RMS-webbtjänst på rotcertifikatservern som svarar på begäran om serverlicensieringscertifikat som skickas från licensieringsservrar under etableringsprocessen.

<!-- -->

**RM-ansvarig**  
En medlem av gruppen RM-ansvariga.

<!-- -->

**RM-ansvariga, grupp**  
En valfri, administrativt definierad användargrupp i varje RMS-kluster. Medlemmarna i gruppen beviljas ägarlicenser av RMS-servern när de öppnar innehåll som har publicerats med servern.

<!-- -->

**användarlicens**  
Den licens som visar rättigheter och villkor för hur en slutanvändare får använda skyddat innehåll. Kallas även slutanvändarlicens.
