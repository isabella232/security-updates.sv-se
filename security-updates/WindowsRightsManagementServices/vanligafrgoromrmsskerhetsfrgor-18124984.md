---
TOCTitle: 'Vanliga frågor om RMS: Säkerhetsfrågor'
Title: 'Vanliga frågor om RMS: Säkerhetsfrågor'
ms:assetid: 'ff433834-79aa-481f-bd39-3393be12a26f'
ms:contentKeyID: 18124984
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747757(v=WS.10)'
---

Vanliga frågor om RMS: Säkerhetsfrågor
======================================

Vanliga frågor om säkerhet i RMS
--------------------------------

-   [Vad är kontot för RM-ansvariga?](#bkmk_43)
-   [Är RMS en säkerhetslösning?](#bkmk_44)
-   [Vilka mekanismer används för att förhindra att mottagare ställer tillbaka klockorna på sina klientdatorer för att förlänga åtkomsttiden till ett rättighetsskyddat dokument när deras användarlicenser har upphört att gälla?](#bkmk_45)
-   [Kan medlemmar i gruppen Domänadministratörer läsa dokument som är avsedda för någon i domänen?](#bkmk_46)
-   [Jag har förstått att varje lockbox kan autentisera alla certifikat och licenser som genereras i systemet, som en tjänst som är registrerad hos Microsoft. Vilken typ av hot skyddar det här mot?](#bkmk_47)
-   [Kan en person som lyckats öppna ett dokument genom att knäcka lösenordet öppna andra dokument med den nyckeln?](#bkmk_48)
-   [Är några delar av nycklarna tillgängliga utanför företaget som distribuerade dem, i enlighet med begränsningar för krypteringstekniker?](#bkmk_49)
-   [Hur förhindrar man att hackare med skadligt uppsåt aktiverar inaktiveringsfunktionen från en fjärrdator?](#bkmk_50)
-   [Kan en användare ta skärmbilder av rättighetsskyddat innehåll?](#bkmk_51)
-   [Kan administratörer som säkerhetskopierar filer som är relaterade till RMS få åtkomst till rättighetsskyddat innehåll?](#bkmk_52)
-   [Innehåller växlingsfilen som används i Windows det okrypterade innehållet vid något tillfälle, så att innehållet är ”öppet”?](#bkmk_53)
-   [Går det att begränsa vilka administratörer som har åtkomst till de olika administrativa funktionerna i RMS?](#bkmk_54)
-   [Kan enskilda dokument skyddas i RMS så fort de har skapats, antingen på användarens hårddisk eller i en delad mapp?](#bkmk_55)
-   [Är autospar-filen och de temporära filerna krypterade när jag öppnar en fil?](#bkmk_56)
-   [När jag får ett rättighetsskyddat e-postmeddelande finns det en bifogad fil i meddelandet. Jag kan spara den bifogade filen trots att meddelandet inte ska kunna sparas. Fungerar inte RMS?](#bkmk_562)

<span id="BKMK_43"></span>
#### Vad är kontot för RM-ansvariga?

I RMS finns en särskild grupp med RM-ansvariga som har fullständig kontroll över allt rättighetsskyddat innehåll. Medlemmar i gruppen RM-ansvariga tilldelas fullständiga ägarrättigheter i alla användarlicenser som utfärdas till dem med det RMS-kluster där gruppen RM-ansvariga finns. Det innebär att medlemmar i den här gruppen kan dekryptera alla skyddade filer och att de även kan ta bort skyddet från de filerna. Medlemmar av den här gruppen kan t.ex. ta bort skyddet från filer som har publicerats av en anställd som har slutat, så att en ny ägare kan publicera och hantera dessa filer.

<span id="BKMK_44"></span>
#### Är RMS en säkerhetslösning?

Nej, RMS är inte en säkerhetslösning. När det används med ett RMS-aktiverat program, t.ex. Office 2007, kan det betraktas som en ”lösning för att tillämpa principer”. Om användaren inte har behörighet att visa data kan han/hon försöka knäcka krypteringen genom en s.k. brute force-attack. Krypteringen kan knäckas trots att den, liksom alla programvarubaserade krypteringsscheman, är robust. Om användaren har behörighet att visa data kan han/hon kopiera den för hand eller ta en digital bild av den och ge informationen till obehöriga användare.

<span id="BKMK_45"></span>
#### Vilka mekanismer används för att förhindra att mottagare ställer tillbaka klockorna på sina klientdatorer för att förlänga åtkomsttiden till ett rättighetsskyddat dokument när deras användarlicenser har upphört att gälla?

Om klockan på en klientdator har ställts bakåt eller framåt upptäcks det i RMS, och användaren hindras från att använda innehåll. Dessutom upptäcks om det finns en mätbar tidsskillnad mellan RMS-servern och klienten.

<span id="BKMK_46"></span>
#### Kan medlemmar i gruppen Domänadministratörer läsa dokument som är avsedda för någon i domänen?

Medlemmar i gruppen Domänadministratörer kan läsa innehåll som är tillgängligt för ett användarkonto om de är medlemmar i gruppen RM-ansvariga för RMS eller om de använder användarens konto. Eftersom medlemmar i gruppen Domänadministratörer har kontroll över användarkontona i domänen finns det inget sätt att mildra effekterna av ett scenario med en opålitlig medlem i gruppen Domänadministratörer.

Du bör endast lägga till medlemmar i gruppen Domänadministratörer till gruppen RM-ansvariga när de behöver få åtkomst till rättighetsskyddat innehåll. När en licens beviljas till en medlem i gruppen RM-ansvariga loggas händelse-ID 49 i RMS-serverns programhändelselogg. Händelse-ID 49 anger **”En licens har beviljats till en användare som tillhör gruppen RM-ansvariga. Användaren har följande e-postadress: &lt;Användarens alias&gt;”**, där **Användarens alias** byts ut mot användarens e-postkonto.

Precis som med andra grupper som används till att begränsa åtkomst till resurser bör du definiera varningar och utföra säkerhetskontroller för att förhindra att någon blir medlem i gruppen RM-ansvariga utan behörighet.

<span id="BKMK_47"></span>
#### Jag har förstått att varje lockbox kan autentisera alla certifikat och licenser som genereras i systemet, som en tjänst som är registrerad hos Microsoft. Vilken typ av hot skyddar det här mot?

Om det inte gick att kontrollera integriteten för certifikat skulle en användare kunna förfalska ett rättighetskontocertifikat som utfärdats till en annan användare och få en användarlicens för innehåll, eller skapa ett program som tar bort skyddet från ett dokument.

<span id="BKMK_48"></span>
#### Kan en person som lyckats öppna ett dokument genom att knäcka lösenordet öppna andra dokument med den nyckeln?

Alla delar av det rättighetsskyddade innehållet är krypterade med olika slumpmässigt genererade symmetriska nycklar. Varje dokuments nyckel är därför unik och kan inte användas till att dekryptera andra dokument.

<span id="BKMK_49"></span>
#### Är några delar av nycklarna tillgängliga utanför företaget som distribuerade dem, i enlighet med begränsningar för krypteringstekniker?

Program som är signerade i Microsoft-roten är underställda Microsoft-roten för nyckelsignering, men efter det visas inga andra nycklar varken av Microsoft eller av en kunds distribution.

<span id="BKMK_50"></span>
#### Hur förhindrar man att hackare med skadligt uppsåt aktiverar inaktiveringsfunktionen från en fjärrdator?

Hackaren måste ha inloggningsuppgifterna för ett användarkonto som har administratörsrättigheter för RMS-klustret. Administrationsgränssnittet i RMS är som standard endast tillgängligt lokalt på RMS-servern. Du kan minska risken genom att försäkra dig om det föregående, se till att RDP (Remote Desktop Protocol) är avaktiverat och att servern är placerad på en säker plats.

<span id="BKMK_51"></span>
#### Kan en användare ta skärmbilder av rättighetsskyddat innehåll?

Om RMS-rättigheterna är inställda på att inte tillåta kopieringsfunktioner avaktiveras Windows Alt+PrintScrn av RMS. I en miljö med ohanterade datorer kan dock en användare använda andra produkter än Microsofts till att kopiera innehåll.

<span id="BKMK_52"></span>
#### Kan administratörer som säkerhetskopierar filer som är relaterade till RMS få åtkomst till rättighetsskyddat innehåll?

Nej, de kan utföra säkerhetskopieringen men har inte åtkomst till innehållet.

<span id="BKMK_53"></span>
#### Innehåller växlingsfilen som används i Windows det okrypterade innehållet vid något tillfälle, så att innehållet är ”öppet”?

När RMS-klienten skickar dekrypterat innehåll tillbaka till programmet kan det visas i växlingsfilen. Bland rekommendationerna för RMS-programutveckling i SDK (Software Development Kit) för Rights Management Services (RMS) finns åtgärder för att förhindra detta, men det här ska ske i det RMS-aktiverade programmet.

<span id="BKMK_54"></span>
#### Går det att begränsa vilka administratörer som har åtkomst till de olika administrativa funktionerna i RMS?

Ja, du kan skapa olika RMS-administratörsgrupper i Active Directory, lägga till användare och sedan skapa en lämplig åtkomstkontrollista (ACL) för administrationssidorna. I standardkonfigurationen för åtkomstkontrollistorna på webbsidan för RMS-administration anges exempelvis att sidan Säkerhetsinställningar endast är tillgänglig för användaren som etablerade servern.

<span id="BKMK_55"></span>
#### Kan enskilda dokument skyddas i RMS så fort de har skapats, antingen på användarens hårddisk eller i en delad mapp?

Trots att RMS kan användas till att skydda dokument som lagrats på en användares lokala dator är krypterande filsystem (EFS) det bästa alternativet. I EFS skyddas dokument automatiskt medan det i RMS krävs manuell hantering (några musklickningar) för att skydda ett dokument.

<span id="BKMK_56"></span>
#### Är autospar-filen och de temporära filerna krypterade när jag öppnar en fil?

Ja, alla temporära filer krypteras.

<span id="BKMK_562"></span>
#### När jag får ett rättighetsskyddat e-postmeddelande finns det en bifogad fil i meddelandet. Jag kan spara den bifogade filen trots att meddelandet inte ska kunna sparas. Fungerar inte RMS?

Det är precis som det ska vara. Den bifogade filen är det krypterade meddelandet innan RMS-klienten har dekrypterat det. Det är fortfarande rättighetsskyddat och kan inte sparas när det har dekrypterats.
