---
TOCTitle: Definiera principer för återkallning
Title: Definiera principer för återkallning
ms:assetid: 'e2fffe9f-def7-439b-a8aa-43f8a065813d'
ms:contentKeyID: 18124930
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747782(v=WS.10)'
---

Definiera principer för återkallning
====================================

Att definiera organisationens principer för återkallning kräver noggranna överväganden och noggrann planering eftersom det kan påverka användarnas möjligheter att använda innehåll, samtidigt som återkallning höjer säkerheten för skyddat innehåll. Du definierar principer för återkallning för en RMS-distribution från administrationswebbplatsen.

Återkallning från tredje part
-----------------------------

Eftersom Microsofts registreringstjänst har utfärdat serverlicensieringscertifikatet för rotcertifikatservern i en RMS-distribution kan Microsoft återkalla serverlicensieringscertifikatet. Men Microsoft återkallar bara ett serverlicensieringscertifikat när man åläggs av en behörig myndighet att göra detta.

Du kan ange en tredje part som kan återkalla serverlicensieringscertifikatet för en RMS-server, utöver Microsofts registreringstjänst. Denna tredje part kan antingen vara en utomstående enhet eller ett offentligt eller privat nyckelpar som administratören genererar för organisationens räkning. Den privata nyckeln hos den tredje part som anges kan signera en lista över återkallade certifikat som används till att återkalla serverlicensieringscertifikatet. Denna tredje part definieras med partens offentliga nyckel under etableringen av RMS. Principmallarna för rättigheter på servern kan också konfigureras så att de tillåter att en tredje part återkallar innehåll, programmanifest, licenser och certifikat som har utfärdats av RMS-installationen. Mer information finns i ”[Skapa och ändra principmallar för rättigheter](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)” senare i det här avsnittet.

| ![](images/Cc747782.Important(WS.10).gif)Viktigt!                                                                                        |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du bestämmer dig för att generera ett eget nyckelpar för återkallning av rotcertifikatserverns serverlicensieringscertifikat måste det förvaras på en säker plats. |

Att besluta sig för att återkalla ett serverlicensieringscertifikat är ett stort beslut, eftersom alla certifikat och licenser som utfärdats med RMS-installationen blir ogiltiga när certifikatet återkallas. Mer information om hur du återkallar serverlicensieringscertifikat finns i ”[Återkalla serverlicensieringscertifikat](https://technet.microsoft.com/8020861d-d196-4431-8282-044675ef5616)” senare i det här avsnittet.

Betänka hur listor över återkallade certifikat fungerar
-------------------------------------------------------

När återkallning krävs för visst skyddat innehåll används alla listor över återkallade certifikat som är registrerade på klientdatorer och de gäller om ett angivet villkor uppfylls. Var därför försiktig när du genomför återkallning eftersom det leder till att listor över återkallade certifikat registreras på klientdatorer. De här listorna kan tillämpas på ett annat sätt än vad som avsågs. Mer information om hur du konfigurerar det här alternativet finns i ”[Skapa och ändra principmallar för rättigheter](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)” senare i det här avsnittet.

Balansera säkerhet och användarvänlighet
----------------------------------------

När du anger en princip för återkallning i en principmall för rättigheter bör du väga behovet av hög säkerhet för dokument mot risken att användare får problem när de använder innehållet, vilket beskrivs i följande exempel.

Som en del i konfigurationen av en lista över återkallade certifikat i en principmall för rättigheter anger du också uppdateringsintervall för listan över återkallade certifikat. En lista över återkallade certifikat måste finnas på användarnas datorer för att de ska kunna använda innehåll som har publicerats med den aktuella principmallen för rättigheter, och listan får inte vara äldre än vad som anges av uppdateringsintervallet. Om uppdateringsintervallet t.ex. är 10 måste listan över återkallade certifikat ha skapats någon gång under de senaste tio dagarna. Om det inte finns någon lista över återkallade certifikat på klientdatorn eller om listans datum är äldre än vad som anges i uppdateringsintervallet, hämtas den senaste listan över återkallade certifikat från den plats som du har angett i användarlicensen. Men användare som inte är anslutna till nätverket kan då eventuellt inte hämta den aktuella listan över återkallade certifikat, och kommer därför inte att kunna använda innehållet.

Följande metoder kan hjälpa dig att undvika det här problemet:

-   Var försiktig när du anger uppdateringsintervallet för en lista över återkallade certifikat och se till att det alltid finns en uppdaterad lista som användarna kan komma åt.
-   Spara listor över återkallade certifikat på platser som går att komma åt både inifrån företagets nätverk och via Internet.
-   Använd Microsoft® Systems Management Server (SMS) eller ett liknande program till att distribuera uppdaterade kopior av listor över återkallade certifikat till alla klientdatorer med jämna mellanrum, t.ex. varje natt.
-   Använd bara återkallning för de allra känsligaste dokumenttyperna.
