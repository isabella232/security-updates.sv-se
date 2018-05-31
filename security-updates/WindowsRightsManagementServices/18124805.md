---
TOCTitle: Förbereda systemåterställning
Title: Förbereda systemåterställning
ms:assetid: '885c047f-1e3b-4bf5-8248-3a4505759cbb'
ms:contentKeyID: 18124805
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747659(v=WS.10)'
---

Förbereda systemåterställning
=============================

Om någon komponent i RMS-systemet får problem (exempelvis Internet- eller intranätanslutningarna som används för RMS-servern, RMS-certifikatservern, någon av de underregistrerade RMS-licensieringsservrarna eller databasservrarna där RMS-konfigurationsdatabaserna ligger) kan det leda till oväntade avbrott i tjänsten. När du konfigurerar ett RMS-system är det viktigt att du överväger den effekt som ett avbrott i RMS-tjänsten skulle få för IT-systemen och känsliga data, samt förbereder en så snabb återställning av komponenten som möjligt.

Problem med de databasservrar som innehåller RMS-konfigurationsdatabaserna kan vara ett fel som gör att du inte kan komma åt RMS-skyddad information. I det här avsnittet beskrivs viktiga överväganden och faktorer för när du förbereder systemåterställning i ett RMS-system, exempelvis följande:

