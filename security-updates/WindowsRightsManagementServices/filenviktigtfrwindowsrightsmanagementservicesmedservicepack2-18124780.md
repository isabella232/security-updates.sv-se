---
TOCTitle: Filen Viktigt för Windows Rights Management Services med Service Pack 2
Title: Filen Viktigt för Windows Rights Management Services med Service Pack 2
ms:assetid: '78067886-681f-49a6-b43d-bfd08a369b69'
ms:contentKeyID: 18124780
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747637(v=WS.10)'
---

Filen Viktigt för Windows Rights Management Services med Service Pack 2
=======================================================================

*Utgivningsdatum: December 2006*

Innan du börjar
---------------

Läs följande information innan du installerar Microsoft® Windows® Rights Management Services (RMS) med Service Pack 2 (SP2). Den här informationen gäller RMS med SP2-servern och inte RMS-klienten. Information om RMS-klienter finns i Rights Management Services ([http://go.microsoft.com/fwlink/?LinkId=68637](http://go.microsoft.com/fwlink/?linkid=68637)).

#### Systemkrav

Maskinvarukraven för att köra RMS med SP2 anges i följande tabell.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Krav</th>
<th style="border:1px solid black;" >Rekommendation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Dator med en Pentium III-processor (800 MHz eller snabbare)</td>
<td style="border:1px solid black;">Dator med två Pentium 4-processorer (1500 MHz eller snabbare)</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">256 MB internminne</td>
<td style="border:1px solid black;">512 MB internminne</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">20 GB ledigt hårddiskutrymme</td>
<td style="border:1px solid black;">40 GB ledigt hårddiskutrymme</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc747637.note(WS.10).gif)Obs!                                                      |  
|----------------------------------------------------------------------------------------------------------------------------|  
| RMS med SP2-servern är avsett för 32-bitarsdator. Om programmet installeras i en 64-bitarsdator körs det i emuleringsläge. |
  
Programvarukraven för servrar där RMS med SP2 körs anges i följande tabell.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Komponent</th>
<th style="border:1px solid black;" >Krav</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Operativsystem</td>
<td style="border:1px solid black;">Microsoft Windows Server® 2003, utom Web Edition, för RMS med SP2.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rights Management Services med SP2</td>
<td style="border:1px solid black;">RMS med Service Pack 1 (SP1) måste vara installerat innan du kan uppgradera till RMS med SP2. RMS med SP2-klienten omfattas inte av det här kravet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Filsystem</td>
<td style="border:1px solid black;">Filsystemet NTFS rekommenderas.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Komponenter som krävs</td>
<td style="border:1px solid black;"><ul>
<li>Message Queuing (även kallat MSMQ) med aktiverad Active Directory-integration.<br />
<br />
</li>
<li>Internet Information Services (IIS) med ASP.NET aktiverat.<br />
<br />
</li>
<li>Microsoft .NET Framework 1.1<br />
<br />
</li>
</ul></td>
</tr>
</tbody>
</table>
 

| ![](images/Cc747637.note(WS.10).gif)Obs!                                                                                                         |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du konfigurerar RMS med SP2 för fjärrinstallation måste datorn som ansluts till administrationstjänsten för RMS med SP2 ha Internet Explorer 6.0 eller senare installerat. |

Kraven på infrastruktur för servrar där RMS med SP2 körs anges i följande tabell.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Komponent</th>
<th style="border:1px solid black;" >Krav</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Katalogtjänster</td>
<td style="border:1px solid black;">Active Directory som körs på domänkontrollanter som använder Windows Server 2000 med Service Pack 3 (SP3) eller senare, i samma domän som RMS är installerad i. Alla användare och grupper som hämtar licenser och publicerar innehåll med RMS måste ha en e-postadress som är konfigurerad i Active Directory.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Databasserver</td>
<td style="border:1px solid black;">För RMS med SP2 behövs en databas och lagrade procedurer för att åtgärder ska kunna utföras. Du kan använda Microsoft SQL Server™ 2000 med SP3a eller senare eller Microsoft SQL Server 2005. Vid testning eller annan distribution till enskilda datorer går det att använda Microsoft SQL Server Desktop Engine (MSDE 2000) Release A eller Microsoft SQL Server 2005 Express Edition.</td>
</tr>
</tbody>
</table>
  
RMS är utvecklat för och testat med databasservrar med Microsoft SQL Server 2000 och Microsoft SQL Server 2005. RMS kan köras i andra databasservrar om de uppfyller följande krav:
  
-   Funktioner för ADO.NET-gränssnitt som tillhandahålls av Microsoft .NET Framework 1.1.  
-   Kompatibilitet med Transact-SQL, det SQL-språk som används i Microsoft SQL Server, eftersom skript för RMS-initiering och lagrade procedurer i RMS baseras på Transact-SQL.  
-   Funktioner för alla Microsoft SQL Server-specifika tillägg.  
-   Svara på metodanrop från namnområdet System.Data.SqlClient i .NET Framework.  
-   Tillhandahålla motsvarande funktioner som namnområdet System.Data.SqlClient.  
-   Använda Windows-autentiseringsläget.
  
Om du vill ta reda på om databasservern uppfyller kraven ovan kontaktar du relevant databasleverantör.
  
I följande tabell visas de användarrättigheter och behörigheter som krävs när du utför olika aktiviteter med RMS.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Aktivitet</th>
<th style="border:1px solid black;" >Kontokrav</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Installera RMS</td>
<td style="border:1px solid black;">Domänanvändare med administratörsbehörighet på den lokala datorn</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Etablera ett RMS-rotkluster</td>
<td style="border:1px solid black;">Domänanvändare med administratörsbehörighet för den lokala datorn samt behörighet att söka och skriva i Active Directory</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Etablera ett RMS licenskluster</td>
<td style="border:1px solid black;">Domänanvändare med administratörsbehörighet för den lokala datorn samt behörighet att söka i Active Directory</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Etablering när en ny konfigurationsdatabas används</td>
<td style="border:1px solid black;">Domänanvändare med administratörsbehörighet för den lokala datorn samt behörighet att läsa, skriva och skapa i en dator som kör SQL Server</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Etablering när en befintlig konfigurationsdatabas används</td>
<td style="border:1px solid black;">Domänanvändare med administrationsbehörighet för den lokala datorn samt behörighet att läsa och skriva i datorn som kör databasservern</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Administrera RMS</td>
<td style="border:1px solid black;">Domänanvändare med administratörsbehörighet på den lokala datorn</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc747637.note(WS.10).gif)Obs!                                                                                                                                                                           |  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Mer information om konfiguration av Windows Server, Active Directory, Message Queuing, IIS och filsystem finns i Windows Server 2003 TechCenter ([http://go.microsoft.com/fwlink/?LinkId=78135](http://go.microsoft.com/fwlink/?linkid=78135)). |
  
Om du använder RMS i en klusterdistribution bör du kontrollera följande:
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Villkor</th>
<th style="border:1px solid black;" >Rekommendation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Ett stort antal datorer kommer att använda RMS</td>
<td style="border:1px solid black;">Använd Systems Management Server (SMS) eller grupprinciper när du installerar RMS med SP2-klienten.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Ett stort antal klientbegäran</td>
<td style="border:1px solid black;">Använd en server som fungerar som belastningsutjämnare, tjänsten Network Load Balancing i operativsystemet Windows Server eller en maskinvarubaserad belastningsutjämning som distribuerar begäran i klustret.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Två nätverksadaptrar som använder virtuell IP-adressering för hantering av extranät- och intranätbegäran</td>
<td style="border:1px solid black;">Se till att alla Domain Name System-registreringar (DNS) som visar den virtuella IP-adressen för extranätet också visar adressen till intranätet.</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc747637.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                                                                                                                                                              |  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Interna klientlicensbegäran kommer att misslyckas om inte DNS-registrering utförs för intranätet. Om det inte går att ändra DNS-inställningarna kan du ändra värdtabellen för varje server som ingår i klustret så att kluster-URL:en mappas till klustrets virtuella IP-adress. DNS-registreringen måste utföras innan du etablerar RMS. Om du redan har etablerat tjänsten måste du avinstallera RMS från servern och sedan upprepa etableringsprocessen. |
  
#### Klienter som fungerar med den här versionen
  
RMS-klient utan Service Pack, RMS-klient med SP1 och RMS-klient med SP2 kan installeras på alla datorer som har Microsoft Windows 2000, Windows XP eller Windows Server 2003 installerat. Tidigare versioner av Windows operativsystem fungerar inte med den här versionen.
  
| ![](images/Cc747637.Caution(WS.10).gif)Varning!                                                      |  
|-----------------------------------------------------------------------------------------------------------------------------------|  
| Om du använder RMS-klienten utan Service Pack kan den inte användas för onlinepublicering mot en RMS-server med SP1 eller senare. |
  
Funktionsförändringar  
---------------------
  
Det finns flera nya funktioner i RMS med SP2:
  
-   [Förbättrad gruppexpansion mellan skogar](#bkmk_cif1)  
-   [Förändringar av databasloggning](#bkmk_cif2)  
-   [Större serverbatchstorlekar](#bkmk_cif3)  
-   [Kompatibilitet med Microsoft SQL Server 2005](#bkmk_cif4)
  
<span id="BKMK_CIF1"></span>
#### Förbättrad gruppexpansion mellan skogar
  
#### Vad gör den här funktionen?
  
I RMS underlättar gruppexpansion mellan skogar förmågan hos RMS att expandera det universella gruppmedlemskapet i Active Directory i en annan skog där gruppmedlemskap inte replikeras mellan två skogar. Om en användare i en skog skickar skyddat innehåll till en användare i en annan skog genomgår RMS en identifieringsperiod, där användarens åtkomst till innehållet verifieras. Den verifieringsprocessen utförs genom att en LDAP-fråga ställs från den ena skogen till den andra för att hitta fjärrskogens RMS-tjänsteanslutningspunkt (SCP). När SCP för fjärrskogen har identifierats skickar RMS-tjänstekontot en begäran till gruppexpansionspipelinen. I begäran frågas fjärrskogen om användaren är medlem av en grupp.
  
#### Vem lämpar sig den här funktionen för?
  
Den nya funktionen är av intresse för RMS-kunder i en Active Directory-miljö med flera skogar, vars universella gruppmedlemskap inte replikeras mellan skogar.
  
#### Varför är den här förändringen viktig?
  
Det nya protokollet för skogsförtroendeexpansion förbättrar tillförlitligheten för kunder som använder en Active Directory-miljö med flera skogar.
  
#### Vad fungerar annorlunda?
  
Före RMS med SP2 uppnåddes gruppexpansion mellan skogar genom att .NET-fjärranrop användes. I den här versionen har protokollet för gruppexpansion mellan skogar ändrats till en ASP.NET-webbtjänst där SOAP/HTTP-begäran används till skogsförtroendegruppens expansionspipeline.
  
| ![](images/Cc747637.note(WS.10).gif)Obs!                                                                                                                                                                |  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Det finns fortfarande funktioner för.NET-fjärranrop i RMS med SP2 av bakåtkompabilitetsskäl. För att dra full nytta av det nya protokollet för gruppexpansion mellan skogar måste dock alla RMS-kluster köras med minst RMS med SP2. |
  
#### Vilka inställningar har lagts till eller ändrats i RMS med SP2?
  
Den nya RMS-gruppexpansionspipelinen har konfigurerats med säkrast tänkbara inställningar som standard i RMS med SP2 och endast lokala RMS-tjänste- och administratörsgrupper har åtkomst. Om du vill ge ett konto åtkomst ändrar du åtkomstlistan för gruppexpansionspipelinen som finns på wwwroot\\\_wmcs\\GroupExpansion\\GroupExpansion.asmx.
  
| ![](images/Cc747637.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                                                                          |  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Verifiera att RMS-tjänstekontot i varje Active Directory-skog har åtkomst till gruppexpansionspipelinen i alla RMS-servrar i klustret. Om kontona inte har åtkomst misslyckas gruppexpansionen. Du kan även skapa samma konto i varje skog och tilldela samma lösenord till kontona. I så fall behöver du bara lägga till ett enda konto till gruppexpansionspipelinen. |
  
Nya händelser har lagts till i RMS med SP2 för att informera dig om problemmeddelanden som inte nådde fram till tjänsten Meddelandeköer. De nya händelseloggarna innehåller händelser som meddelar dig om ett meddelande inte går att signera digitalt eller om meddelandet inte går att verifiera. Några exempel på verifieringsproblem är ett felaktigt utformat meddelande, ett saknat hash-värde eller signatur eller ett felaktigt hash-värde eller signatur.
  
<span id="BKMK_CIF2"></span>
#### Förändringar av databasloggning
  
#### Vad gör den här funktionen?
  
RMS använder en lyssnartjänst för loggning som skickar all RMS-kommunikation till loggningsdatabasen med hjälp av meddelandeköer. RMS-klustret skickar meddelanden till tjänsten Meddelandeköer och lyssnartjänsten för loggning hämtar meddelandena från kön i Meddelandeköer och skriver dem i loggningsdatabasen.
  
#### Vem lämpar sig den här funktionen för?
  
Den här funktionen lämpar sig för befintliga användare av RMS som använder lyssnartjänsten för loggning i RMS och för nya användare av RMS med SP2 som överväger att använda lyssnartjänsten för loggning i RMS.
  
#### Varför är den här förändringen viktig?
  
I tidigare versioner av RMS skyddades RMS-loggningskön genom att åtkomstlistor användes, men autentisering var inte aktiverad. Utan autentisering kan en användare med skadligt uppsåt potentiellt skriva felaktiga meddelanden i RMS-loggningskön.
  
#### Vad fungerar annorlunda?
  
I RMS med SP2 utförs extra autentisering av meddelanden som överförs av RMS-kluster genom att meddelandeköer används. Förutom åtkomstlistor som förhindrar obehörig åtkomst till meddelandekön skyddas även kön i Meddelandeköer genom användning av en mekanism för verifiering av meddelandets autenticitet. När ett meddelande skickas till tjänsten Meddelandeköer genererar RMS-pipelines ett hash-värde för meddelandet och signerar det digitalt genom att använda RMS-klustrets privata nyckel. Lyssnartjänsten för loggning beräknar först ett eget hash-värde för meddelandet och jämför det med det hash-värde som finns i meddelandet. Om hash-värdena stämmer överens verifierar lyssnartjänsten för loggning sedan signaturen genom att använda klustrets offentliga nyckel och hash-värdet i meddelandet. Om hash-värdena stämmer överens och signaturen verifieras skickas meddelandet till loggningsdatabasen. Om verifieringsstegen inte lyckas ta meddelandet bort permanent från kön i Meddelandeköer och en händelsevarning skrivs i programloggen i Loggboken.
  
#### Vilka inställningar har lagts till eller ändrats i RMS med SP2?
  
Nya händelser har lagts till i RMS med SP2 som har utvecklats för att visa att problemmeddelanden inte nådde till kön i Meddelandeköer. De nya händelserna skrivs i programloggen och inkluderar meddelanden som inte går att signera digitalt eller meddelanden vars digitala signaturer inte går att verifiera. Några exempel på verifieringsproblem är ett felaktigt utformat meddelande, ett saknat hash-värde eller signatur eller ett felaktigt hash-värde eller signatur.
  
<span id="BKMK_CIF3"></span>
#### Större serverbatchstorlekar
  
#### Vad gör den här funktionen?
  
Batchkörning i RMS ökar prestanda genom att flera licensbegäran nu kan skickas till RMS-klustret som en enda begäran i stället för att göra en enskild begäran för varje licens.
  
#### Vem lämpar sig den här funktionen för?
  
Möjligheten med större serverbatchstorlekar är av intresse för RMS-aktiverade program där flera licenser behövs skaffas samtidigt för skyddat innehåll.
  
#### Varför är den här förändringen viktig?
  
RMS-batchkörning möjliggör att en enda begäran utfärdas till AcquireLicense RMS-pipelinen för att hämta användarlicenser för flera rättighetskontocertifikat (RAC) mot en eller flera publiceringslicenser. Utan en batchstorlek som är större än 1 skulle det RMS-aktiverade programmet behöva begära en användarlicens individuellt för varje användare.
  
#### Vad fungerar annorlunda?
  
I tidigare RMS-versioner än RMS med SP2 kunde RMS-klustret ha en maximal batchstorlek på 1. Om maximal storlek ställdes in som en siffra högre än 1 ignorerades den av klustret. Med RMS med SP2 kan den maximala batchstorleken vara så stor som 100.
  
| ![](images/Cc747637.note(WS.10).gif)Obs! |  
|-----------------------------------------------------------------------|  
| Bara AcquireLicense RMS-pipelinen har funktioner för batchbegäran.    |
  
Felrapporteringen har förbättrats i RMS med SP2 för att redovisa för batchbegäran. Om du till exempel skickar en batch med tio begäran och den andra och tredje begäran misslyckas, skrivs en händelse i händelseloggen för varje fel.
  
<span id="BKMK_CIF4"></span>
#### Kompatibilitet med Microsoft SQL Server 2005
  
#### Vad gör den här funktionen?
  
I RMS med SP2 kan Microsoft SQL Server 2005 användas som databasserver som stöd för RMS-konfiguration och loggningsdatabaser utan att någon extra konfiguration behöver utföras.
  
#### Vem lämpar sig den här funktionen för?
  
Möjligheten att använda Microsoft SQL Server 2005 med RMS med SP2 är av intresse för RMS-kunder som vill använda Microsoft SQL Server 2005 som RMS-databas.
  
#### Varför är den här förändringen viktig?
  
I tidigare versioner av RMS var datatyper hos vissa av parametrarna som användes i systemmeddelandetabellen inkompatibla med formatspecifikationen i Microsoft SQL Server 2005. Mer information finns i artikel 913372 i Microsoft Knowledge Base ([http://go.microsoft.com/fwlink/?LinkId=68638](http://go.microsoft.com/fwlink/?linkid=68638)).
  
#### Vad fungerar annorlunda?
  
I tidigare versioner av RMS än RMS med SP2 användes SQL RAISERROR-satser för att meddela RMS-användaren om att ett fel hade inträffat. RAISERROR-satsen frågar systemmeddelandetabellen och hämtar de RMS-felmeddelanden som lagras i tabellen. I RMS med SP2 används en annan teknik för att sprida SQL-fel så att det inte längre finns något beroende av systemmeddelandetabellen.
  
| ![](images/Cc747637.note(WS.10).gif)Obs!                                                                                                                                                                                                                 |  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om du uppgraderar från RMS med SP1 till RMS med SP2 skapas inga frågor till systemmeddelandetabellen om felmeddelanden, men själva felmeddelandena kvarstår i systemmeddelandetabellen. Med en ren installation av RMS med SP2 läggs inte nya poster till i systemmeddelandetabellen. |
  
Kända problem  
-------------
  
I följande avsnitt behandlas kända problem med den här versionen av RMS.
  
#### Hjälpfilen hänvisar fortfarande till RMS med Service Pack 1
  
Hjälpfilen som ingår i installationen av RMS med SP2 hänvisar fortfarande till RMS med SP1. Information om RMS med SP2 finns i Rights Management Services ([http://go.microsoft.com/fwlink/?LinkId=68637](http://go.microsoft.com/fwlink/?linkid=68637)).
  
#### Det går inte att installera RMS med SP2-klienten via Windows Update i x64-baserade eller Itanium-baserade datorer
  
Om RMS-klienten eller RMS med SP1-klienten installeras i en x64-baserad dator och du försöker uppgradera klienten till RMS med SP2-klienten (x64) från Windows Update misslyckas installationen. Även om tidigare RMS-klienter som skapades för 32-bitarssystem fungerade i x64-baserade datorer kan de inte uppgraderas till RMS med SP2-klienten (x64). Du måste först avinstallera den tidigare RMS-klienten och sedan starta uppdateringen igen. Windows Update identifierar operativsystemets version och erbjuder rätt RMS med SP2-klient. Detsamma gäller för Itanium-baserade datorer.
  
#### När etableringen görs om går det inte att starta lyssnartjänsten för loggning
  
När klustret inte har etablerats inträffar ett fel i lyssnartjänsten för loggning och den kan inte lämnas i stoppat läge. Du måste starta om datorn för att stoppa tjänsten helt och hållet.
  
#### Det går inte att ta bort en betrodd publiceringsdomän som inte baseras på programvara
  
Efter import av en betrodd publiceringsdomän med implementering av privat nyckel som inte är programvarubaserad går det inte att ta bort domänen. Import av en privat nyckel som inte är programvarubaserad bör inte göras från administrationskonsolen i Windows Rights Management Services. Kontakta tillämplig maskinvaruleverantör om du vill ha instruktioner om export och import av privata nycklar.
  
#### Microsoft .NET Framework 2.0 ändrar virtuella IIS-rotkataloger vid installation i RMS-servern
  
RMS med SP2 använder ASP.NET-skriptmappning som ingår i .NET Framework version 1.1. Mappningen som ingår i senare versioner är inte kompatibel med RMS med SP2. Båda versionerna kan dock användas samtidigt utan att påverka andra beroende program. Om .NET Framework 1.1 och .NET Framework 2.0 eller senare är installerat kan det hända att RMS-servern inte fungerar på rätt sätt trots att installationen och etableringen av RMS med SP2 verkar ha slutförts på rätt sätt. Anledningen är att de virtuella RMS-rotkatalogerna måste vara registrerade med ASP.NET-skriptmappning version 1.1 i stället för version 2.0. Om du vill registrera de virtuella RMS-rotkatalogerna med ASP.NET-skriptmappning version 1.1 anger du följande kommando i Kommandotolken:
  
**%windir%\\Microsoft.NET\\Framework\\v1.1.4322&gt;aspnet\_regiis.exe -s W3SVC/1/ROOT/\_wmcs**
  
När du kör kommandot registreras de virtuella RMS-rotkatalogerna på rätt sätt och RMS med SP2 aktiveras för att köras i servern.
  
#### Gruppmedlemskap kan saknas vid användning av den enhetliga funktionsnivån Active Directory Windows 2000
  
Vid distribution av RMS i en miljö där infrastrukturnivåerna i Active Directory har höjts till den enhetliga funktionsnivån Windows 2000 kanske RMS inte kan läsa attributet memberOf i Active Directory-objekt vid försök att expandera gruppmedlemskap för dolda distributionslistor. RMS-tjänstkontot måste använda ett domänkonto som tillhör gruppen Åtkomst till äldre operativsystem (före Windows 2000) i skogen för att det ska gå att läsa attributet memberOf i Rights Management Services. Mer information finns i Microsoft Knowledge Base, artikel 812841 ([http://go.microsoft.com/fwlink/?LinkId=78152](http://go.microsoft.com/fwlink/?linkid=78152)).
  
#### Lyssnartjänsten för loggning skickar meddelanden för Meddelandeköer till Dead Letter-kön när databasen inte är åtkomlig
  
Det finns tillfällen (t.ex. databasen är inte igång, problem med nätverksanslutning osv.) när lyssnartjänsten för loggning inte kan nå databasen. I sådana fall skickas meddelanden till en Dead Letter-kö. Det enda sättet att återställa meddelandena (d.v.s. skicka dem till loggningsdatabasen) är att använda verktyget RMS-återställning av kö, som levereras med RMS-administrationsverktygen. Om du vill hämta RMS-administrationsverktyg går du till [http://go.microsoft.com/fwlink/?LinkId=33841](http://go.microsoft.com/fwlink/?linkid=33841).
  
| ![](images/Cc747637.note(WS.10).gif)Obs!                                                                                                                                              |  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Recover och RecoverandPurge har tagits bort från LogRecoveryCmd. Det här garanterar att alla meddelanden dirigeras tillbaka via tjänsten Meddelandeköer och autentiseras innan de skickas till loggningsdatabasen. |
  
#### Du måste uppgradera RMS med SP2 innan du uppgraderar Microsoft SQL Server 2005
  
Vid uppgradering av RMS med SP2 och från Microsoft SQL Server 2000 till Microsoft SQL Server 2005 ska du se till att först uppgradera RMS. Det undviker kompatibilitetsproblem med uppgraderingen av Microsoft SQL Server.
  
#### Det går inte att etablera RMS med SP2 på webbplatser vars namn innehåller en apostrof (')
  
Om du försöker etablera RMS med SP2 på en webbplats vars namn innehåller ett apostroftecken (') kommer etableringsprocessen att misslyckas och felmeddelandet "**Ogiltig parameter**" visas. Om du vill etablera RMS med SP2 på webbplatsen tar du bort apostrofen från webbplatsens namn.
  
#### Aktivera ASP.NET version 1.1 på servrar som kör en 64-bitars version av Windows Server 2003
  
I avsnittet "Systemkrav" i RMS-hjälpen finns information om hur du installerar .NET Framework 1.1 och aktiverar ASP.NET 1.1 när du har installerat Internet Information Services (IIS). Om .NET Framework 1.1 installeras före IIS kommer dock ASP.NET 1.1 inte att finnas med i webbtjänsttilläggen och den beskrivna proceduren går inte att använda. Om IIS installerades efter .NET Framework 1.1 anger du följande kommando i Kommandotolken för att aktivera ASP.NET:
  
**%SystemRoot%\\Microsoft.NET\\Framework\\v1.1.4322\\aspnet\_regiis.exe -i –enable**
  
Om du använder en senare version av .NET Framework än 1.1 byter du ut **-i** mot **-ir** i kommandot för att undvika återställning av befintliga IIS-skriptmappningar.
  
#### RMS-tjänstekonto för fjärrskogar måste läggas till till lokal gruppexpansionspipeline
  
Ett säkerhetsproblem korrigerades, vilket tar bort BUILTIN\\users från ACL i gruppexpansionspipelinen. Det kan bryta gruppexpansion mellan skogsscenarier. För att lösa problemet vidtar du följande steg:
  
**Lägg till RMS-tjänstekontot till fjärrskogen**  
1.  Under Forest1, där Forest1 är RMS-rotklustret i den första skogen, går du till inetpub\\wwwroot\\\_wmcs.
  
2.  Högerklicka på mappen **Gruppexpansion** och välj sedan **Egenskaper**.
  
3.  I fönstret **Egenskaper för gruppexpansion** klickar du på fliken **Säkerhet** och lägger till posten för *Forest2\\RmsServiceAccount* (till exempel rmil31\\rmsvc), där Forest2 är RMS-rotklustret i den andra skogen.
  
4.  Klicka på **OK**.
  
5.  Klicka på **Kör**, skriv **iisreset** och klicka sedan på**OK**.
  
#### Uppgradering av .NET Framework kan resultera i dataförlust
  
Om .NET Framework (CLR) version 1.1 uppgraderas efter att RMS har installerats och etablerats ställs vroots in för att använda .NET Framework version 2.0. Om det händer loggas ingen information i loggningsdatabasen. Det resulterar i dataförlust. Vidta en av följande åtgärder:
  
-   Uppgradera .NET Framework före installation och etablering av RMS.  
-   Återställ vroots så att 1.1 används efter att .NET Framework har uppgraderats.
  
Dokumentationsändringar i den här versionen  
-------------------------------------------
  
Här följer en lista över avsnitt som har ändrats i den här versionen:
  
-   Så här skapar du förtroende för Passport-baserade rättighetskontocertifikat ([http://go.microsoft.com/fwlink/?LinkId=70369](http://go.microsoft.com/fwlink/?linkid=70369))  
-   Programvarukrav för RMS ([http://go.microsoft.com/fwlink/?LinkId=70371](http://go.microsoft.com/fwlink/?linkid=70371))  
-   Så här distribuerar du RMS-klienten ([http://go.microsoft.com/fwlink/?LinkId=70373](http://go.microsoft.com/fwlink/?linkid=70373))  
-   RMS-installation via kommandotolken ([http://go.microsoft.com/fwlink/?LinkId=70374](http://go.microsoft.com/fwlink/?linkid=70374))  
-   Viktiga konfigurationsdatabastabeller i RMS ([http://go.microsoft.com/fwlink/?LinkId=70375](http://go.microsoft.com/fwlink/?linkid=70375))  
-   Certifieringstabeller för konfigurationsdatabas i RMS ([http://go.microsoft.com/fwlink/?LinkId=70376](http://go.microsoft.com/fwlink/?linkid=70376))  
-   RMS-loggningsdatabastabeller ([http://go.microsoft.com/fwlink/?LinkId=70377](http://go.microsoft.com/fwlink/?linkid=70377))  
-   Utvärdera skalningskrav [http://go.microsoft.com/fwlink/?LinkId=70378](http://go.microsoft.com/fwlink/?linkid=70378))  
-   Skydda RMS-distributionen ([http://go.microsoft.com/fwlink/?LinkId=70379](http://go.microsoft.com/fwlink/?linkid=70379))  
-   Aktivera inaktiveringstjänsten ([http://go.microsoft.com/fwlink/?LinkId=70380](http://go.microsoft.com/fwlink/?linkid=70380))  
-   Planera för externa RMS-användare [http://go.microsoft.com/fwlink/?LinkId=70381](http://go.microsoft.com/fwlink/?linkid=70381))  
-   Aktivera RMS-serverfunktioner för mobila enheter och servertjänster ([http://go.microsoft.com/fwlink/?LinkId=70382](http://go.microsoft.com/fwlink/?linkid=70382))
  
#### Copyright
  
*Informationen i det här dokumentet visar Microsoft Corporations aktuella hållning i de ämnen som tas upp vid publiceringstillfället. Eftersom Microsoft snabbt måste agera efter förändringar på marknaden ska den inte tolkas som bindande från Microsofts sida, och Microsoft kan inte heller garantera korrektheten i informationen efter publiceringsdatumet.*
  
*Det här dokumentet är endast avsett som information. MICROSOFT GER INGA GARANTIER, UTTRYCKLIGA, UNDERFÖRSTÅDDA ELLER LAGSTADGADE, VAD GÄLLER INFORMATIONEN I DET HÄR DOKUMENTET.*
  
*Ansvaret för att följa upphovsrättslagar ligger på användaren. Ingen del av det här dokumentet får reproduceras, lagras eller infogas i ett informationssystem eller överföras i någon form, med något medel (elektroniska eller mekaniska medier, fotokopiering, inspelning eller någon annan form av reproduktion) eller för något ändamål utan uttrycklig skriftlig tillåtelse från Microsoft Corporation.*
  
*För innehållet i det här dokumentet kan Microsoft inneha patent, patentansökningar, varumärken, copyright eller andra rättigheter som regleras av upphovsrättslagar. Innehav av detta dokument medför inga rättigheter till patent, varumärken, copyright eller andra upphovsrättsskyddade produkter utöver vad som uttryckligen anges i ett skriftligt licensavtal med Microsoft.*
  
*Om inget annat anges är de exempel på företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser som nämns i det här dokumentet påhittade, och alla eventuella kopplingar till verkliga företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser är helt oavsiktliga.*
  
*© 2006 Microsoft Corporation. Med ensamrätt.*
  
*Active Directory, Microsoft, MS-DOS, Visual Studio, Windows, Windows Server, SQL Server och Windows NT är antingen registrerade varumärken eller varumärken som tillhör Microsoft Corporation i USA och/eller andra länder.*
  
*Namnen på befintliga företag och produkter som nämns här kan vara varumärken som tillhör respektive ägare.*
