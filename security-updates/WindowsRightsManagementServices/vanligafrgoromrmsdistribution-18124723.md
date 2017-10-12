---
TOCTitle: 'Vanliga frågor om RMS: Distribution'
Title: 'Vanliga frågor om RMS: Distribution'
ms:assetid: '5559ae65-77ae-4e0b-bfd8-3512409ed29b'
ms:contentKeyID: 18124723
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720274(v=WS.10)'
---

Vanliga frågor om RMS: Distribution
===================================

Vanliga frågor om RMS-distribution
----------------------------------

-   [Finns det något krav på Exchange-version om de säkerhetsenheter som används i RMS är medlemmar i en global adresslista?](#bkmk_20)
-   [Vilken roll har SQL Server i RMS?](#bkmk_21)
-   [Måste användarens dator anslutas till samma domän som RMS-rotklustret för att RMS ska kunna användas?](#bkmk_22)
-   [Vilka portar måste vara öppna i Internet-brandväggen och intranätbrandväggen för kommunikation med RMS om en användare vill placera RMS-servern i ett perimeternätverk?](#bkmk_23)
-   [Hur registreras underordnade servrar i ett licenskluster och måste jag göra något med klienterna för att de ska känna av klustret?](#bkmk_24)
-   [Vilka är fördelarna med licenskluster?](#bkmk_25)
-   [Hur gör jag för att återställa en RMS-installation fullständigt?](#bkmk_26)
-   [Måste jag ta bort några andra filer när jag har avinstallerat RMS-klienten genom att använda Lägg till eller ta bort program?](#bkmk_27)
-   [Fungerar RMS med filsystemet FAT?](#bkmk_28)
-   [Vilken maskinvarukonfiguration rekommenderas vanligen för databasservern som används i RMS?](#bkmk_29)
-   [Hur påverkas prestanda för den globala katalogservern av att en global katalog används för gruppexpansion i RMS?](#bkmk_30)
-   [Krävs det några schemaändringar i Active Directory för RMS?](#bkmk_31)
-   [Replikeras anslutningspunkten för tjänst automatiskt mellan de olika domänkontrollanterna i domänen där RMS-klustret är installerat?](#bkmk_32)
-   [Hur kan RMS-klienten installeras och konfigureras om användare inte har administratörsrättigheter på sina datorer?](#bkmk_33)
-   [Hur kan RMS storleksanpassas?](#bkmk_35)
-   [Går det att använda HSM (Hardware Security Module) till att säkra RMS-nycklarna i maskinvaran?](#bkmk_36)

<span id="BKMK_20"></span>
#### Finns det något krav på Exchange-version om de säkerhetsenheter som används i RMS är medlemmar i en global adresslista?

RMS är beroende av Active Directory men inte av Exchange. I Exchange 5.5 finns en egen katalog och Active Directory används inte. Kontrollera att alla användar- och gruppobjekt i Active Directory har giltiga e-postattribut som innehåller ett fullständigt kvalificerat domännamn. Det här sker automatiskt om du använder Exchange 2000 eller senare.

<span id="BKMK_21"></span>
#### Vilken roll har SQL Server i RMS?

I RMS används en databas till att lagra alla tjänstkonfigurationsdata, information om enheter i systemet, alla loggningsdata och till att cachelagra sökningar vid expansion av Active Directory och distributionslistor. RMS har testats fullständigt med SQL Server 2000 och SQL Server 2005.

<span id="BKMK_22"></span>
#### Måste användarens dator anslutas till samma domän som RMS-servern för att RMS ska kunna användas?

Användarens dator behöver inte vara medlem i samma domän som RMS-klustret men den måste kunna hitta RMS-klustret. Det enklaste sättet att se till att klientdatorer hittar RMS-klustret är att använda en Active Directory-sökning via anslutningspunkten för tjänst. Registerinställningarna för klienten kan dock även konfigureras så att RMS-klustret hittas utan Active Directory-sökning. De exakta registerinställningarna är olika i olika RMS-aktiverade program.

<span id="BKMK_23"></span>
#### Vilka portar måste vara öppna i Internet-brandväggen och intranätbrandväggen för kommunikation med RMS om en användare vill placera RMS-servern i ett perimeternätverk?

De interna användarna måste ha åtkomst till RMS-servrarna som utfärdar rättighetskontocertifikat (RAC) och användarlicenser. RMS-servern lyssnar som standard på HTTP (TCP-port 80) eller HTTPS (TCP-port 443), beroende på om servern är konfigurerad för användning av SSL, så de portarna måste vara öppna i Internet-brandväggen. Du måste öppna ytterligare portar som används av medlemsservrar i en domän i intranätbrandväggen.

<span id="BKMK_24"></span>
#### Hur registreras underordnade servrar i ett licenskluster och måste jag göra något med klienterna för att de ska känna av klustret?

När den första RMS-servern skapas i ett företags rotkluster förses den med ett serverlicensieringscertifikat från Microsofts registreringstjänst. När nästa RMS-server installeras och etableras kan du ansluta den till rotklustret eller registrera den som server i ett underordnat licenskluster. Om du väljer att registrera den som en server i ett underordnat licenskluster skickas en registreringsbegäran till RMS-rotklustret. I RMS-aktiverade program anges var ett klientprogram ska söka efter licensklustret. Office 2003 är ett exempel på ett RMS-aktiverat program där rotklustret söks upp som standard. Den här funktionen kan åsidosättas med hjälp av registerinställningar så att programmet i stället gör en sökning efter det nya underordnade licensklustret.

<span id="BKMK_25"></span>
#### Vilka är fördelarna med underordnade licenskluster?

En fördel är att du kan isolera olika avdelningar inom en organisation. Om det inte upprättas någon betrodd publiceringsdomän mellan RMS-kluster kan innehåll endast användas av användare som har åtkomst till en viss licensieringsserver. På så sätt kan en juridisk avdelning se till att ingen annan kan läsa deras RMS-krypterade e-post. Dessutom kan flera alternativ anges i licensklustret, t.ex. rättighetsmallar, loggning, medlemskap i gruppen RM-ansvariga och exkluderingsprinciper.

<span id="BKMK_26"></span>
#### Hur gör jag för att återställa en RMS-installation fullständigt?

Om du vill återställa en RMS-installation fullständigt gör du följande:

**Så här återställer du en RMS-installation**
1.  Ta bort anslutningspunkten för tjänst för RMS-klustret genom att använda webbplatsen Administration av RMS.

2.  På sidan **Global Administration** klickar du på **Ta bort RMS från den här webbplatsen** så tas RMS bort från servern. Du bör först ta bort alla underregistrerade servrar i licensklustren och sedan ta bort rotklusterservrarna.

3.  I **Kontrollpanelen** klickar du på **Lägg till eller ta bort program** och tar bort **Rights Management Services**.

4.  Ta bort alla RMS-databaser på databasservern.

5.  Ta bort RMS-tjänstkontot från listan över godkända inloggningar på databasservrarna och ta sedan bort kontot från Active Directory.

6.  Om RMS-klienterna körs med Windows XP och Windows 2000 tar du bort RMS-klienten från klientdatorerna.

| ![](images/Cc720274.Important(WS.10).gif)Viktigt!                                                                                                            |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| När du har gjort det kan du inte längre öppna rättighetsskyddat innehåll. Du bör inaktivera RMS innan du återställer en RMS-installation om RMS användes till att skydda värdefulla data. |

<span id="BKMK_27"></span>
#### Måste jag ta bort några andra filer när jag har avinstallerat RMS-klienten genom att använda Lägg till eller ta bort program?

Du kan ta bort lockboxen från %systemroot%\\system32, trots att det egentligen inte är nödvändigt.

<span id="BKMK_28"></span>
#### Fungerar RMS med filsystemet FAT?

Ja, RMS fungerar på datorer där FAT används. Filsystemet NTFS rekommenderas dock.

<span id="BKMK_29"></span>
#### Vilken maskinvarukonfiguration rekommenderas vanligen för databasservern som används i RMS?

Loggningsdatabasen växer snabbt, särskilt i miljöer där RMS används i stor utsträckning. Om du planerar att använda SQL Server som databasserver bör du överväga att använda SQL Server 2000 Enterprise Edition eller SQL Server 2005 Enterprise Edition i Windows 2000 Advanced Server eller Windows Server 2003, Enterprise Edition, som konfigurerats i ett kluster i aktiv/standbykonfiguration. I så fall är de rekommenderade konfigurationerna RAID-1-loggdiskar och RAID-5-datadiskar och minst 512 MB RAM-minne. Den minsta rekommenderade processorn för den här konfigurationen är en Pentium III på 1,4 GHz. På särskilda databasservrar behövs inte flera processorer.

<span id="BKMK_30"></span>
#### Hur påverkas prestanda för den globala katalogservern av att en global katalog används för gruppexpansion i RMS?

På RMS-servern cachelagras eventuella gruppexpansionslistor så att inte den globala katalogservern ska belastas. Regelbundna uppdateringar av gruppmedlemskap ökar beroendet av den globala katalogservern. Tidsgränsen för att skaffa nya grupplistor kan dock konfigureras genom registret. Regelbundna uppdateringar av stora grupper försämrar prestanda. Mer information finns i avsnittet ”Ändra cacheinställningar för Active Directory” i ”RMS: Åtgärder" i den här dokumentationssamlingen.

<span id="BKMK_31"></span>
#### Krävs det några schemaändringar i Active Directory för RMS?

För att RMS ska kunna expandera det gruppmedlemskap som har angivits i publiceringslicensen mellan skogar måste det finnas ett kontaktobjekt i den lokala Active Directory-skogen som representerar den aktuella gruppen i den andra skogen. RMS kan efterfråga attributen för kontaktobjektet och upptäcka att det här objektet representerar en grupp som finns i en annan skog.

Om RMS ska kunna göra det krävs att Exchange Server 2003-schemaattributet msExchOriginatingForest (eller senare) för Active Directory används. Attributet installeras som standard i Active Directory-schemat när det finns en server i skogen där Exchange Server 2003 körs. Det här attributet måste finnas i skogen för varje Active Directory-schema som deltar i RMS. Om du inte använder Exchange Server 2003 kan du installera schemat separat i Active Directory-strukturen med hjälp av RMS Administration Toolkit.

<span id="BKMK_32"></span>
#### Replikeras anslutningspunkten för tjänst automatiskt mellan de olika domänkontrollanterna i domänen där RMS-servern är installerad?

När du har etablerat den första RMS-servern i en skog måste den registreras i Active Directory med hjälp av ett domänkonto som har tillräckliga behörigheter för att skapa ett behållarobjekt under tjänstbehållaren i konfigurationsbehållaren i Active Directory. Den inbyggda säkerhetsgruppen Företagsadministratörer är ett exempel på ett konto med de nödvändiga behörigheterna. På så sätt skapas anslutningspunkten för tjänst. Eftersom det här är i tjänstbehållaren replikeras informationen till alla domänkontrollanter i skogen.

<span id="BKMK_33"></span>
#### Hur kan RMS-klienten installeras och konfigureras om användare inte har administratörsrättigheter på sina datorer?

RMS-klienten är en Windows Installer-fil som kan distribueras genom att använda en infrastruktur för programvarudistribution, t.ex. Systems Management Server 2003. Du kan även distribuera RMS-klienten med hjälp av ett grupprincipobjekt (GPO) där ett tjänstkonto med administratörsrättigheter används. Om RMS-klienten körs med Windows Vista krävs ingen separat installation av RMS-klienten, eftersom den är inbyggd i operativsystemet.

<span id="BKMK_35"></span>
#### Hur kan RMS storleksanpassas?

RMS är en webbtjänst utan status som kan placeras i kluster och belastningsutjämnas precis som andra webbplatser eller -tjänster. Prestanda i RMS beror oftast på de tillgängliga processorerna, så de kan förbättras om du lägger till fler processorer.

<span id="BKMK_36"></span>
#### Går det att använda HSM (Hardware Security Module) till att säkra RMS-nycklarna i maskinvaran?

Ja, RMS fungerar med CAPI-kompatibla HSM:er som nCipher HSM.