-   [Internetanslutningar](#bkmk_1)
-   [Intranätanslutningar](#bkmk_2)
-   [Certifierings- och licensieringstjänster](#bkmk_3)
-   [Databasservrar](#bkmk_4)
-   [Active Directory](#bkmk_5)

<span id="BKMK_1"></span>
Internetanslutningar
--------------------

Om du använder onlineregistrering av RMS-servern behöver du en Internetuppkoppling under etableringsprocessen för att kunna ta emot ett serverlicensieringscertifikat och för att kunna förnya serverlicensieringscertifikaten varje år. När ettårsdagen närmar sig meddelar certifikatservern dig att det är dags att förnya certifikatet, genom att logga händelser i systemets händelselogg. Händelserna loggas en månad innan serverlicensieringscertifikatet går ut (händelse-ID 16), en vecka innan serverlicensieringscertifikatet går ut (händelse-ID 17) och när serverlicensieringscertifikatet går ut (händelse-ID 18). Du får också meddelanden via RMS-webbsidan Global administration på webbplatsen Administration av RMS när serverlicensieringscertifikatet snart går ut. Om du använder RMS Management Pack för Microsoft Operations Manager (MOM) leder utgångsdatumshändelserna till en avisering. Om det inte finns någon Internetanslutning på RMS-servern kan du inte förnya serverlicensieringscertifikatet genom att trycka på knappen **Förnya** på webbplatsen Administration av RMS. Då måste du i stället använda offlineregistreringsprocessen till att begära ett uppdaterat certifikat.

Du bör förnya serverlicensieringscertifikatet i god tid före utgångsdatumet för att undvika problem som kan uppstå om t.ex. Internetuppkopplingen inte fungerar när certifikatet går ut. Inga RMS-tjänster kan tillhandahållas från RMS-servern utan ett giltigt serverlicensieringscertifikat. Det betyder att användarna inte kan publicera RMS-skyddad information eller få de användarlicenser och rättighetskontocertifikat som krävs för att läsa RMS-skyddad information. Användare som nyligen fått en användarlicens eller ett rättighetskontocertifikat för delar av RMS-skyddat innehåll har fortsatt tillgång till informationen tills deras användarlicenser eller rättighetskontocertifikat går ut.

<span id="BKMK_2"></span>
Intranätanslutningar
--------------------

RMS är en klient-server-teknik som bygger på en sammankopplad infrastruktur. RMS-servrarna kan inte ansluta till tjänster inom företaget eller tillhandahålla tjänster för användarna utan ett fungerande intranät. Utan intranätanslutning kan användarna inte få rättighetskontocertifikat, klientlicensieringscertifikat eller användarlicenser från RMS-servrarna.

Alla organisationer bör överväga att ha redundanta routningsarkitekturer och länkar till växlingar vid fel från fjärrplatser till RMS-serverplatser.

När en användare har tagit emot ett klientlicensieringscertifikat till sin dator kan användaren publicera RMS-skyddad information offline när det inte finns någon anslutning till RMS-servern. Vissa RMS-aktiverade e-postprogram har konfigurerats till att hämta användarlicenser för tillhörande RMS-skyddade e-postmeddelanden automatiskt när e-postlådan synkroniseras, så att användaren kan läsa RMS-skyddade e-postmeddelanden även om det inte finns någon intranätanslutning.

<span id="BKMK_3"></span>
Certifierings- och licensieringstjänster
----------------------------------------

RMS-systemet är beroende av två virtuella kataloger inom Internet Information Services (IIS) 6.0 - certifierings- och licensieringstjänsterna. Med hjälp av de tjänsterna kan användare och datorer registrera sig i RMS-miljön och RMS-aktiverade program och publicera och få tillgång till RMS-skyddad information. Om de här tjänsterna inte finns tillgängliga kan användarna nekas tillgång till dem tills de har återställts.

Som en förberedelse för avbrott i tjänsten kan du överväga att skapa certifikatserverklustret och det underregistrerade licensieringsserverklustret på ett sådant sätt att tillgängligheten i tjänsten inte påverkas om någon nod i klustret havererar.

Du bör också bygga in extra kapacitet i klustren så att fel på noder inte påverkar den samlade kapaciteten. När du installerar den första certifieringsservern och varje underregistrerad licensieringsserver, eller den första underregistrerade licensieringsservern i ett kluster, ska du noggrant anteckna de konfigurationsalternativ och uppgifter som du anger vid etableringen.

<span id="BKMK_4"></span>
Databasservrar
--------------

De viktigaste komponenterna i RMS-systemet är databasservrarna som innehåller konfigurationsdatabaserna. Varje RMS-server eller serverkluster använder databaser för att lagra konfigurerings- och loggningsinformation. Den konfigureringsinformationen är mycket viktig för driften av RMS. I databaserna finns serverlicensieringscertifikatet, de principmallar för RMS som har skapats och en lista över de användare som är registrerade i RMS-systemet. Om du inte använder någon HSM tillsammans med RMS-servern innehåller databasen också de privata och offentliga nycklarna till RMS-servern. Med säkerhetskopiorna av RMS-databaserna kan du återställa en tidigare RMS-installation på en ny server och återskapa ett RMS-system. Effekten av en databasförlust skiljer sig mellan olika databaser. I följande lista beskrivs effekten av olika databasproblem:

-   **Konfigurationsdatabas**. Om du förlorar åtkomsten till databasen vid användning av en RMS-server kan RMS-tjänsterna ändå fungera, eftersom viktig information sparas lokalt i cache-minnet i RMS. Men om en händelse inträffar som kräver interaktion mellan RMS-tjänsten och databasservern, t.ex. vid registrering av nya användare, blir det fel i RMS-tjänsten. De nya användarna kommer då inte att kunna arbeta med RMS-skyddat innehåll. Om något inträffar som gör att RMS-servern ignorerar informationen som sparats i cache-minnet, t.ex. en omstart av IIS-tjänsten eller en förinställd uppdatering av det lokala cache-minnet, kommer RMS-tjänsten att sluta fungera. RMS-servern kan inte återgå till normal drift innan konfigurationsdatabasen är tillgänglig igen.
    Om konfigurationsdatabasen blir skadad eller permanent otillgänglig slutar RMS-servrarna att fungera.
-   **Katalogtjänstdatabasen**. Här finns information om gruppnamn och medlemskap som hämtas från en global katalogserver och sparas i cache-minnet. Om tabellen inte är tillgänglig under korta tidsperioder leder det inte till någon märkbar försämring i RMS-tjänsterna. Databasens huvudsakliga uppgift är att tillhandahålla redundans och minskad tjänstbelastning för den globala katalogservern.
-   **Loggningsdatabasen**. Om loggning har aktiverats på RMS-servern är det i den här databasen loggen sparas. Om databasen inte är tillgänglig samlas loggposterna i Message Queuing-tjänsten (MSMQ) på RMS-servern. Då kommer allt ledigt diskutrymme att gå åt till loggposterna, om inte någon annan konfiguration används.

Du bör skapa ett kluster av databasservrarna för att få ett tillgängligt, aktivt skydd mot fel. Du bör också säkerhetskopiera databaserna för RMS-certifikatservrarna och -klustren regelbundet, liksom licensieringsservrarna och klustren.

Du kan också använda leverans av transaktionsloggar som en metod för att få en färdig säkerhetskopieringsdatabas. Även om den metoden kan kräva extra maskinvara gör den att organisationen kan återställa databaser snabbare. Microsoft IT har implementerat den här metoden för återställning av RMS-konfigurationsdatabasen. För att göra det väljer du det virtuella SQL-namnet under etableringen av RMS. Med det virtuella SQL-namnet kan du sedan mappa till det riktiga SQL-namnet med hjälp av DNS (Domain Name System). Om den ursprungliga SQL-servern slutar fungera kan du enkelt byta till den säkerhetskopierade SQL-servern genom att ändra DNS-namnmappningen från den ursprungliga servern till servern med säkerhetskopian. Mer information om den interna implementeringen av den här lösningen vid Microsoft finns i fallstudien från Microsoft Corporation på [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=42070) (http://go.microsoft.com/fwlink/?LinkId=42070).

<span id="BKMK_5"></span>
Active Directory
----------------

I RMS används Active Directory till två viktiga tjänster: autentisering av användare och den globala katalogtjänsten. Om Active Directory inte är tillgängligt kan inte autentiseringen av användare utföras. Det medför att varken användare eller datorer kan registrera sig i RMS-systemet. Certifieringspipelinen krävs för att kunna hämta ett rättighetskontocertifikat och för det krävs autentisering. När en användare har fått ett rättighetskontocertifikat kan den personen få användarlicenser utan vidare autentisering eftersom licensieringspipelinen har anonymitet som standard.

Eftersom enheter inom företag kan använda gruppmedlemskap i Active Directory till att ange vem som ska få tillgång till RMS-skyddad information innebär en förlust av Active Directory-tjänsten att inga användare kan få användarlicenser. Informationen om gruppmedlemskap sparas som standard i RMS-serverns cache-minne i 15 minuter. På så sätt tillåts tillfälliga avbrott i den globala katalogtjänsten. Du kan ändra den registernyckel som styr tidsvärdet om du vill öka eller minska tiden mellan uppdateringarna i cache-minnet. Mer information finns i ”Ändra cacheinställningar för Active Directory” i ”Använda en RMS-server”.
