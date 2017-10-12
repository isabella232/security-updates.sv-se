---
TOCTitle: 'Skydda RMS-distributionen'
Title: 'Skydda RMS-distributionen'
ms:assetid: '6de8b636-a824-4844-aefc-f26347abfc14'
ms:contentKeyID: 18124760
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720291(v=WS.10)'
---

Skydda RMS-distributionen
=========================

RMS-distribution är en tillgång för alla organisationer som kräver samma fysiska säkerhetsåtgärder och nätverkssäkerhet som andra viktiga servrar i infrastrukturen. Du bör som ett led i distributionen identifiera de hot och skyddsåtgärder som gäller för RMS-servern.

RMS implementeras som en webbtjänst. Det betyder att du kontrollerar åtkomsten till RMS på samma sätt som med andra webbtjänster genom att använda åtkomstlistor (ACL) och SSL.

**Begränsa åtkomsten till RMS webbtjänster med ACL**

Du kan begränsa åtkomsten till RMS-tjänsterna med hjälp av åtkomstlistor. Varje virtuell rotkatalog som skapas när RMS etableras på en webbplats har en motsvarande mappstruktur som kan skyddas. Mappstrukturen finns på &lt;systemenhet&gt;:\\*&lt;webbrotmapp*&gt;\\\_wmcs, där *webbrotmapp* är namnet på den mapp som är kopplad till den webbplats där du har etablerat RMS. Vissa webbtjänster, t.ex. underregistreringstjänsten, certifieringstjänsterna för mobila enheter och servertjänster, har begränsningar som standard. De användargrupper som du vill ska kunna använda tjänsten måste aktivt läggas till i åtkomstlistan.

I certifieringstjänsten för servertjänster skapas rättighetskontocertifikat (RAC) som kan användas för åtkomst till RMS-skyddade tjänster, t.ex. tjänster för webbsamarbete, e-postservrar och dokumenthanteringsservrar som utökar RMS-systemet, t.ex:

-   En dokumentsamarbetsserver som användare kan överföra oskyddade dokument till. Däremot används RMS-skydd automatiskt för hämtade filer i enlighet med rättighetsprinciperna för innehållstypen. Ett exempel på det är Microsoft Office SharePoint Server 2007.
-   Ett dokumenthanteringssystem som fungerar som generell databas och dokumentarkiv för både skyddade och oskyddade dokument. RMS-skyddade dokument kan indexeras för sökning i systemet samtidigt som den rättighetsprincip som definierats av innehållsskaparen bevaras.
-   Konfigurera e-postservern för att snabbt öppna skyddat innehåll och utföra virus- och skräppostkontroller, eller utföra kontroller i enlighet med juridiska krav eller företagets e-postpolicy.

Eftersom de här scenarierna kräver licenser för användarna bör du kräva att funktionen för att hämta rättighetskontocertifikat (RAC) ska begränsas till de servrar i organisationen som har godkänts för funktionen och är skyddade på lämpligt sätt.

**Begränsa åtkomsten till RMS-webbtjänster med SSL**

Vi rekommenderar att du aktiverar SSL och använder 128-bitarskryptering för varje RMS-webbtjänstfil. De filerna har filnamnstillägget .asmx och finns i de virtuella katalogerna Licensiering, Certifiering och Admin. För SSL krävs att servern har ett giltigt SSL-certifikat installerat för webbplatsen. Om du tillämpar SSL på \_wmcs-mappen i RMS-installationen tillämpas inställningen även på undermapparna och -filerna. Mer information om webbtjänstfilerna och virtuella kataloger finns i "Internet Information Services" i avsnittet "RMS: Tekniska referenser" i den här dokumentationssamlingen.

| ![](images/Cc720291.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                 |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du vill öppna administrationswebbsidorna för Windows RMS från en webbläsare på en fjärrdator måste du aktivera SSL. Men även om du aktiverar SSL går det inte att öppna sidan **Global administration** från en fjärrdator. Mer information om fjärradministration av RMS finns i "Använda administrationshemsidan" i avsnittet "RMS: Åtgärder" i den här dokumentationssamlingen. |

**Ange en stark privat lösenordsnyckel**

Det privata nyckellösenordet används till att skapa och på ett säkert sätt lagra den privata nyckeln i RMS-konfigurationsdatabasen. Ett starkt lösenord rekommenderas för att garantera maximal säkerhet. Om lösenordet måste antecknas ska det förvaras på en fysiskt skyddad plats.

| ![](images/Cc720291.Caution(WS.10).gif)Varning!                                                                                                                                   |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om det privata nyckellösenordet tappas eller glöms bort och RMS plötsligt ställs i offlineläge måste du dekryptera alla RMS-dokument, återskapa RMS-miljön och kryptera allt igen med den nya privata nyckeln. |
