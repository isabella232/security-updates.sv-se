---
TOCTitle: 'Filen Viktigt.txt för Microsoft Windows Server Update Services 3.0 SP1'
Title: 'Filen Viktigt.txt för Microsoft Windows Server Update Services 3.0 SP1'
ms:assetid: 'a5aa93bf-842b-4ad4-ab0f-fe867843cb02'
ms:contentKeyID: 18152953
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708525(v=WS.10)'
---

Filen Viktigt.txt för Microsoft Windows Server Update Services 3.0 SP1
======================================================================

Den här Viktigt-filen beskriver kända problem som påverkar Microsoft® Windows® Server Update Services (WSUS) 3.0 Service Pack 1 och innehåller rekommendationer och krav för att installera programmet. Dessa anmärkningar innehåller följande avsnitt:

-   Systemkrav för serverinstallation av WSUS 3.0 SP1
-   Konfigurationskrav för serverinstallation av WSUS 3.0 SP1
-   Systemkrav för fjärrkonsolinstallation av WSUS 3.0 SP1
-   Systemkrav för klientinstallation
-   Programvarukrav för serverinstallation av WSUS SP1
-   Minimala diskutrymmeskrav för serverinstallation av WSUS 3.0 SP1
-   Uppgraderingskrav för WSUS 3.0 SP1
-   Konfigurera kommandoradsparametrar
-   Konfigurationsproblem
-   Uppgraderingsproblem
-   Kända problem
-   WSUS 3.0 SP1 på Windows Server® 2008
-   WSUS 3.0 SP1 på Windows Small Business Server 2003

Systemkrav för serverinstallation av WSUS 3.0 SP1
-------------------------------------------------

#### WSUS 3.0 SP1-servern stöds i Windows Server 2008 och Windows Server 2003 Service Pack 1

WSUS 3.0 SP1-servern stöds i Windows Server 2008 och Windows Server 2003 Service Pack 1.

#### Windows 2000 Server stöds inte för WSUS 3.0 SP1-servrar

Microsoft Windows® 2000 Server är inte ett operativsystem som stöds för WSUS 3.0 SP1-servrar.

#### WSUS 3.0 SP1 stöds inte på servrar som kör Terminal Services

Även om WSUS 3.0 SP1 går att köras på servrar som kör Terminal Services är det inte något som stöds eller rekommenderas. WSUS 3.0 SP1 går inte att köras på en server som kör Terminal Services i konfigurationer som använder fjärrimplementeringar av SQL Server. Installationen kan misslyckas eftersom alla anpassade åtgärder (inklusive installation) som görs med fjärranslutning på en Terminal Services-licensserver körs som systemkontot, och serverns systemkonto kanske inte har behörigheter på fjärrinstans av SQL Server.

Konfigurationskrav för serverinstallation av WSUS 3.0 SP1
---------------------------------------------------------

#### IIS måste vara installerat

WSUS 3.0 SP1 kräver IIS (Internet Information Services), vilket dock inte finns installerat som standard i Windows Server 2008 eller Microsoft Windows Server 2003. Om du försöker installera WSUS 3.0 SP1 utan IIS, visar Installationsprogrammet för Windows Server Update Services ett felmeddelande som talar om att IIS inte installerats.

#### Om IIS körs i IIS 5.0-isoleringsläge misslyckas installationen

Om du har uppgraderat servern från Windows 2000 Server till Windows Server 2003 kan IIS köras i IIS 5.0-kompatibilitetsläge. Det är också möjligt att aktivera IIS 5.0-isoleringsläge i IIS Manager. Detta leder till att installationen misslyckas. Du måste inaktivera IIS 5.0-isoleringsläget innan du installerar WSUS 3.0 SP1.

#### Om någon IIS-komponent installeras i 32-bitars kompatibilitetsläge på en 64-bitars plattform kan installationen av WSUS 3.0 SP1 misslyckas

Alla IIS-komponenter ska installeras i enhetligt läge på 64-bitars plattformar. Installationen kan misslyckas om någon av IIS-komponenterna är i 32-bitars kompatibilitetsläge.

#### Proxyservrar kan endast stödja HTTP, eller HTTP och HTTPS

I WSUS 3.0 SP1 är det möjligt för en proxyserver att enbart stödja HTTP. Du bör konfigurera en andra proxyserver som kör HTTPS genom att använda kommandoraden (**wsusutil configuresslproxy**) innan du konfigurerar WSUS-servern från konfigurationsguiden eller administrationskonsolen.

#### Om två eller flera webbplatser redan körs på port 80 ska du ta bort alla utom en innan du installerar WSUS

Om du har två eller flera webbplatser som körs på port 80 (t.ex. Windows® SharePoint® Services), bör du ta bort alla utom en av dem innan du installerar WSUS. Om du inte gör det kanske det inte går att uppdatera serverns klienter automatiskt.

#### När du installerar WSUS 3.0 SP1 kanske du måste inaktivera antivirusprogram

När du installerar WSUS 3.0 SP1 kanske du måste inaktivera antivirusprogram innan du kan utföra installationen utan problem. När du har inaktiverat antivirusprogrammet ska du starta om datorn innan du installerar WSUS. När du startar om datorn förhindrar det att filer låses när installationsprocessen måste nå dem. När installationen är klar ska du se till att du återigen aktiverar antivirusprogrammet. Gå till antivirusprogramleverantörens webbplats för exakta steg för att inaktivera och återigen aktivera ditt antivirusprogram och versionen av programmet.

