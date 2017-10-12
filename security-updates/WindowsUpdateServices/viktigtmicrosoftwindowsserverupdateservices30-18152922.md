---
TOCTitle: 'Viktigt – Microsoft Windows Server Update Services 3.0'
Title: 'Viktigt – Microsoft Windows Server Update Services 3.0'
ms:assetid: '94d1385f-4872-4c29-8822-3a4ec5e45ae4'
ms:contentKeyID: 18152922
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708491(v=WS.10)'
---

Viktigt – Microsoft Windows Server Update Services 3.0
======================================================

I den här viktiga informationen beskrivs kända problem som påverkar Microsoft® Windows® Server Update Services 3.0 (WSUS 3.0) och här finns rekommendationer och krav för installation av programmet. Här ingår följande avsnitt:

-   Systemkrav vid serverinstallation av WSUS 3.0
-   Konfigurationskrav vid serverinstallation av WSUS 3.0
-   Systemkrav vid fjärrkonsolinstallation av WSUS 3.0
-   Konfigurationskrav för WSUS 3.0-fjärrkonsoler
-   Systemkrav vid klientinstallation
-   Programkrav vid serverinstallation av WSUS 3.0
-   Krav på diskutrymme vid serverinstallation av WSUS 3.0
-   Uppgraderingskrav för WSUS 3.0
-   Kommandoradsparametrar i installationsprogrammet
-   Problem vid installation och uppgradering
-   Kända problem
-   WSUS 3.0 på Windows Server® 2008
-   WSUS 3.0 i Windows Small Business Server 2003

