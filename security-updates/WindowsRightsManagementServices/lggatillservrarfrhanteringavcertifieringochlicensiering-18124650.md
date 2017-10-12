---
TOCTitle: Lägga till servrar för hantering av certifiering och licensiering
Title: Lägga till servrar för hantering av certifiering och licensiering
ms:assetid: '089ceb62-2a96-444f-ab42-1d5deaabd0c3'
ms:contentKeyID: 18124650
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720189(v=WS.10)'
---

Lägga till servrar för hantering av certifiering och licensiering
=================================================================

När du har slutfört installationen, och etableringen av den första servern och rotinstallationen av RMS har slutförts, kan du installera ytterligare servrar och konfigurera utökade funktioner för certifierings- och licensieringstjänsterna. Du kan t.ex.:

-   Lägga till en server som en medlem i ett rotcertifikatkluster och utöka funktionerna för certifiering och licensiering. En server som läggs till i klustret använder samma konfiguration och samma databaser som rotcertifikatservern.
-   Du kan konfigurera en enskild licensieringsserver, eller konfigurera den som en medlem av ett licensieringsserverkluster. Den underregistreras i rotcertifikatklustret och får ett serverlicensieringscertifikat (SLC) via certifieringstjänsterna i rotcertifikatservern. Alla klientbegäran för certifieringstjänster som anländer till licensieringsservern vidarebefordras till certifikatservern. Från licensieringsservern kan användarlicenser och publiceringslicenser utfärdas utan att begäran vidarebefordras till rotcertifikatservern.

Vilket alternativ du väljer att distribuera beror på organisationens storlek och hur du vill implementera redundans, anpassningsmöjligheter, funktioner för belastningsutjämning och säkerhet. Om du distribuerar ytterligare RMS-servrar för att möta ett ökat certifierings-, licensierings- och publiceringsbehov distribuerar du RMS-servrarna som en del av rotcertifikatklustret, så att du kan konfigurera redundans och belastningsutjämning mellan alla servrar. Du kan placera certifikatservrar i kluster och minska belastningen för licenserings- och publiceringstjänster genom att underregistrera licenseringsservrar (som också kan placeras i kluster för belastningsutjämning). Du kan inte belastningsutjämna ett underregistrerat licensieringskluster med ett rotcertifikatkluster.

Du kan få mer information om det i följande avsnitt:

-   [Roller, behörigheter och rättigheter som krävs för installation och etablering](#bkmk_1)
-   [Etableringsprocesser för ytterligare certifikat- och licensieringsservrar](#bkmk_2)
-   [Konfigurera kluster och belastningsutjämning](#bkmk_3)

<span id="BKMK_1"></span>
Roller, behörigheter och rättigheter som krävs för installation och etablering
------------------------------------------------------------------------------

Om du vill installera och etablera ytterligare servrar måste du ha samma roller, behörigheter och rättigheter som gäller för konfigurationen av den första servern. Dessutom måste du även ha behörigheter från rotcertifikatservern att konfigurera en separat licensieringsserver, vilket kallas för underregistrering. Rotcertifikatservern kontrolleras via DACL-listan i filen SubEnrollService.asmx. Medlemmar i RMS-tjänstgruppen, inklusive det RMS-tjänstkonto som du anger vid etableringen av rotcertifikatservern, har behörighet att utföra underregistreringar. Mer information finns i ”[Konfigurera certifierings- och licensieringstjänsterna på den första servern](https://technet.microsoft.com/cce29a2f-984f-48ed-9187-0eb68286ec5b)” tidigare i avsnittet.

<span id="BKMK_2"></span>
Etableringsprocesser för ytterligare certifikat- och licensieringsservrar
-------------------------------------------------------------------------

När du lägger till servrar i certifikat- och licensieringskluster måste etableringsprocessen slutföras på servern. Etableringsprocessen kan variera beroende på vilken typ av server du etablerar.

-   Om du etablerar en separat licensieringsserver anger du en konfigurationsdatabas, ett RMS-tjänstkonto, en kluster-URL och den privata nyckel som används för att skydda information, på samma sätt som när du angav den informationen för en rotcertifikatserver. Du anger däremot inte någon princip för återkallning av serverlicensieringscertifikat, eftersom den principen kontrolleras av rotcertifikatservern.
-   Om du etablerar en server som en medlem av ett kluster är den enda information som du behöver ange under etableringen RMS-tjänstkonto, konfigurationsdatabas och lösenord för den privata nyckeln (du kan också använda samma CSP och privata nyckel som i det befintliga klustret). Alla servrar i ett kluster delar samma serverlicensieringscertifikat och servernyckelpar.

| ![](images/Cc720189.Important(WS.10).gif)Viktigt!                                                                      |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Påbörja inte installationen av RMS på några andra servrar förrän du har slutfört både installationen och etableringen av RMS på den första servern. |

När du har installerat och etablerat ytterligare en server konfigureras den automatiskt som en medlem av ett kluster. Men om du har implementerat belastningsutjämning måste du konfigurera programvaran för belastningsutjämning så att den fungerar med den nya servern.

<span id="BKMK_3"></span>
Konfigurera kluster och belastningsutjämning
--------------------------------------------

RMS är utformad för att hantera serverkluster. Genom att skapa kluster med RMS-servrar får du större anpassningsmöjlighet, bättre tillförlitlighet och bättre belastningsutjämning i RMS-distributionen.

**Skapa kluster**

Om du vill konfigurera ett kluster börjar du med en rotcertifikatserver eller en licensieringsserver. På efterföljande servrar i samma kluster installerar du RMS, går till sidan **Global administration** och klickar sedan på **Lägg till den här servern i ett kluster**, så etableras nödvändiga resurser och servern kopplas till rotcertifikatklustret eller licensieringsklustret.

Ange databasnamnet på det kluster som du vill ansluta till.

**Belastningsutjämningskluster**

Belastningsutjämning implementeras inte automatiskt i RMS. Du kan använda program- eller maskinvarubaserad belastningsutjämning, inklusive tjänsten Utjämning av nätverksbelastning, till att utjämna belastningen mellan alla RMS-servrar.

Följande avsnitt innehåller ytterligare information om det ämnet:

-   Mer information om skillnaderna mellan certifierings- och licensieringstjänster finns i ”Översikt över RMS-systemet” i ”Tekniska referenser för RMS”.
-   Mer information om hur du mappar serverdistributioner i förhållande till organisationens behov och prestandakrav finns i ”Tillhandahålla redundans och belastningsutjämning” i ”Planera en RMS-distribution”.
-   Mer information om hur du avgör hur många servrar som krävs för att hantera RMS-distributionen i organisationen finns i ”Utvärdera utrymmeskrav” i ”Planera en RMS-distribution”.
-   Mer information om hur du implementerar IT-säkerhet i RMS-distributionen finns i ”[Skydda RMS-distributionen](https://technet.microsoft.com/6de8b636-a824-4844-aefc-f26347abfc14)”.
-   Information om hur du installerar RMS finns i ”Så här installerar du RMS med Service Pack 1” i ”Använda en RMS-server”.
    Du kan också installera RMS från kommandotolken. Mer information finns i ”RMS-installation via Kommandotolken” i ”Använda en RMS-server”.
-   Mer information om hur du etablerar en licensieringsserver finns i ”Så här etablerar du en licensieringsserver” i ”Använda en RMS-server”.
-   Information om hur du etablerar fler servrar i ett kluster finns i ”Så här lägger du till en server i ett kluster” i ”Använda en RMS-server”.