| ![](images/Cc708525.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Denna bugglösning kan göra datorn och nätverket mer sårbara för attack av illvilliga användare eller av skadlig programvara, till exempel virus. Vi rekommenderar inte denna bugglösning. Vi tillhandahåller dock den här informationen så att du kan implementera den här bugglösningen efter eget gottfinnande. Använd den här bugglösningen på egen risk. |

| ![](images/Cc708525.note(WS.10).gif)Obs!                                                                                                                                                                                               |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ett antivirusprogram är avsett att hjälpa dig att skydda datorn från virus. När antivirusprogrammet är inaktiverat får du inte hämta eller öppna filer från källor som du inte litar på, gå till webbplatser som du inte har tillit till eller öppna e-postbilagor. |

#### WSUS 3.0 SP1 kräver att alternativet med nästlade utlösningar är på i SQL Server

Alternativet för nästlade utlösningar är som standard på. En SQL Server-administratör kan dock stänga av det.

Om du avser att använda en SQL Server-databas som databas i Windows Server Update Services ska SQL Server-administratören bekräfta att alternativet för nästlade utlösningar på servern aktiveras innan WSUS 3.0 SP1-administratören installerar WSUS 3.0 SP1 och anger databas under konfigurationen.

Installationsprogrammet för WSUS 3.0 SP1 aktiverar alternativet RECURSIVE\_TRIGGERS som är ett databasspecifikt alternativ. Det aktiverar dock inte alternativet med nästlade utlösningar som är ett serverglobalt alternativ.

Använd följande för att se om alternativet för nästlade utlösningar är på:

**sp\_configure 'nested triggers'**

Aktivera alternativet nästlade utlösningar i SQL Server genom att köra följande från kommandofil på datorn som kör SQL Server:

**sp\_configure 'nested triggers', 1**

**GO**

**RECONFIGURE**

**GO**

Du kan köra SQL-skript från kommandoraden om du inte har SQL Server Management Studio på servern. Du kan hämta Microsoft SQL Server 2005 Command Line Query Utility från [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=70728) (http://go.microsoft.com/fwlink/?LinkId=70728). Kör **sqlcmd** för att komma igång.

Om du vill köra SQL-skript mot Windows Internal Database måste du dessutom hämta SQL Server Native Client från samma hämtningssida.

#### Begränsningar och krav för fjärr-SQL

WSUS 3.0 SP1 erbjuder stöd för körning av databasprogram på en dator som är separat från datorn med resten av WSUS 3.0 SP1-programmet. Det finns vissa krav vid konfigurationen av en fjärr-SQL-installation:

-   Du kan inte använda en server som konfigurerats som domänkontrollant för serverdelen på fjärr-SQL-paret.
-   Du får inte köra Terminal Server på den dator som ska vara servern på en fjärr-SQL-installation.
-   Du måste använda som lägst Microsoft SQL Server 2005 Service Pack 1 (tillgänglig från [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=66143) (http://go.microsoft.com/fwlink/?LinkId=66143) för databasprogramvara på serverdelen om den datorn kör Windows Server 2003 och SQL Server 2005 Service Pack 2 om serverdatorn kör Windows Server® 2008.
-   Både frontdatorn och serverdelen måste anslutas till en Active Directory-domän. Om de finns i olika domäner måste du upprätta förtroende mellan domänerna innan du kör WSUS-installationen.
-   Om du redan har installerat WSUS 2.0 i en fjärr-SQL-konfiguration och vill uppgradera till WSUS 3.0 SP1 ska du avinstallera WSUS 2.0 (med **Lägg till eller ta bort program** i Kontrollpanelen) på serverdelen samtidigt som du försäkrar dig om att den befintliga databasen förblir oförändrad. Du ska sedan installera SQL Server 2005 SP1 eller SP2 och uppgradera den befintliga databasen. Installera till sist WSUS 3.0 SP1 på frontdatorn.

Systemkrav för fjärrkonsolinstallation av WSUS 3.0 SP1
------------------------------------------------------

Du kan installera fjärrkonsolen WSUS 3.0 SP1 på följande plattformar:

-   Windows Server 2008
-   Windows Vista® eller senare
-   Windows Server 2003 SP1 eller senare
-   Windows XP SP2 eller senare

Systemkrav för klientinstallation
---------------------------------

Automatiska uppdateringar är programvaran för WSUS-klienten. Den går att använda med WSUS på något av följande operativsystem:

-   Windows Vista eller senare
-   Windows Server 2008 eller senare
-   Microsoft Windows Server 2003, valfri version
-   Microsoft Windows XP Professional SP2 eller senare
-   Microsoft Windows 2000 Professional SP4, Windows 2000 Server SP4 eller Windows 2000 Advanced Server med SP4

Programvarukrav för serverinstallation av WSUS 3.0 SP1
------------------------------------------------------

Följande tabell visar den obligatoriska programvaran för Windows Server 2003 SP1-plattformar. Den programvara som är obligatorisk för Windows Server 2008 finns i det avsnitt som beskriver WSUS 3.0 SP1 i Windows Server 2008.

Innan du kör installationen av WSUS 3.0 SP1 ska du kontrollera att WSUS 3.0 SP1-servern uppfyller den här listan med krav. Om någon av dessa uppdateringar kräver att du startar om datorn när installationen har slutförts, måste du starta om innan du kan installera WSUS 3.0 SP1.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Krav</th>
<th style="border:1px solid black;" >Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Microsoft IIS (Internet Information Services)</td>
<td style="border:1px solid black;">Installera från operativsystemet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft .NET Framework Version 2.0 Redistributable Package</td>
<td style="border:1px solid black;">Se Microsoft .NET Framework Version 2.0 Redistributable Package (x86) på <a href="http://go.microsoft.com/fwlink/?linkid=68935">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=68935). För 64-bitars plattformar, se Microsoft .NET Framework Version 2.0 Redistributable Package (x64) på <a href="http://go.microsoft.com/fwlink/?linkid=70637">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70637)</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Management Console 3.0 för Windows Server 2003</td>
<td style="border:1px solid black;">Detta är en förutsättning för att kunna använda användargränssnittet i WSUS 3.0 SP1. Se Microsoft Management Console 3.0 för Windows Server 2003 (KB907265) på <a href="http://go.microsoft.com/fwlink/?linkid=70412">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70412). För 64-bitars plattformar, se Microsoft Management Console 3.0 för Windows Server 2003 x64 Edition (KB907265) på <a href="http://go.microsoft.com/fwlink/?linkid=70638">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70638).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft Report Viewer</td>
<td style="border:1px solid black;">Detta är en förutsättning för att kunna använda användargränssnittet i WSUS 3.0 SP1. Se Microsoft Report Viewer Redistributable 2005 på <a href="http://go.microsoft.com/fwlink/?linkid=70410">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70410).</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">SQL Server 2005 (valfritt)</td>
<td style="border:1px solid black;">WSUS 3.0 SP1 installerar Windows Internal Database åt dig om det inte redan finns en installerad kompatibel version av SQL Server. Om du avser att använda en fullständig SQL Server-databas, måste du (som lägst) använda SQL Server 2005 SP1 (tillgänglig på <a href="http://go.microsoft.com/fwlink/?linkid=66143">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=66143) på Windows Server 2003 eller SQL Server 2005 SP2 (tillgänglig på <a href="http://go.microsoft.com/fwlink/?linkid=84823">Microsoft Download Center</a> på http://go.microsoft.com/fwlink/?LinkId=84823) på Windows Server 2008.</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc708525.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                      |  
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om WSUS 2.0 har installerats tidigare och det använder SQL Server 2000, SQL Server Desktop Engine 2000 eller någon SQL Server-databas som är tidigare än SQL Server 2005 SP1 (eller SQL Server 2005 SP2 på Windows Server 2008), kommer installationsprogrammet för WSUS 3.0 SP1 att installera Windows® Internal Database och migrera databasen till den. |
  
Minimala diskutrymmeskrav för serverinstallation av WSUS 3.0 SP1  
----------------------------------------------------------------
  
Följande är minimala diskutrymmeskrav för att installera Windows Server Update Services:
  
-   1 GB på systempartitionen  
-   2 GB för den volym som databasfiler ska lagras på  
-   20 GB för volymen som innehållet lagras på
  
| ![](images/Cc708525.Important(WS.10).gif)Viktigt!                                             |  
|----------------------------------------------------------------------------------------------------------------------------|  
| Det går inte att installera WSUS 3.0 SP1 på komprimerade enheter. Kontrollera att den enhet du väljer inte är komprimerad. |
  
Uppgraderingskrav för WSUS 3.0 SP1  
----------------------------------
  
#### Se till att WSUS-installationen körs och säkerhetskopiera WSUS-databasen före uppgraderingen
  
Om du uppgraderar till WSUS 3.0 SP1 från en tidigare version, se till att den nuvarande installationen körs och säkerhetskopiera WSUS-databasen före uppgraderingen.
  
1.  Se efter om det finns nya fel i händelseloggar, problem med synkronisering mellan underordnade servrar och överordnade servrar eller problem med klienter som inte rapporterar. Se till att dessa problem har lösts innan du fortsätter.  
2.  Du kan köra DBCC CHECKDB för att försäkra dig om att WSUS-databasen är korrekt indexerad. För mer information om DBCC CHECKDB, gå till [DBCC CHECKDB](http://go.microsoft.com/fwlink/?linkid=86948) (http://go.microsoft.com/fwlink/?LinkId=86948).  
3.  Säkerhetskopiera WSUS-databasen.
  
#### Avinstallera före uppgradering om du har modifierat porten som används av WSUS manuellt
  
När du modifierar porten för WSUS ska du alltid använda verktyget wsusutil i stället för att försöka modifiera porten manuellt. Om du har modifierat porten manuellt och tidigare uppgraderat från Software Update Services 1.0 till WSUS 2.0:
  
1.  Om du ännu inte har installerat WSUS 3.0, avinstallera WSUS 2.0. Behåll databasen och innehållet. (Om du redan har installerat WSUS 3.0, avinstallera det. Behåll databasen och innehållet.)  
2.  Starta standardwebbplatsen, aktivera temporärt SUS 1.0 igen. Gör det dock tillgängligt för avinstallationsprogrammet.  
3.  Avinstallera SUS 1.0.  
4.  Installera WSUS 3.0.
  
#### Software Update Services 1.0 bör avinstalleras
  
Installationen av WSUS 3.0 SP1 misslyckas om Software Update Services 1.0 är installerat på samma dator. Du ska avinstallera Software Update Services 1.0 innan du installerar WSUS 3.0 SP1.
  
#### Det är inte möjligt att uppgradera från WSUS 2.0 till WSUS 3.0 SP1 på ett 64-bitars operativsystem
  
WSUS 2.0 stöds inte i 64-bitars operativsystem. Det är inte möjligt att uppgradera från WSUS 2.0 till WSUS 3.0 SP1 på ett 64-bitars operativsystem
  
Konfigurera kommandoradsparametrar  
----------------------------------
  
Du kan utföra oövervakade installationer av WSUS 3.0 SP1 genom att använda WSUS-installationsprogrammet med kommandorad. Den här tabellen visar kommandoradsparametrarna för WSUS 3.0 SP1-konfigurationen.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Alternativ</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;"><strong>/q</strong></td>
<td style="border:1px solid black;">Utför tyst installation.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/u</strong></td>
<td style="border:1px solid black;">Avinstallera produkten. Avinstallerar dessutom Windows Internal Database-instansen om den installeras.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/p</strong></td>
<td style="border:1px solid black;">Endast förutsättningskontroll. Installerar inte produkten. Det inspekterar dock systemet och rapporterar eventuella förutsättningar som saknas.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/?, /h</strong></td>
<td style="border:1px solid black;">Visa kommandoradsparametrar och tillhörande beskrivningar.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/g</strong></td>
<td style="border:1px solid black;">Uppgradera från tidigare WSUS-version. (Försök inte uppgradera från SUS 1.0.) Den enda giltiga parametern med detta alternativ är /q (tyst installation). Den enda giltiga egenskapen med detta alternativ är DEFAULT_WEBSITE.</td>
</tr>
</tbody>
</table>
  
Den här tabellen visar kommandoradsegenskaperna för WSUS 3.0 SP1.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Egenskap</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">CONTENT_LOCAL</td>
<td style="border:1px solid black;">0=innehåll som finns lokalt, 1=värd i Microsoft Update</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">CONTENT_DIR</td>
<td style="border:1px solid black;">Sökväg till innehållskatalog. Standard är <em>WSUSInstallationsenhet</em><strong>\WSUS\WSUSInnehåll</strong>, där <em>WSUSInstallationsenhet</em> är den lokala enheten med största mängd ledigt utrymme.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">WYUKON_DATA_DIR</td>
<td style="border:1px solid black;">Sökväg till datakatalog i Windows Internal Database.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">SQLINSTANCE_NAME</td>
<td style="border:1px solid black;">Namnet ska visas i formatet <em>Servernamn</em>\<em>SQLInstansnamn</em>. Om databasinstansen finns på den lokala datorn, använd miljövariabeln %COMPUTERNAME%. Om det inte finns någon befintlig instans är standard %COMPUTERNAME%\WSUS.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DEFAULT_WEBSITE</td>
<td style="border:1px solid black;">0=port 8530, 1=port 80</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">PREREQ_CHECK_LOG</td>
<td style="border:1px solid black;">Sökväg och filnamn för loggfil</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">CONSOLE_INSTALL</td>
<td style="border:1px solid black;">0=installera WSUS-servern, 1=installera endast konsol</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">ENABLE_INVENTORY</td>
<td style="border:1px solid black;">0=installera inte inventeringsfunktioner, 1=installera inventeringsfunktioner</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DELETE_DATABASE</td>
<td style="border:1px solid black;">0=behåll databas, 1=ta bort databas</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">DELETE_CONTENT</td>
<td style="border:1px solid black;">0=behåll innehållsfiler, 1=ta bort innehållsfiler</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DELETE_LOGS</td>
<td style="border:1px solid black;">0=behåll loggfiler, 1=ta bort loggfiler (används med installationsväxeln /u).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">CREATE_DATABASE</td>
<td style="border:1px solid black;">0=använd nuvarande databas, 1=skapa databas</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">PROGRESS_WINDOW_HANDLE</td>
<td style="border:1px solid black;">Fönsterhandtag för att returnera MSI-förloppsmeddelanden</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">MU_ROLLUP</td>
<td style="border:1px solid black;">1=delta i Microsoft Update Improvement Program, 0=delta inte i Microsoft Update Improvement Program</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">FRONTEND_SETUP</td>
<td style="border:1px solid black;">1=skriv inte innehållsplatsen till databasen, 0=skriv innehållsplatsen till databasen (för NLB)</td>
</tr>
</tbody>
</table>
  
#### Användningsexempel
  
```  
WSUSSetup.exe /q DEFAULT\_WEBSITE=0 (install in quiet mode using port 8530) WSUSSetup.exe /q /u (uninstall WSUS)  
```  
| ![](images/Cc708525.Important(WS.10).gif)Viktigt!                                                                                                                                |  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om du installerar WSUS 3.0 SP1 i tyst läge (/q), och alla förutsättningar inte är installerade på datorn, då genererar installationen en fil som heter WSUSPreReqCheck.xml och sparar den i katalogen %TEMP%. |
  
Konfigurationsproblem  
---------------------
  
#### IIS startas om under installationen av WSUS 3.0 SP1
  
Installationsprogrammet för WSUS 3.0 SP1 startar om IIS utan meddelande. Det skulle kunna påverka befintliga webbplatser i organisationen. Om IIS inte körs startar installationsprogrammet för WSUS 3.0 SP1 det.
  
#### Installationen kan misslyckas om anslutningar öppnas till en befintlig WSUS-databas
  
Installationen kan misslyckas om du uppgraderar till WSUS 3.0 SP1 från en befintlig installation och anslutningar fortfarande är öppna till den befintliga WSUS-databasen (t.ex. om SQL Server Management Studio är öppet). Stäng alla anslutningar och installera WSUS 3.0 SP1 igen.
  
#### WSUS-installationen visar fel katalog för databasfiler
  
I WSUS-installationen rapporterar skärmen **Klar att installera** felaktigt att databasplatsen är den överordnade katalogen för databasplatsen. Standardplatsen är exempelvis %systemenhet%\\WSUS\\UpdateServicesDbFiles. Den här platsen visas dock felaktigt som %systemenhet%\\WSUS.
  
#### Om WSUS är installerat på en dator som har språkpaket för Multilingual User Interface med ett standardspråk som inte är engelska visas hjälpen på standardspråket i stället för på engelska
  
Om du har en dator med språkpaket för Multilingual User Interface med ett standardspråk som inte är engelska kan du ändå installera WSUS när användarens aktuella språk är engelska. Användargränssnittet visas på engelska. Du måste dock använda ett annat sätt att visa hjälpen på engelska på. Kopiera den engelskspråkiga hjälpens .chm-fil (*WSUSInstallDir*\\documentation\\mui\\0409\\WSUS30Help.chm) till huvuddokumentationskatalogen (*WSUSInstallDir*\\documentation\\WSUS30Help.chm). I det här läget bör hjälpen visas korrekt på alla språk.
  
Uppgraderingsproblem  
--------------------
  
#### Återställa från misslyckad uppgradering
  
Om du uppgraderar från en tidigare version av WSUS (WSUS 3.0, WSUS 2.0 SP1 eller WSUS 2.0) till WSUS 3.0 SP1 och uppgraderingen misslyckas av någon anledning:
  
1.  Installera tidigare WSUS-version igen.  
2.  Återställ databasen från den säkerhetskopia som du gjorde innan du provade uppgraderingen. (I flertalet fall skapar WSUS dessutom automatiskt en säkerhetskopia. Se WSUSSetup.log-filen för platsen.)  
3.  Gå igenom loggarna för att fastställa orsaken till felet och åtgärda problemet.  
4.  Försök uppgradera WSUS igen.
  
#### Det är inte möjligt att uppgradera från WSUS 2.0 till WSUS 3.0 SP1 om det finns en WSUS 3.0 SP1-databas från tidigare installation
  
Om du tidigare installerade WSUS 3.0 SP1, och sedan installerade WSUS 2.0 igen, då måste du ta bort WSUS 3.0 SP1-databasen på datorn innan du försöker installera WSUS 3.0 SP1 igen.
  
#### Om du ändrar datornamnet innan du uppgraderar till WSUS 3.0 SP1 kan uppgraderingen misslyckas
  
Om du ändrar datornamnet efter att ha installerat WSUS 2.0, och innan du uppgraderar till WSUS 3.0 SP1, kan uppgraderingen misslyckas.
  
Använd följande skript för att ta bort och återigen lägga till grupperna ASPNET och WSUS-administratörer. Kör sedan uppgraderingen igen.
  
Du måste ersätta *&lt;DBPlats&gt;* med mappen där databasen är installerad och *&lt;Innehållskatalog&gt;* med den lokala lagringsmappen.
  
```  
sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @asplogin varchar(200) SELECT @asplogin=name from sysusers WHERE name like '%ASPNET' EXEC sp\_revokedbaccess @asplogin" sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @wsusadminslogin varchar(200) SELECT @wsusadminslogin=name from sysusers WHERE name like '%WSUS Administrators' EXEC sp\_revokedbaccess @wsusadminslogin"   sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @asplogin varchar(200) SELECT @asplogin=HOST\_NAME()+'\\ASPNET' EXEC sp\_grantlogin @asplogin EXEC sp\_grantdbaccess @asplogin EXEC sp\_addrolemember webService,@asplogin" sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @wsusadminslogin varchar(200) SELECT @wsusadminslogin=HOST\_NAME()+'\\WSUS Administrators' EXEC sp\_grantlogin @wsusadminslogin EXEC sp\_grantdbaccess @wsusadminslogin EXEC sp\_addrolemember webService,@wsusadminslogin"   sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "backup database SUSDB to disk=N'*&lt;ContentDirectory&gt;*\\SUSDB.Dat' with init"  
```
  
#### Installationsprogrammet skriver över en tidigare säkerhetskopia av databasen
  
Installationsprogrammet för WSUS 3.0 SP1 lägger till databasen i standardkatalogen som är *enhet*\\WSUS (där *enhet* är den lokala NTFS-enhet som har störst mängd ledigt utrymme). Om det finns en säkerhetskopia av databasen i den här katalogen kan den skrivas över. Före uppgradering till WSUS 3.0 SP1 ska administratörer spara en säkerhetskopia av databasen för den aktuella versionen på en annan plats.
  
#### Om du har migrerat från MSDE till SQL Server 2000 eller SQL Server 2005 på WSUS 2.0 måste du ändra ett registervärde
  
Om du har en installation av WSUS 2.0, och har migrerat till SQL Server 2000 eller SQL Server 2005, måste du ändra värdet för **HKLM\\SOFTWARE\\Microsoft\\Update Services\\Server\\Setup\\WmsdeInstalled** från 1 till 0. Om du inte gör det innan du uppgraderar till WSUS 3.0 SP1 misslyckas uppgraderingen.
  
#### Om WSUS 2.0-installationen startas och avbryts tar den bort WSUS-registernyckeln
  
WSUS-registernyckeln tas bort om du startar installationsprogrammet för WSUS 2.0 och sedan avbryter det. Om du redan har installerat WSUS 3.0 SP1 kan detta orsaka problem. Samma problem uppstår om du börjar avinstallera WSUS 2.0 och sedan avbryter åtgärden, och sedan försöker uppgradera från WSUS 2.0 till WSUS 3.0 SP1.
  
#### Om du avinstallerar WSUS 3.0 SP1 och lämnar kvar loggfilerna kanske de inte har korrekt behörighet efter ominstallationen
  
När du avinstallerar WSUS 3.0 SP1 har du möjlighet att behålla installationens loggfiler. När du installerar WSUS 3.0 SP1 igen förlorar de gamla loggfilerna sin behörighet (vanligtvis endast för WSUS-administratörer). Återställ behörigheten på dessa loggfiler.
  
#### Om WSUS 2.0-klienter har uppdateringar med status Inte tillämpligt visas uppdateringarna som Okänt under en kort tid efter uppgradering till WSUS 3.0 SP1
  
Om en WSUS 2.0-server har klienter med uppdateringar av typ **Inte tillämpligt** verkar det som om dessa uppdateringar har status **Okänt** under en kort tid efter det att servern uppgraderats till WSUS 3.0 SP1. Uppdateringsstatus återgår till **Inte tillämpligt** efter nästa gång klienten utför en skanning.
  
Kända problem  
-------------
  
#### Felsöka flera hämtningsfel eller upprepade klientsynkroniseringsfel
  
Om WSUS 3.0 SP1-klienter rapporterar flera hämtningsfel, eller om klienter inte kan synkronisera med WSUS 3.0 SP1-servern under en längre tidsperiod, kanske du har ett skadat cacheminne för klienthämtning. Återställ från det här läget genom att försöka att ta bort cacheminnet för klienthämtning från filsystemet.
  
Ta bort cacheminnet för klienthämtning så här:
  
1.  Ta bort alla filer och underkataloger på det här platsen på klientdatorn: **%windir%\\SoftwareDistribution\\Download**  
2.  Försök installera uppdateringen genom att synkronisera klientdatorn med WSUS 3.0 SP1 igen. Det här installationsförsöket bör misslyckas med följande fel: **WU\_E\_DM\_NOTDOWNLOADED, "Uppdateringen har inte hämtats."**  
3.  Efter det här felet startar klientdatorn automatiskt om hämtningen och installationen kan fortsätta.
  
#### Om synkroniseringen misslyckas, pröva med att synkronisera igen
  
Om synkroniseringen misslyckas blir din första felsökningsåtgärd att försöka synkronisera servern igen. Om efterföljande synkroniseringar misslyckas, använd felsökningsinformationen i [Windows Server Update Services 3.0 Operations Guide](http://go.microsoft.com/fwlink/?linkid=81072) (http://go.microsoft.com/fwlink/?LinkId=81072).
  
#### Det går inte att ändra WSUS 3.0 SP1-konfigurationen direkt i databasen
  
Windows Server Update Services lagrar sina konfigurationsdata i en SQL Server-databas. Det går dock inte att ändra konfigurationsdata genom att nå databasen direkt. Försök inte modifiera WSUS 3.0 SP1-konfigurationen genom att nå databasen direkt. Du ska ändra WSUS 3.0 SP1-konfigurationen genom att använda WSUS 3.0 SP1-konsolen eller anropa API:er för WSUS 3.0 SP1.
  
#### Hämtningsfel rapporteras inte snabbt om diskkvoter är aktiverade
  
Om diskkvoter är aktiverade och kvoter nås kanske inte fel av typ uppdatera hämtning på WSUS-servern rapporteras på ett tidsenligt sätt. Undvik detta problem genom att inaktivera diskkvoter eller öka kvoter.
  
#### Om WSUS 3.0 SP1 distribueras med SSL kan klientdatorer misslyckas med felkod 0x8024400a
  
Klientdatorer kan ibland misslyckas med felkod 0x8024400a vid kommunikation med en WSUS 3.0 SP1-server som använder SSL. För en uppdatering som tar itu med det här problemet, gå till [KB 905422](http://go.microsoft.com/fwlink/?linkid=70593) (http://go.microsoft.com/fwlink/?LinkId=70593).
  
#### Domänkontot för WSUS-administratörer tas inte bort när WSUS avinstalleras
  
Gruppen WSUS-administratörer skapas som ett domänkonto (inte ett lokalt konto) på domänkontrollanter, vilket innebär att alla installationer som använder det här domänkontot skulle inaktiveras om kontot togs bort när WSUS avinstalleras. Därför gäller att avinstallationen av WSUS inte tar bort domänkontot WSUS-administratörer.
  
#### Om en underordnad server konverteras till en överordnad server måste uppdateringar för katalogplatser importeras igen
  
När du befordrar en underordnad server till en överordnad server måste du dessutom importera alla uppdateringar till katalogplatser igen. Annars kan inte platsen synkronisera de nya revisionerna för uppdateringar av katalogplatser till den här servern.
  
#### Om du använder IIS med SSL är okrypterad åtkomst fortfarande möjlig, såvida inte Kräv en säker kanal är markerat
  
Om du har konfigurerat IIS så att det använder SSL genom att installera ett certifikat är det fortfarande möjligt att nå platsen via okrypterat HTTP såvida inte alternativet **Kräv en säker kanal** är markerat. För mer information, se dokumentationen om [IIS](http://go.microsoft.com/fwlink/?linkid=98084) (http://go.microsoft.com/fwlink/?LinkId=98084).
  
#### Katalogplatsimport kan misslyckas utan läs-/skrivbehörighet till mappen %windir%\\TEMP
  
När du utför en katalogplatsimport gäller att om kontot Nätverkstjänst inte har läs/skriv-behörighet för mappen %windir%\\TEMP kan importen misslyckas med ett felmeddelande som det här: Servern kunde inte behandla begäran. ---&gt; Det gick inte att hitta filen: "C:\\WINDOWS\\TEMP\\*tempFilnamn*.dll".
  
#### Prestanda kan försämras vid synkronisering mellan WSUS 3.0 SP1 och underordnad replikserver som kör WSUS 2.0
  
Du kan erfara prestandaproblem om du installerar WSUS 3.0 SP1 på en överordnad server och försöker synkronisera med underordnad replikserver som kör WSUS 2.0. Ta itu med det här problemet genom att hänvisa till [KB 910847](http://go.microsoft.com/fwlink/?linkid=70669) (http://go.microsoft.com/fwlink/?LinkId=70669).
  
#### E-postmeddelandet misslyckas utan varning om e-postservern är nere eller inte går att nå
  
Om nätverkets e-postserver är offline misslyckas WSUS 3.0 SP1 med att skicka e-postmeddelanden i tysthet. Den skriver dock händelse 10052 (HealthCoreEmailNotificationRed) i händelseloggen.
  
#### Ändrade inställningar på överordnad server skickas inte omedelbart till den underordnade servern
  
När konfigurationen av den överordnade servern ändras kan det ta tid innan dessa konfigurationsändringar verkligen träder i kraft. Om du exempelvis ändrar en inställning på den överordnade servern genom att välja ett nytt språk och omedelbart utlöser en synkronisering på den underordnade servern sker inte förändringen. Istället skickas den till den underordnade servern vid nästa schemalagda synkronisering. Väntetiden ökar beroende på antalet uppdateringar som finns på den överordnade servern.
  
#### Avinstallationen av WSUS 3.0 SP1 avinstallerar inte databasinstansen
  
Om WSUS 3.0 SP1 avinstalleras, avinstalleras inte databasinstansen. Instansen kan delas av mer än ett program och om den tas bort leder det till att andra program inte längre fungerar.
  
Om det blir nödvändigt att avinstallera Windows Internal Database, avinstallerar följande kommandon programmet:
  
(på 32-bitars plattformar)
  
```  
msiexec /x {CEB5780F-1A70-44A9-850F-DE6C4F6AA8FB} callerid=ocsetup.exe  
```  
(på 64-bitars plattformar)
  
```  
msiexec /x {BDD79957-5801-4A2D-B09E-852E7FA64D01} callerid=ocsetup.exe  
```  
Om du vill avinstallera Windows Internal Database Service Pack 2 från Windows Server 2008 kan du göra det genom att använda Serverhanteraren.
  
Det gäller dock att borttagningen av programmet kanske inte tar bort standardfiler av typ .mdf och .ldf vilket leder till att en efterföljande WSUS 3.0 SP1-installation misslyckas. Du kan ta bort dessa filer från katalogen %windir%\\SYSMSI\\SSEE.
  
#### Om en underordnad server ändrar sin överordnade server rapporteras uppdateringar av status Okänt som Inte tillämpligt
  
Om en underordnad server börjar synkronisera från en annan överordnad server rapporteras uppdateringar som har en status som är **Okänt** som **Inte tillämpligt** på den nya överordnade servern. Detta läge är temporärt och korrigeras nästa gång den underordnade servern rapporterar dess status, efter det att dess klienter har synkroniserat med den.
  
#### Om guiden Serverrensning når tidsgränsen på en server när den körs på flera servrar från en fjärrkonsol förloras anslutningen till alla servrar
  
Det är möjligt att köra guiden Serverrensning på flera servrar från en enda fjärrkonsol. Dock gäller att om rensningsproceduren når tidsgränsen på en av servrarna förlorar konsolen sin anslutning till alla servrar. Inga data förloras men administratören måste återställa fjärranslutningen för var och en av servrarna.
  
#### Om du startar och stoppar anslutningen snabbt i följd leder det till felmeddelandet Inget synkroniseringsfel inträffade i konfigurationsguiden
  
När du konfigurerar WSUS måste du ansluta till den överordnade servern (antingen Microsoft Update-server eller intranätets överordnade server) för att kunna överföra grundläggande information om servern. Om du klickar på **Starta anslutning** och omedelbart klickar på **Avsluta anslutning** får du det felaktiga felmeddelandet Inget synkroniseringsfel inträffade.
  
WSUS 3.0 SP1 på Windows Server 2008  
-----------------------------------
  
#### Versioner som stöds
  
WSUS 3.0 SP1 stöder Windows Server 2008 i både 32-bitars- och 64-bitarsversioner.
  
#### Förutsättningar
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Krav</th>
<th style="border:1px solid black;" >Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Microsoft IIS (Internet Information Services)</td>
<td style="border:1px solid black;">Installera från operativsystemet. Se till att följande komponenter är aktiverade:
<ul>
<li>Windows-autentisering<br />
<br />
</li>
<li>Static Content<br />
<br />
</li>
<li>ASP.NET<br />
<br />
</li>
<li>6.0 Management Compatibility<br />
<br />
</li>
<li>6.0 IIS Metabase Compatibility<br />
<br />
</li>
</ul></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft .NET Framework Version 2.0 Redistributable Package (x86)</td>
<td style="border:1px solid black;">Behövs inte i Windows Server 2008. Det är redan installerat som del av operativsystemet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Management Console 3.0</td>
<td style="border:1px solid black;">Behövs inte i Windows Server 2008. Det är redan installerat som del av operativsystemet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft Report Viewer</td>
<td style="border:1px solid black;">Detta är en förutsättning för att kunna använda användargränssnittet i WSUS. Se Microsoft Report Viewer Redistributable 2005 på <a href="http://go.microsoft.com/fwlink/?linkid=70410">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70410).</td>
</tr>
</tbody>
</table>
  
#### Använda guiden Säkerhetskonfiguration
  
När du kör guiden Säkerhetskonfiguration i Windows Server 2008 kan du välja WSUS-rollen och aktivera dess beroenden. Kör guiden Säkerhetskonfiguration genom att klicka på **Start**, peka på **Administrationsverktyg** och klicka sedan på **Guiden Säkerhetskonfiguration**.
  
Det finns följande kända problem med att använda guiden Säkerhetskonfiguration tillsammans med WSUS-rollen:
  
-   **Tjänsten Windows Internal Database är aktiverad även om den inte kan användas av WSUS.** Du konfigurerar WSUS att använda en databas – antingen Windows Internal Database eller SQL Server-databas. Om WSUS installeras med SQL Server och du väljer rollen WSUS i guiden Säkerhetskonfiguration aktiveras tjänsten Windows Internal Database om den är installerad på datorn men ännu inte används av WSUS. Du måste inaktivera tjänsten Windows Internal Database om du använder SQL Server-databas i stället för Windows Internal Database.  
-   **Brandväggsregler för WSUS på en anpassad webbplats markeras inte som standard.** Om du installerar WSUS på en anpassad webbplats (port 8530 eller 8531) markeras inte de obligatoriska brandväggsreglerna automatiskt även om du väljer WSUS-rollen i guiden Säkerhetskonfiguration. Du ska aktivera lämpliga brandväggsregler för WSUS baserat på om SSL (Secure Sockets Layer) är konfigurerat för WSUS-servern.
  
WSUS 3.0 SP1 på Windows Small Business Server 2003  
--------------------------------------------------
  
#### Om IIS virtuella rot är begränsad till vissa IP-adresser eller domännamn kan inte WSUS 3.0 SP1-servern uppdateras automatiskt
  
Vissa Windows Small Business Server-installationer kan ha standardwebbplatsen för IIS konfigurerad för **IP-adress och domännamnsrestriktioner**. Om så är fallet kanske Windows Update-klienten på servern inte kan uppdateras automatiskt.
  
#### Installera WSUS 3.0 SP1 på Small Business Server – Integreringsproblem
  
-   Om Windows Small Business Server 2003 använder en ISA-proxyserver för att få åtkomst till Internet måste följande anges i användargränssnittet **Inställningar**: **proxyserverinställningar, proxyservernamn, port**.  
-   Om ISA använder Windows-autentisering ska autentiseringsuppgifter för proxyservern anges i formatet *DOMÄN*\\*användare* och användaren ska vara medlem i gruppen Internet-användare.
  
#### Om du har lagt till ett undernät i nätverket utan att använda Windows SBS-guiderna måste du utföra den här proceduren
  
Installationsproceduren för WSUS-servern installerar två IIS vroots på servern: SelfUpdate och ClientWebService. Installationsprogrammet placerar dessutom vissa filer under hemkatalogen på standardwebbplatsen (på port 80), vilket gör det möjligt att uppdatera klientdatorer automatiskt genom standardwebbplatsen. Standard är att standardwebbplatsen är konfigurerad att neka åtkomst till någon annan IP-adress än localhost eller till specifika undernät som är anslutna till servern. Resultatet blir att klientdatorer som inte finns på localhost eller på de specifika undernäten inte kan uppdateras automatiskt. Om du har lagt till ett undernät i nätverket utan att använda guiderna i Microsoft Windows Small Business Server 2003 (Windows SBS) måste du utföra den här proceduren
  
1.  I Serverhantering, expandera **Avancerad hantering**, expandera **Internet Information Services**, expandera **Webbplatser**, expandera **Standardwebbplats**, högerklicka på den virtuella katalogen **Selfupdate** och klicka sedan på **Egenskaper**.  
2.  Klicka på **Katalogsäkerhet**.  
3.  Klicka på **Redigera** under **IP-adress och domännamnsrestriktioner** och klicka sedan på **Beviljas åtkomst**.  
4.  Klicka på **OK**, högerklicka på den virtuella katalogen **ClientWebService** och klicka sedan på **Egenskaper**.  
5.  Klicka på **Katalogsäkerhet**.  
6.  Klicka på **Redigera** under **IP-adress och domännamnsrestriktioner** och klicka sedan på **Beviljas åtkomst**.
  
Upphovsrätt  
-----------
  
Innehållet i detta dokument, inklusive URL och andra hänvisningar till webbplatser på Internet, kan ändras utan föregående meddelande. Om inte annat anges är företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser som förekommer i exempel fiktiva. Ingen association med verkliga företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser eller händelser är avsedd. Det är användarens ansvar att följa alla gällande upphovsrättslagar. Utan att begränsa rättigheterna under upphovsrätten får ingen del av det här dokumentet reproduceras, lagras eller introduceras i ett arkivsystem eller överföras i någon form eller på något sätt (elektroniskt, mekaniskt, fotokopiering, inspelning eller annat), eller för något syfte, utan uttryckligt, skriftligt tillstånd från Microsoft Corporation.
  
Microsoft kan ha patent, patentansökningar, varumärken, upphovsrätter eller andra immateriella egendomsrättigheter som omfattar informationen i detta dokument. Förutom enligt vad som uttryckligen tillhandahålls i skriftligt licensavtal från Microsoft, ger tillhandahållandet av det här dokumentet inte dig någon licens till dessa patent, varumärken, upphovsrätter eller annan immateriell egendom.
  
© 2007 Microsoft Corporation. Med ensamrätt.
  
Microsoft, SQL Server, Windows och Windows Server är antingen registrerade varumärken eller varumärken som tillhör Microsoft Corporation i USA och/eller andra länder.
  
Alla andra varumärken är egendom som tillhör respektive ägare.