| ![](images/Cc708491.note(WS.10).gif)Obs!                                                                                                                                        |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du kan hämta det här dokumentet på [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=71220) ([http://go.microsoft.com/fwlink/?LinkId=71220](http://go.microsoft.com/fwlink/?linkid=71220)). |

Viktigt konfigurationsproblem: Du måste skriva över proxyserverlösenordet i konfigurationsguiden
------------------------------------------------------------------------------------------------

Om du använder en proxyserver som kräver autentisering med användarnamn och lösenord kan du bli tvungen att skriva över proxyserverlösenordet för att uppdateringar ska synkroniseras när du kör konfigurationsguiden för WSUS-servern. Eftersom konfigurationsguiden startas automatiskt när installationen är klar kan det leda till synkroniseringsfel när du uppgraderar till WSUS 3.0 från en äldre version av WSUS.

Du kan undvika problemet genom att avbryta konfigurationsguiden efter uppgraderingen eller genom att ange proxylösenordet igen samtidigt som du kör konfigurationsguiden. Om du vill åtgärda felet efter att det har inträffat går du till **Uppdateringskälla och proxyserver** på sidan **Alternativ**, anger proxylösenordet på nytt och sparar inställningen.

Systemkrav vid serverinstallation av WSUS 3.0
---------------------------------------------

#### WSUS 3.0-servern kan installeras på Windows Server 2003 Service Pack 1 och Windows Server 2008

WSUS 3.0-servern kan installeras på Windows Server 2003 Service Pack 1 och Windows Server 2008.

#### Windows 2000 Server kan inte användas med WSUS 3.0-servrar

Operativsystemet Microsoft Windows® 2000 Server kan inte användas med WSUS 3.0-servrar.

#### WSUS 3.0 kan inte användas på servrar där Terminal Services körs

Du rekommenderas inte att köra WSUS 3.0 på servrar där Terminal Services körs även om det skulle gå. WSUS 3.0 kan inte köras på en server där Terminal Services körs i konfigurationer där SQL Server-implementering används. Eftersom alla fjärrstyrda anpassningsåtgärder (bland annat installation) på en Terminal Server-licensserver körs som systemkontot, och serverns systemkonto kanske inte har behörighet på den fjärrstyrda SQL-servern, kanske installationen misslyckas.

Konfigurationskrav vid serverinstallation av WSUS 3.0
-----------------------------------------------------

#### IIS måste vara installerat

För Microsoft Windows Server Update Services 3.0 krävs Internet Information Services (IIS), som inte installeras som standard i Microsoft Windows Server 2003 eller Windows Server 2008. Om du försöker installera WSUS 3.0 utan IIS visas ett felmeddelande i installationsprogrammet för Windows Server Update Services som talar om att IIS inte har installerats

#### Om du kör IIS i IIS 5.0-isoleringsläge misslyckas installationen

Om du har uppgraderat servern från Windows 2000 Server till Windows Server 2003 är det möjligt att IIS körs i IIS 5.0-kompatibilitetsläge. Det går även att aktivera IIS 5.0-isoleringsläge i IIS-hanteraren. Då misslyckas installationen. Du måste inaktivera IIS 5.0-isoleringsläget innan du installerar WSUS 3.0.

#### Om någon IIS-komponent är installerade i 32-bitars kompatibilitetsläge på en 64-bitars plattform, kanske WSUS 3.0-installationen misslyckas

Alla IIS-komponenter ska vara installerade i enhetligt läge på 64-bitars plattformar. Installationen kanske misslyckas om någon IIS-komponent är i 32-bitars kompatibilitetsläge.

#### Proxy-servrar måste ha stöd för HTTP och HTTPS

När du konfigurerar WSUS-huvudservern (WSUS-servern som uppdateras direkt från Microsoft Update) och om det ska finnas en proxyserver mellan WSUS-servern och Internet så måste proxyservern ha stöd för HTTP och HTTPS.

#### Om du redan kör två eller flera webbplatser på port 80 tar du bort alla utom en innan du installerar WSUS

Om du kör två eller flera webbplatser på port 80 (exempelvis Windows® SharePoint® Services) bör du ta bort alla utom en innan du installerar WSUS. Annars är det inte säkert att serverklienterna uppdateras automatiskt.

#### När du installerar WSUS 3.0 kanske du måste inaktivera antivirusprogrammen

När du installerar WSUS 3.0 kanske du måste inaktivera antivirusprogrammen innan du kan utföra installationen. När du har inaktiverat antivirusprogrammet måste du starta om datorn innan du installerar WSUS. Omstart av datorn förhindrar att filerna låses när installationsprogrammet måste komma åt dem. När installationen är klar måste du komma ihåg att aktivera antivirusprogrammet igen. Mer information om hur du inaktiverar och aktiverar antivirusprogrammet finns på respektive leverantörs webbplats.

| ![](images/Cc708491.Caution(WS.10).gif)Varning!                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Den här lösningen kan göra datorn och nätverket mer sårbart för attacker från skadliga program och virus. Vi rekommenderar inte den här lösningen, men förser dig ändå med den här informationen så att du kan använda lösningen efter eget omdöme. Du gör detta på egen risk. |

| ![](images/Cc708491.note(WS.10).gif)Obs!                                                                                                                                                           |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ett antivirusprogram skyddar datorer mot virus. Du ska inte hämta eller öppna filer från källor som du inte litar på, besöka webbplatser som du inte litar på eller öppna e-postbilagor när antivirusprogrammet är inaktiverat. |

#### För WSUS 3.0 krävs att alternativet för nästlade utlösare aktiveras i SQL Server

Alternativet för nästlade utlösare är som standard aktiverat men kan inaktiveras av SQL Server-administratören.

Om du planerar att använda en SQL Server-databas som arkiv för Windows Server Update Services-data måste SQL Server-administratören kontrollera att alternativet för nästlade utlösare är aktiverat på servern innan WSUS 3.0-administratören installerar WSUS 3.0 och anger databasen vid installationen.

Installationsprogrammet för WSUS 3.0 aktiverar alternativet RECURSIVE\_TRIGGERS vilket är ett databasspecifikt alternativ. Alternativet för nästlade utlösare aktiveras emellertid inte eftersom det är ett globalt serveralternativ.

Använd följande om du vill ta reda på om alternativet för nästlade utlösare är aktiverat:

**sp\_configure 'nested triggers'**

När du vill aktivera alternativet för nästlade utlösare i SQL Server kör du följande från en batchfil på datorn där SQL Server körs:

**sp\_configure 'nested triggers', 1**

**GO**

**RECONFIGURE**

**GO**

Om du inte har SQL Server Management Studio på servern kanske du vill köra SQL-skript från kommandoraden. Du kan hämta kommandoradsverktyget för Microsoft SQL Server 2005 från [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=70728) (http://go.microsoft.com/fwlink/?LinkId=70728). Du börjar genom att köra **sqlcmd**.

Om du vill köra SQL-skript mot en Windows Internal Database-databas måste du hämta SQL Native Client från samma sida.

#### Begränsningar och krav för fjärrstyrd SQL

Det fungerar mindre bra att köra databasprogramvara på en annan dator än den där resten av WSUS 3.0 är installerat. Det finns vissa krav som gäller vid konfiguration av en fjärrstyrd SQL-installation:

-   Det går inte att använda en server som konfigurerats som domänkontrollant för serverdatorn i ett fjärrstyrt SQL-par.
-   Du ska inte köra Terminal Server på klientdatorn i den fjärrstyrda SQL-installationen.
-   Du måste använda dig av Microsoft SQL Server 2005 Service Pack 1 eller senare (finns att hämta på [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=66143) (http://go.microsoft.com/fwlink/?LinkId=66143)) för databasprogram på serverdatorn om den körs med Windows Server 2003 och SQL Server 2005 Service Pack 2 om den körs med Windows Server® 2008.
-   Både klientdatorn och serverdatorn måste anslutas till en Active Directory-domän. Om de tillhör olika domäner måste du upprätta ett förtroende mellan domänerna innan du kan köra installationsprogrammet för WSUS.
-   Om du har installerat WSUS 2.0 på en fjärrkonfiguration av SQL och vill uppgradera till WSUS 3.0 måste du avinstallera WSUS 2.0 (med **Lägg till eller ta bort program** på Kontrollpanelen) på serverdatorn och se till att den befintliga databasen förblir intakt. Installera sedan SQL Server 2005 SP1 eller SP2 och uppgradera den befintliga databasen. Installera sedan WSUS 3.0 på klientdatorn.

#### Det går inte att installera WSUS när vissa förhandsversioner av Internet Explorer 7 plus Terminal Services redan är installerade

Installationsprogrammet för WSUS misslyckas när vissa versionskandidater av Internet Explorer 7 är installerade tillsammans med Terminal Services.

Systemkrav vid fjärrkonsolinstallation av WSUS 3.0
--------------------------------------------------

WSUS 3.0-fjärrkonsolen kan installeras på följande plattformar:

-   Windows Server 2008
-   Windows Vista®
-   Windows Server 2003 SP1
-   Windows XP SP2

Konfigurationskrav för WSUS 3.0-fjärrkonsoler
---------------------------------------------

#### Du bör ha en bredbandsanslutning mellan en fjärradministratörskonsol och en WSUS 3.0-server

Om du ansluter WSUS 3.0-servern till en fjärradministratörskonsol via smalbandig WAN-anslutning kan det uppstå prestandaproblem. Genom att filtrera uppdateringsvyer och datorvyer kan du begränsa antalet uppdateringar och datorer som visas, men du rekommenderas då att använda bredbandsanslutning mellan fjärradministratörskonsolen och WSUS 3.0-servrarna. Om du upplever prestandaproblem med fjärrkonsolen rekommenderas du att ansluta till servern med Terminal Server för fjärrhantering.

Systemkrav vid klientinstallation
---------------------------------

Automatiska uppdateringar är klientprogramvaran för WSUS. Den kan användas med WSUS i följande operativsystem:

-   Windows Vista
-   Windows Server 2008
-   Microsoft Windows Server 2003, alla utgåvor
-   Microsoft Windows XP Professional SP2
-   Microsoft Windows 2000 Professional SP4, Windows 2000 Server SP4 eller Windows 2000 Advanced Server med SP4

Programkrav vid serverinstallation av WSUS 3.0
----------------------------------------------

I följande tabell kan du se vilka program som krävs för Windows Server 2003-plattformar med SP1. Programvara som krävs för Windows Server 2008 tas upp i avsnittet som handlar om WSUS 3.0 på Windows Server 2008.

Kontrollera att WSUS 3.0-servern uppfyller de här kraven innan du kör installationsprogrammet för WSUS 3.0. Om någon av uppdateringarna kräver att datorn startas om när installationen har slutförts ska du starta om datorn innan du installerar WSUS 3.0.

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
<td style="border:1px solid black;">Microsoft Internet Information Services (IIS)</td>
<td style="border:1px solid black;">Installera från operativsystemet.
Se problem 1: IIS måste vara installerat.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft .NET Framework Version 2.0 Redistributable Package (x86)</td>
<td style="border:1px solid black;">Mer information finns i Microsoft .NET Framework Version 2.0 Redistributable Package (x86) på <a href="http://go.microsoft.com/fwlink/?linkid=68935">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=68935). När det gäller 64-bitars plattformar finns mer information i Microsoft .NET Framework Version 2.0 Redistributable Package (x64) på <a href="http://go.microsoft.com/fwlink/?linkid=70637">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70637).</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Management Console 3.0 för Windows Server 2003</td>
<td style="border:1px solid black;">Detta är ett krav för att använda gränssnittet i WSUS 3.0. Mer information finns i Microsoft Management Console 3.0 för Windows Server 2003 (KB907265) på on the <a href="http://go.microsoft.com/fwlink/?linkid=70412">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70412). När det gäller 64-bitars plattformar finns mer information i Microsoft Management Console 3.0 för Windows Server 2003 x64 Edition (KB907265) på <a href="http://go.microsoft.com/fwlink/?linkid=70638">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70638).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft Report Viewer</td>
<td style="border:1px solid black;">Detta är ett krav för att använda gränssnittet i WSUS 3.0. Mer information finns i Microsoft Report Viewer Redistributable 2005 på <a href="http://go.microsoft.com/fwlink/?linkid=70410">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70410).</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">SQL Server 2005 (valfri)</td>
<td style="border:1px solid black;">Windows Internal Database installeras om inte någon annan kompatibel version av SQL Server redan har installerats. Om du tänker använda en fullständig SQL Server-databas måste du använda SQL Server 2005 SP1 eller senare (finns att hämta på <a href="http://go.microsoft.com/fwlink/?linkid=66143">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=66143)) på Windows Server 2003 eller SQL Server 2005 SP2 (finns att hämta på <a href="http://go.microsoft.com/fwlink/?linkid=84823">Microsoft Download Center</a> på http://go.microsoft.com/fwlink/?LinkId=84823) på Windows Server 2008.</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc708491.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                         |  
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om du har installerat WSUS 2.0 och använder SQL Server 2000, SQL Server Desktop Engine 2000 eller någon annan SQL Server-databas som är äldre än SQL Server 2005 SP1 (eller SQL Server 2005 SP2 på Windows Server 2008) så installeras Windows® Internal Database när du kör installationsprogrammet för WSUS 3.0 och databasen migreras dit. |
  
Krav på diskutrymme vid installation av WSUS 3.0-servern  
--------------------------------------------------------
  
Här följer krav på diskutrymme för Windows Server Update Services:
  
-   1 GB på systempartitionen  
-   2 GB för den volym där databasfilerna ska lagras  
-   20 GB för den volym där innehåll ska lagras
  
| ![](images/Cc708491.Important(WS.10).gif)Viktigt!                                         |  
|------------------------------------------------------------------------------------------------------------------------|  
| Det går inte att installera WSUS 3.0 på komprimerade enheter. Kontrollera att enheten som du valt inte är komprimerad. |
  
Uppgraderingskrav för WSUS 3.0  
------------------------------
  
#### Kontrollera att WSUS-installationen körs på rätt sätt och säkerhetskopiera WSUS-databasen innan du uppgraderar
  
Om du uppgraderar till WSUS 3.0 från en tidigare version bör du kontrollera att den nuvarande installationen körs på rätt sätt och säkerhetskopiera WSUS-databasen innan du uppgraderar.
  
1.  Kontrollera om det nyligen har registrerats några fel i händelseloggarna, om det har uppstått problem mellan underordnade och överordnade servrar eller varit problem med klientrapportering. Åtgärda eventuella problem innan du går vidare.  
2.  Du kan bli tvungen att köra DBCC CHECKDB för att försäkra dig om att WSUS-databasen är indexerad på rätt sätt. Mer information om CHECKDB hittar du på [DBCC CHECKDB](http://go.microsoft.com/fwlink/?linkid=86948) (http://go.microsoft.com/fwlink/?LinkId=86948).  
3.  Säkerhetskopiera WSUS-databasen.
  
#### Software Update Services 1.0 ska vara avinstallerat
  
Installationen av WSUS 3.0 misslyckas om Software Update Services 1.0 är installerat på samma dator. Du måste avinstallera Software Update Services 1.0 innan du kan installera WSUS 3.0.
  
#### Uppgradering från en betaversion av WSUS 3.0 till RTM-versionen av WSUS 3.0 stöds inte, men uppgradering från RC-versionen till RTM-versionen tillåts
  
Om du har en betaversion av WSUS 3.0 installerad måste du avinstallera den och ta bort databasen innan du kan installera RTM-versionen av WSUS 3.0. Det går endast att uppgradera från RC-versionen till RTM-versionen.
  
#### Det går inte att uppgradera från WSUS 2.0 till WSUS 3.0 på ett 64-bitars operativsystem
  
WSUS 2.0 stöds inte på operativsystem med 64-bitar. Det går inte att uppgradera från WSUS 2.0 till WSUS 3.0 på operativsystem med 64-bitar.
  
Kommandoradsparametrar i installationsprogrammet  
------------------------------------------------
  
Du kan utföra obevakade installationer av WSUS 3.0 med hjälp av kommandoradsparametrar för WSUS. I tabellen nedan visas kommandoradsparametrarna för WSUS 3.0.
  
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
<td style="border:1px solid black;">Genomför tyst installation.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/u</strong></td>
<td style="border:1px solid black;">Avinstallera produkten. Avinstallera även Windows Internal Database-instansen om den har installerats.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/p</strong></td>
<td style="border:1px solid black;">Endast kontroll av krav. Produkten installeras inte men systemet kontrolleras och rapporter skapas om kraven inte uppfylls.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/?, /h</strong></td>
<td style="border:1px solid black;">Visa kommandoradsparametrar med respektive beskrivning.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/g</strong></td>
<td style="border:1px solid black;">Uppgradera från WSUS 2.0. Den enda giltiga parametern för det här alternativet är /q (tyst installation). Den enda giltiga egenskapen för det här alternativet är DEFAULT_WEBSITE.</td>
</tr>
</tbody>
</table>
  
I tabellen nedan visas kommandoradsegenskaper för WSUS 3.0.
  
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
<td style="border:1px solid black;">0 = innehåll lagras lokalt, 1 = värd på Microsoft Update</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">CONTENT_DIR</td>
<td style="border:1px solid black;">Sökväg till innehållskatalog. Standard är <em>WSUS_installationsenhet</em><strong>\WSUS\WSUSContent</strong> där <em>WSUS_installationsenhet</em> är den lokala enhet som har mest ledigt diskutrymme.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">WYUKON_DATA_DIR</td>
<td style="border:1px solid black;">Sökväg till Windows Internal Database-datakatalog.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">SQLINSTANCE_NAME</td>
<td style="border:1px solid black;">Namnet ska visas i formatet <em>Servernamn</em>\<em>SQL-instansnamn</em>. Använd %COMPUTERNAME%-miljövariabeln om databasinstansen är på den lokala datorn. Om en befintlig instans inte finns används %COMPUTERNAME%\WSUS som standard.</td>
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
<td style="border:1px solid black;">0=installera WSUS-servern, 1=installera endast konsolen</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">ENABLE_INVENTORY</td>
<td style="border:1px solid black;">0 = installera inte inventeringsfunktioner, 1 = installera inventeringsfunktioner</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DELETE_DATABASE</td>
<td style="border:1px solid black;">0 = behåll databas, 1 = ta bort databas</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">DELETE_CONTENT</td>
<td style="border:1px solid black;">0 = behåll innehållsfiler, 1 = ta bort innehållsfiler</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DELETE_LOGS</td>
<td style="border:1px solid black;">0=spara loggfiler, 1=ta bort loggfiler (används med parametern /u).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">CREATE_DATABASE</td>
<td style="border:1px solid black;">0=använd aktuell databas, 1=skapa databas</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">PROGRESS_WINDOW_HANDLE</td>
<td style="border:1px solid black;">Fönsterreferens för retur av MSI-förloppsmeddelanden</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">MU_ROLLUP</td>
<td style="border:1px solid black;">1=delta i Program för kvalitetsförbättring av Microsoft Update, 0=delta inte</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">FRONTEND_SETUP</td>
<td style="border:1px solid black;">1=skriv inte innehållsplatsen till databasen, 0=skriv innehållsplatsen till databasen (för NLB)</td>
</tr>
</tbody>
</table>
  
#### Exempel på användningsområden
  
```  
WSUSSetup.exe /q DEFAULT\_WEBSITE=0 (install in quiet mode using port 8530) WSUSSetup.exe /q /u (uninstall WSUS)  
```  
| ![](images/Cc708491.Important(WS.10).gif)Viktigt!                                                                                          |  
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om du installerar WSUS 3.0 i tyst läge (/q) och datorn inte har alla komponenter som krävs, skapas en fil med namnet WSUSPreReqCheck.xml som sparas i katalogen %TEMP%. |
  
Installationsproblem  
--------------------
  
#### IIS startas om när WSUS 3.0 installeras
  
Installationsprogrammet för WSUS 3.0 startar om IIS utan meddelande, vilket kan påverka organisationens befintliga webbplatser. Om IIS inte körs startas det med installationsprogrammet för WSUS 3.0.
  
#### Om det finns anslutningar öppna till en befintlig WSUS-databas misslyckas installationen
  
Om du uppgraderar till WSUS 3.0 från en befintlig installation och det finns anslutningar öppna till den befintliga WSUS-databasen (till exempel om SQL Server Management Studio är öppet), misslyckas installationen. Stäng alla anslutningar och installera om WSUS 3.0.
  
#### Installationsprogrammet för WSUS visar fel katalog för databasfiler
  
På skärmen **Installationen kan påbörjas** i installationsprogrammet för WSUS visas felaktigt att databasen ska placeras i den överordnade katalogen. Om standardplatsen är %systemdrive%\\WSUS\\UpdateServicesDbFiles, visas platsen t.ex. felaktigt som %systemdrive%\\WSUS.
  
#### Om WSUS har installerats på en dator som har MUI-språkpaket (Multilingual User Interface) med något annat standardspråk än engelska visas hjälpen på standardspråket i stället för på engelska
  
Om du använder en dator med MUI-språkpaket (Multilingual User Interface) med något annat standardspråk än engelska kan du installera WSUS så länge den aktuella användarens språkversion är engelska. Användargränssnittet visas på engelska men du måste använda en tillfällig lösning för att hjälpen ska visas på engelska. Kopiera chm-filen för den engelskspråkiga hjälpen (*WSUS\_installationskatalog*\\documentation\\mui\\0409\\WSUS30Help.chm) till huvudkatalogen för dokumentation (*WSUS\_installationskatalog*\\documentation\\WSUS30Help.chm). Nu bör hjälpen visas på rätt sätt på samtliga språk.
  
Uppgraderingsproblem  
--------------------
  
#### När du uppgraderar från WSUS 3.0 RC till WSUS 3.0 RTM tilldelas inte SSL-certifikatet till WSUS-webbplatsen
  
Vid uppgraderingen från WSUS 3.0 RC till WSUS 3.0 RTM tas WSUS-webbplatsen bort och återskapas sedan på nytt. Detta resulterar i att SSL-certifikatet inte längre tilldelas WSUS-webbplatsen. När du har genomfört uppgraderingen måste du därför tilldela certifikatet på nytt.
  
#### Återställa från en misslyckad uppgradering
  
Om du uppgraderar från WSUS 2.0 till WSUS 3.0 och uppgraderingen misslyckas av någon anledning, måste du installera om WSUS 2.0 och återställa dess databas från säkerhetskopian.
  
#### Det går inte att uppgradera från WSUS 2.0 till WSUS 3.0 om det finns en WSUS 3.0-databas från en tidigare installation
  
Om du tidigare har installerat WSUS 3.0 och sedan installerar om WSUS 2.0 måste du ta bort WSUS 3.0-databasen på datorn innan du försöker installera om WSUS 3.0.
  
#### Om datornamnet ändras innan uppgraderingen till WSUS 3.0 kan uppgraderingen misslyckas
  
Om du ändrar datornamnet efter att du installerat WSUS 2.0 och innan du uppgraderar till WSUS 3.0 kan uppgraderingen misslyckas.
  
Ta bort och lägg till grupperna ASPNET och WSUS-administratörer igen genom att använda följande skript. Kör sedan uppgraderingen igen.
  
Du måste ersätta *&lt;DBPlats&gt;* med mappen där databasen är installerad och *&lt;InnehållsKatalog&gt;* med den lokala lagringsmappen.
  
```  
sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @asplogin varchar(200) SELECT @asplogin=name from sysusers WHERE name like '%ASPNET' EXEC sp\_revokedbaccess @asplogin" sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @wsusadminslogin varchar(200) SELECT @wsusadminslogin=name from sysusers WHERE name like '%WSUS Administrators' EXEC sp\_revokedbaccess @wsusadminslogin"   sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @asplogin varchar(200) SELECT @asplogin=HOST\_NAME()+'\\ASPNET' EXEC sp\_grantlogin @asplogin EXEC sp\_grantdbaccess @asplogin EXEC sp\_addrolemember webService,@asplogin" sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @wsusadminslogin varchar(200) SELECT @wsusadminslogin=HOST\_NAME()+'\\WSUS Administrators' EXEC sp\_grantlogin @wsusadminslogin EXEC sp\_grantdbaccess @wsusadminslogin EXEC sp\_addrolemember webService,@wsusadminslogin"   sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "backup database SUSDB to disk=N'*&lt;ContentDirectory&gt;*\\SUSDB.Dat' with init"  
```
  
#### Installationsprogrammet kan skriva över en tidigare säkerhetskopia av databasen
  
Installationsprogrammet för WSUS 3.0 lägger till databasen i katalogen som anges under installationen. Standardplatsen är *%systemdrive%*\\WSUS\\UpdateServicesDbFiles. Om det finns en säkerhetskopia av en databas i katalogen skrivs den över med den nya databasen. Administratörer bör säkerhetskopiera databasfiler innan uppdateringar körs på datorn där databasen finns.
  
#### Om du har migrerat från MSDE till SQL Server 2000 eller SQL Server 2005 i WSUS 2.0 måste du ändra ett registervärde
  
Om du har installerat WSUS 2.0 och migrerat från SQL Server 2000 eller SQL Server 2005 måste du ändra värdet **HKLM\\SOFTWARE\\Microsoft\\Update Services\\Server\\Setup\\WmsdeInstalled** från 1 till 0. Om du inte gör det innan du uppgraderar till WSUS 3.0 kommer uppgraderingen att misslyckas.
  
#### Om installationsprogrammet för WSUS 2.0 startas och avbryts tas registernyckeln för WSUS bort.
  
Om du startar installationsprogrammet för WSUS 2.0 och avbryter det tas registernyckeln för WSUS bort. Det kan orsaka problem om WSUS 3.0 redan är installerad. Samma problem inträffar om du påbörjar avinstallationen av WSUS 2.0 och avbryter åtgärden och sedan försöker att uppgradera från WSUS 2.0 till WSUS 3.0.
  
#### Om du avinstallerar WSUS 3.0 och lämnar kvar loggfilerna kan de ha felaktiga behörighetsinställningar efter en ominstallation
  
Om du avinstallerar WSUS 3.0 kan du, om du vill, behålla installationsloggfilerna. När du installerar WSUS 3.0 igen förlorar de gamla loggfilerna sina behörighetsinställningar (oftast endast för WSUS-administratörer). Du bör återställa behörigheterna för loggfilerna.
  
#### Det går att uppgradera till WSUS 3.0 RTM även om Windows SharePoint Services installerades efter WSUS 3.0 RC
  
Om du installerade WSUS 3.0 RC och sedan installerade Windows SharePoint Services på samma dator så kan du endast uppgradera till WSUS 3.0 RTM om du väljer att installera på den anpassade porten (port 8530). Öppna kommandotolken och skriv följande kommando om du vill installera från kommandoraden: **WSUSSetup /q / g/ DEFAULT\_WEBSITE=0**. (Ange **WSUSSetup /g DEFAULT\_WEBSITE=0** om du vill installera med gränssnittet.)
  
Om WSUS har installerats på en dator med MUI-språkpaket (Multilingual User Interface) installerade visas hjälpen på standardspråket i stället för på det språk som den aktuella användaren har valt
  
#### Om WSUS 2.0-klienter har uppdateringar med status Inte tillämpliga markeras uppdateringarna som Okänd efter uppgraderingen till WSUS 3.0
  
Om en WSUS 2.0-server har klienter med uppdateringar som inte är tillämpliga markeras uppdateringarna med statusen Okänd under en kort stund efter att servern har uppgraderats till WSUS 3.0. Den uppdaterade statusen återgår till Inte tillämplig nästa gång klienten utför en sökning.
  
Kända problem  
-------------
  
#### Felsökning av flera fel eller upprepade klientsynkroniseringar misslyckas
  
Om WSUS 3.0-klienterna rapporterar flera hämtningsfel eller om klienterna misslyckas med att synkronisera med WSUS 3.0-servern under en längre tid kanske det beror på en skadad klientsammansättningscache. Du återställer detta genom att försöka ta bort sammansättningscachen från filsystemet.
  
Så här tar du bort en klientsammansättningscache:
  
1.  Ta bort alla filer och underkataloger på den här platsen på klientdatorn: **%windir%\\SoftwareDistribution\\Download**  
2.  Försök att installera uppdateringen genom att synkronisera klientdatorn med WSUS 3.0 igen. Det här installationsförsöket ska misslyckas och ett felmeddelande i stil med följande visas: **WU\_E\_DM\_NOTDOWNLOADED, "Uppdateringen har inte hämtats."**  
3.  Efter det här felet startar klienten automatiskt om hämtningen och installationen kan fortsätta.
  
#### Om synkroniseringen misslyckas försöker du igen
  
Om synkroniseringen misslyckas, ska den första felsökningsåtgärden vara att försöka synkronisera servern igen. Om efterföljande synkroniseringar misslyckas använder du felsökningsinformationen i [operatörshandboken till Windows Server Update Services 3.0](http://go.microsoft.com/fwlink/?linkid=81072) (http://go.microsoft.com/fwlink/?LinkId=81072).
  
#### Det går inte att ändra WSUS 3.0-konfigurationen direkt i databasen
  
I Windows Server Update Services lagras konfigurationsdata i en SQL Server-databas. Det går dock inte att ändra konfigurationsdata direkt i databasen. Försök inte att ändra WSUS 3.0-konfigurationen genom att komma åt databasen direkt. Du ska ändra WSUS 3.0-konfigurationen med hjälp av WSUS 3.0-konsolen eller anropa programmeringsgränssnitten i WSUS 3.0.
  
#### Hämtningsfel rapporteras långsamt om diskkvoter är aktiverade
  
Om diskkvoter är aktiverade och kvoten uppnås, kanske hämtningsfelen på WSUS-servern inte rapporteras tillräckligt snabbt. Du undviker detta genom att inaktivera diskkvoter eller öka kvoten.
  
#### Om WSUS 3.0 distribueras med hjälp av SSL kan klientdatorerna misslyckas med felkoden 0x8024400a
  
Klientdatorer kan ibland misslyckas med felkoden "0x8024400a" när de kommunicerar med en WSUS 3.0-server via SSL. En uppdatering som hanterar det problemet finns i [KB 905422](http://go.microsoft.com/fwlink/?linkid=70593) (http://go.microsoft.com/fwlink/?LinkId=70593).
  
#### Domänkontot för WSUS-administratörer tas inte bort när WSUS avinstalleras
  
Gruppen WSUS-administratörer skapas som ett domänkonto (inte ett lokalt konto) på domänkontrollanter, så alla installationer som använder det här domänkontot inaktiveras om kontot tas bort när WSUS avinstalleras. Därför tas inte kontot WSUS-administratörer bort när WSUS avinstalleras.
  
#### Om en underordnad server konverteras till en överordnad server måste uppdateringarna för katalogwebbplatsen importeras igen
  
När du omvandlar en underordnad server till en överordnad måste du också importera om alla uppdateringar för katalogwebbplatsen. Annars kan inte webbplatsen synkronisera nya uppdateringsändringar för katalogwebbplatsen till denna nya server.
  
#### Om du använder IIS med SSL är okrypterad åtkomst fortfarande möjlig såvida inte "Kräv en säker kanal" är markerat
  
Om du konfigurerar IIS till att använda SSL genom att installera ett certifikat, går det fortfarande att komma åt webbplatsen via okrypterad HTTP om inte alternativet "Kräv en säker kanal" är markerat. Mer information finns i [Enabling Encryption](http://go.microsoft.com/fwlink/?linkid=70601) (http://go.microsoft.com/fwlink/?LinkId=70601).
  
#### Importen till katalogwebbplatsen kanske misslyckas utan läs-/skrivbehörighet till mappen %windir%\\TEMP
  
När du importerar till en katalogwebbplats kanske importen misslyckas och ett felmeddelande i stil med följande visas om Network Service-kontot inte har läs-/skrivbehörighet till mappen %windir%\\TEMP: "Servern kunde inte behandla begäran." ---&gt; Det gick inte att hitta filen 'C:\\WINDOWS\\TEMP\\*TemporärtFilnamn*.dll'."
  
#### Det kan gå långsamt vid synkronisering mellan WSUS 3.0 och en underordnad replikserver som kör WSUS 2.0
  
Om du installerar WSUS 3.0 på en överordnad server och försöker att synkronisera med en underordnad replikserver som kör WSUS 2.0 kan det bli prestandaproblem. Information om hur du hanterar det problemet finns i [KB 910847](http://go.microsoft.com/fwlink/?linkid=70669) (http://go.microsoft.com/fwlink/?LinkId=70669).
  
#### Om e-postservern inte är aktiv eller inte kan nås misslyckas e-postaviseringar utan att detta meddelas
  
Om nätverkets e-postserver är offline går det inte att skicka e-postaviseringar, och du får inget meddelande om detta. Den skriver dock händelsen 10052 (HealthCoreEmailNotificationRed) i händelseloggen.
  
#### Ändrade inställningar på en överordnad server skickas inte omedelbart till den underordnade servern
  
När konfigurationen av den överordnade servern ändras kan det ta en stund innan dessa konfigurationsändringar träder i kraft. Om du ändrar en inställning på en överordnad server, till exempel väljer ett nytt språk, och omedelbart utlöser en synkronisering på den underordnade servern visas inte ändringen. Den skickas i stället till den underordnade servern vid nästa schemalagda synkronisering. Väntetiden ökar beroende på antalet uppdateringar som finns på den överordnade servern.
  
#### Avinstallation av WSUS 3.0 avinstallerar inte databasinstansen
  
Om WSUS 3.0 avinstalleras kommer databasinstansen inte att avinstalleras. Instansen kan delas av fler än ett program och kan orsaka att andra program misslyckas om den tas bort.
  
Om du behöver avinstallera Windows Internal Database, avinstalleras programmet med följande kommandon:
  
(på 32-bitars plattformar)
  
```  
msiexec /x {CEB5780F-1A70-44A9-850F-DE6C4F6AA8FB} callerid=ocsetup.exe  
```  
(på 64-bitars plattformar)
  
```  
msiexec /x {BDD79957-5801-4A2D-B09E-852E7FA64D01} callerid=ocsetup.exe  
```  
Du kan avinstallera Windows Internal Database Service Pack 2 från Windows Server 2008 med hjälp av Server Manager.
  
När programmet tas bort kanske det inte innebär att standardfilerna med filnamnstilläggen MDF och LDF tas bort, vilket gör att en efterföljande installation av WSUS 3.0 misslyckas. Dessa filer kan tas bort från katalogen %windir%\\SYSMSI\\SSEE.
  
#### Om en underordnad server ändrar sin överordnade server rapporteras "Okända" statusuppdateringar som "Inte tillämpliga"
  
Om en underordnad server börjar att synkronisera från en annan överordnad server kommer uppdateringar med status "Okänd" att rapporteras på den nya överordnade servern som "Inte tillämplig". Det här läget är tillfälligt och korrigeras nästa gång den underordnade servern rapporterar sin status, efter att dess klienter har synkroniserats med den.
  
#### Om en WSUS 3.0-replikserver hanterar fler än en dator med samma namn misslyckas rapporteringsinsamlingen
  
Om en WSUS 3.0-replikserver hanterar fler än en dator med samma namn misslyckas rapporteringsinsamlingen. De rapporter som finns på rot-WSUS-servern kanske därför är ofullständiga. Du löser det här problemet genom att ta bort alla dubblettposter utom en på replikservern.
  
#### Om guiden Serverrensning gör ett uppehåll på servern när den körs på flera servrar från en fjärrkonsol kopplas alla anslutningar till servern från
  
Det går att köra guiden Serverrensning på flera servrar från en enskild fjärrkonsol. Om rensningen gör ett uppehåll på någon av servrarna förlorar emellertid konsolen sin anslutning till alla servrar. Inga data förloras, men administratören måste återställa fjärranslutningen till var och en av servrarna.
  
#### Guiden Serverrensning tar bort filer efter 30 dagar, inte efter tre månader
  
En del av texten i guiden Serverrensning är felaktig. Den lyder: "Ta bort uppdateringar som har upphört att gälla och inte har godkänts på tre månader, och ta bort gamla revisioner av uppdateringar som inte har godkänts på tre månader." Det ska vara 30 dagar, inte tre månader.
  
#### Om anslutningen startas och stoppas i snabb följd visas ett "inget fel"-meddelande i konfigurationsguiden
  
När du konfigurerar WSUS måste du ansluta till den överordnade servern (antingen Microsoft Update eller den överordnade servern på intranätet) för att överföra grundläggande information om servern. Om du klickar på **Starta anslutning** och direkt efteråt klickar på **Avsluta anslutning** visas det felaktiga meddelandet "Inget synkroniseringsfel inträffade".
  
#### WSUS-klienter som använder Windows Vista RTM kan nu söka efter uppdateringar på Microsoft Update
  
Klienter som använder Windows Vista RTM i tidigare versioner av WSUS kunde endast få uppdateringar från WSUS-servern. Med WSUS 3.0 RTM så kan Vista-klienter också få uppdateringar från Microsoft Updates. Du kan peka Vista-klienter till Microsoft Update genom att öppna Windows Update från Kontrollpanelen och klicka på länken om **sökning online för uppdateringar från tjänsten Microsoft Update**. Om Grupprincipalternativet **Neka åtkomst till alla funktioner på Windows Update** är aktiverad visar inte Windows Update länken.
  
WSUS 3.0 på Windows Server 2008  
-------------------------------
  
#### Versioner som stöds
  
WSUS 3.0 stöder Windows Server 2008 i både 32-bitars- och 64-bitarsversioner.
  
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
<td style="border:1px solid black;">Microsoft Internet Information Services (IIS)</td>
<td style="border:1px solid black;">Installera från operativsystemet. Se till att följande komponenter är aktiverade:
Windows-autentisering
Static Content
ASP.NET
6.0 Management Compatibility
IIS Metabase Compatibility</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft .NET Framework Version 2.0 Redistributable Package (x86)</td>
<td style="border:1px solid black;">Behövs inte på Windows Server 2008 eftersom det redan är installerat som en del i operativsystemet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Management Console 3.0</td>
<td style="border:1px solid black;">Behövs inte på Windows Server 2008 eftersom det redan är installerat som en del i operativsystemet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft Report Viewer</td>
<td style="border:1px solid black;">Detta är ett krav för att använda gränssnittet i WSUS. Mer information finns i Microsoft Report Viewer Redistributable 2005 på <a href="http://go.microsoft.com/fwlink/?linkid=70410">Microsoft Download Center</a> (http://go.microsoft.com/fwlink/?LinkId=70410).</td>
</tr>
</tbody>
</table>
  
#### Problem 1: Konfigurationsfilen för IIS 7.0 måste uppdateras innan WSUS 3.0 körs
  
Konfigurationsfilen för IIS måste uppdateras innan WSUS 3.0 körs på Windows Server 2008. Du måste genomföra följande steg:
  
1. Öppna konfigurationsfilen för IIS: %WINDIR%\\system32\\inetsrv\\applicationhost.config
  
2. Ta bort &lt;add name="CustomErrorMode"&gt; i taggen &lt;System.webServer&gt;&lt;modules&gt; om den finns.
  
3. Lägg till &lt;add name="CustomErrorMode"&gt; i taggen &lt;System.webServer&gt;&lt;modules&gt;.
  
Taggen ska nu se ut på följande sätt:
  
```  
 &lt;System.webServer&gt; &lt;modules&gt; &lt;remove name="CustomErrorMode"&gt; &lt;/modules&gt; &lt;/System.webServer&gt;  
```
  
#### Problem 2: Om du vill installera WSUS 3.0 på den anpassade porten i Windows Server 2008 Beta 3 måste du skapa webbplatsen i förväg
  
Om du tänker installera WSUS 3.0 på Windows Server 2008 Beta 3 och vill konfigurera WSUS för användning via port 8530 måste du skapa webbplatsen WSUS Administration på port 8530 innan du startar installationsprogrammet för WSUS.
  
WSUS 3.0 i Windows Small Business Server 2003  
---------------------------------------------
  
#### Problem 1: Om den virtuella IIS-roten är begränsad till vissa IP-adresser eller domännamn kan WSUS 3.0-servern inte uppdateras automatiskt
  
Vissa installationer av Windows Small Business Server kan ha sin standard-IIS-webbplats konfigurerad för "IP-adress och domännamnsrestriktioner". Då kan kanske inte Windows Update-klienten uppdatera sig själv
  
#### Problem 2: Installera WSUS 3.0 på Small Business Server – integreringsproblem
  
-   Om Windows Small Business Server 2003 använder en ISA-proxyserver för åtkomst till Internet måste du skriva följande i användargränssnittet **Inställningar**: proxyserverinställningar, proxyservernamn och port.  
-   Om ISA använder Windows-autentisering ska proxyserverns referenser skrivas med formatet "DOMAIN\\användare" och användaren måste tillhöra gruppen Internet-användare.
  
#### Problem 3: Om du har lagt till ett undernät i nätverket utan att använda Windows SBS-guiderna måste du utföra den här proceduren
  
Under installationen av WSUS-servern installeras två IIS v-rötter på servern: SelfUpdate och ClientWebService. Under installationen placeras också vissa filer under standardwebbplatsens (på port 80) hemkatalog som gör det möjligt för klientdatorer att uppdateras automatiskt via standardwebbplatsen. Standardwebbplatsen konfigureras vanligtvis till att neka åtkomst till alla andra IP-adresser än localhost eller till vissa undernät som är kopplade till servern. Klientdatorer som inte finns på localhost eller dessa specifika undernät kan därför inte uppdateras automatiskt. Om du har lagt till ett undernät i nätverket utan att använda Windows SBS-guiderna (Microsoft Windows Small Business Server 2003) måste du utföra den här proceduren.
  
1.  Expandera **Avancerad hantering** i Serverhantering, expandera **Internet Information Services**, expandera **Webbplatser**, expandera **Standardwebbplats**, högerklicka på den virtuella katalogen **Selfupdate** och klicka sedan på **Egenskaper**.  
2.  Klicka på **Katalogsäkerhet**.  
3.  Klicka på **Redigera** under **IP-adress och domännamnsrestriktioner** och klicka sedan på **Beviljas åtkomst**.  
4.  Klicka på **OK**, högerklicka på den virtuella katalogen **ClientWebService** och klicka sedan på **Egenskaper**.  
5.  Klicka på **Katalogsäkerhet**.  
6.  Klicka på **Redigera** under **IP-adress och domännamnsrestriktioner** och klicka sedan på **Beviljas åtkomst**.
  
#### Upphovsrätt
  
Det här dokumentet gäller för en preliminär utgåva av en programprodukt som kan komma att ändras betydligt före den slutliga, kommersiella versionen, och innehåller konfidentiell information som tillhör Microsoft Corporation. Informationen tillhandahålls enligt en överenskommelse mellan mottagare och Microsoft om att inte avslöja informationen. Dokumentet ska bara användas i informationssyfte och Microsoft utfäster inga garantier, varken uttryckligen eller underförstått, i detta dokument. Informationen i det här dokumentet, bland annat URL:er och andra referenser till webbplatser, kan ändras utan föregående meddelande. Hela risken för användningen eller resultatet från användningen av det här dokumentet ligger hos användaren. Såvida inte annat anges är alla företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser som förekommer i exemplen fiktiva. Alla likheter med verkliga företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser eller händelser är oavsiktliga. Ansvaret för att upphovsrättslagar följs ligger på användaren. Ingen del av det här dokumentet får reproduceras, lagras eller infogas i ett informationssystem eller överföras i någon form, med något medel (elektroniska eller mekaniska medier, fotokopiering, inspelning eller någon annan form av reproduktion) eller för något ändamål utan uttrycklig skriftlig tillåtelse från Microsoft Corporation.
  
För innehållet i detta dokument kan Microsoft inneha patent, patentansökningar, varumärken, copyright eller andra rättigheter som regleras av upphovsrättslagar. Innehav av detta dokument medför inga rättigheter till patent, varumärken, copyright eller andra upphovsrättsskyddade produkter utöver vad som uttryckligen anges i ett skriftligt licensavtal med Microsoft.
  
© 2007 Microsoft Corporation. Med ensamrätt.
  
Microsoft, MS-DOS, Windows och Windows NT är antingen registrerade varumärken eller varumärken som tillhör Microsoft Corporation i USA och/eller i andra länder.
  
Alla andra varumärken tillhör respektive ägare.
