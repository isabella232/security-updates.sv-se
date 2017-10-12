---
TOCTitle: 'Windows Server Update Services 3.0 SP2 Viktigt'
Title: 'Windows Server Update Services 3.0 SP2 Viktigt'
ms:assetid: 'b3723422-489d-47b7-abfa-663353647da0'
ms:contentKeyID: 21799681
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939886(v=WS.10)'
---

Windows Server Update Services 3.0 SP2 Viktigt
==============================================

Det här dokumentet beskriver den nya versionen av Windows Server Update Services 3.0 Service Pack 2 (WSUS 3.0 SP2). Dokumentet innehåller följande avsnitt:

1.  Nyheter i den här versionen
2.  Systemkrav för serverinstallation av WSUS 3.0 SP2
3.  Förutsättningar för konfigurering och bästa tillvägagångssätt för WSUS Server
4.  Förutsättningar för Windows Small Business Server
5.  Systemkrav för fjärrkonsolinstallation av WSUS 3.0 SP2
6.  Systemkrav för klientinstallation
7.  Krav och rekommendationer vid uppgradering
8.  Installera WSUS 3.0 SP2
9.  Kommandoradsparametrar för obevakade WSUS 3.0 SP2-installationer
10. Kända problem

Nyheter i den här versionen
---------------------------

-   Integrering med Windows Server 2008 R2.
-   Stöd för funktionen BranchCache i Windows Server 2008 R2.
-   Stöd för Windows 7-klienter.
-   Förbättringar av WUA-klienten (Windows Update Agent). Den nya WUA-klienten innehåller flera prestandaförbättringar, användarvänligare och en rad felkorrigeringar som baseras på kundernas synpunkter.
    -   Genomsökningstiden är snabbare än i tidigare versioner av klienten.
    -   Nu går det att köra begränsade genomsökningar på datorer som hanteras med WSUS-servrar.  Detta ger mycket snabbare genomsökningar i program där Microsoft Update-API:er används, t.ex Windows Defender.
    -   Förbättringen av användarfunktionerna i WUA (Windows Update Agent) gör det enklare för användaren att ordna uppdateringar ger bättre överblick över funktioner och information om uppdateringarna.
    -   Avbildade datorer visas tydligare i WSUS-konsolen. Det finns mer information i artikeln [En Windows 2000-baserad, Windows Server 2003-baserad eller Windows XP-baserad dator som har installerats med en Windows 2000-, Windows Server 2003- eller ,Windows XP-avbildning visas inte i WSUS-konsolen](http://go.microsoft.com/fwlink/?linkid=159749).
-   Nya funktioner:
    -   Reglerna för automatiskt godkännande inbegriper möjligheten att ange senaste datum och tid för godkännande för alla datorer eller för specifika datorgrupper.
    -   Den förbättrade hanteringen av språkval för underordnade servrar inbegriper en ny varningsdialogruta som visas när du bestämmer dig för att bara hämta uppdateringar för angivna språk.
    -   Med de nya uppdaterings- och datorstatusrapporterna kan du filtrera efter uppdateringar som har godkänts för installation. Du kan köra rapporterna från WSUS-konsolen eller använda programmeringsgränssnittet (API) för att implementera funktionen i dina egna rapporter.
-   Användargränssnittet är kompatibelt mellan Service Pack 1 och Service Pack 2 till WSUS 3.0 på både klient och server.
-   Programvaruuppdateringar.
-   Kända problem med Windows Update Agent som har åtgärdats i den här versionen:
    1.  WSUS 3.0 SP2 och Windows 7 innehåller en ny version av Windows Update Agent (för Windows XP, Windows Vista, Windows Server 2000, Windows Server 2003 och Windows Server 2008). I den här versionen har följande problem korrigerats: Programmeringsgränssnitt som anropas av icke-lokala systemprocedurer i en icke-interaktiv session misslyckas.
    2.  Problemet korrigeras i version 7.2.6001.788 av Windows Update Agent. Den här uppdateringen korrigerar följande problem: Vid försök att installera 80 eller fler uppdateringar samtidigt från webbsidan Windows Update eller Microsoft Update kan det hända att felkoden 0x80070057 visas.
    3.  Förbättringar och problem som korrigeras i version 7.2.6001.784 av Windows Update Agent. Den här uppdateringen innehåller följande: Förbättrar genomsökningstiden för Windows Update, förbättrar hastigheten vid uppdatering och leverans av signaturer, innehåller stöd för ominstallation med Windows-installationsprogrammet samt förbättrar visning av felmeddelanden.

<span id="BKMK_SysReqWSUS30SP2"></span>
Systemkrav för serverinstallation av WSUS 3.0 SP2
-------------------------------------------------

Det här avsnittet beskriver program- och maskinvarukraven för installation av WSUS 3.0 SP2.

### Programvarukrav för WSUS-server

-   Ett av följande operativsystem som stöds måste vara installerat:
    -   Windows Server 2008 R2
    -   Windows Server 2008 SP1 eller senare
 
        <table style="border:1px solid black;">
        <colgroup>
        <col width="100%" />
        </colgroup>
        <thead>
        <tr class="header">
        <th style="border:1px solid black;" ><img src="images/Dd939886.Warning(WS.10).gif" />Varning</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td style="border:1px solid black;">Om WSUS 3.0 SP2 installeras i Windows Server 2008 före uppgradering till Windows Server 2008 R2, kommer uppgraderingen till Windows Server 2008 R2 att misslyckas. Det finns mer information i avsnittet <a href="#bkmk_knownissues">Kända problem</a>.
        </td>
        </tr>
        </tbody>
        </table>
 

    -   Windows Server 2003 SP1 eller senare
    -   Windows Small Business Server 2008
    -   Windows Small Business Server 2003

    Observera att ytterligare förutsättningar gäller för Windows Small Business Server. Mer information finns i avsnittet "Förutsättningar för Windows Small Business Server".
-   Internet Information Services (IIS) 6.0 och senare
-   Microsoft .NET Framework 2.0 eller senare
-   Ett av följande databasprogram som stöds måste vara installerat:
    -   Microsoft SQL Server 2008 Standard eller Enterprise Edition
    -   Microsoft SQL Server 2005 SP3 och senare
    -   Windows Internal Database

    Om ingen de tillåtna versionerna av SQL Server har installerats, installerar installationsguiden i WSUS 3.0 SP2 Windows Internal Database.
-   Microsoft Management Console 3.0
-   Microsoft Report Viewer Redistributable 2008

 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939886.Important(WS.10).gif" />Viktigt</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Windows Server 2008 R2 kräver WSUS 3.0 SP2. Om du installerar Windows Server 2008 R2 bör du installera WSUS 3.0 SP2. Installera inte WSUS 3.0 SP1 i Windows Server 2008 R2.

WSUS 3.0 SP2 stöds inte för användning med Terminal Services på frontend-servern i en SQL-fjärrkonfiguration.
</td>
</tr>
</tbody>
</table>
 

### Programvarukrav för WSUS-administratörskonsol

-   Ett av följande tillåtna operativsystem: Windows Server 2008 R2, Windows Server 2008, Windows Server 2003 SP2 och senare, Windows Small Business Server 2008 eller Windows Small Business Server 2003, Windows Vista eller Windows XP SP2
-   Microsoft .NET Framework 2.0 eller senare
-   Microsoft Management Console 3.0
-   Microsoft Report Viewer Redistributable 2008

### Maskinvarukrav för WSUS-server

Följande lista innehåller systemkraven för en grundläggande serverinstallation. Det finns en heltäckande lista med maskinvarukonfigurationer som stöds i distributionsguiden för WSUS 3.0 SP2 på [http://go.microsoft.com/fwlink/?LinkId=139832](http://go.microsoft.com/fwlink/?linkid=139832).

-   Både systempartitionen och den partition där WSUS 3.0 SP2 installeras måste vara NTFS-formaterade.
-   Minst 1 GB ledigt utrymme på systempartitionen
-   Minst 2 GB ledigt utrymme på den volym där databasfilerna lagras.
-   Minst 20 GB ledigt utrymme krävs på den volym där innehållet lagras, 30 GB rekommenderas.

 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939886.Important(WS.10).gif" />Viktigt</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">WSUS 3.0 SP2 kan inte installeras på komprimerade enheter.
</td>
</tr>
</tbody>
</table>
 

Förutsättningar för konfigurering och bästa tillvägagångssätt för WSUS Server
-----------------------------------------------------------------------------

Kontrollera att du har slutfört nödvändiga uppgifter i det här avsnittet innan du installerar WSUS 3.0 SP2.

### IIS

-   Installera alla önskade funktioner, alla IIS-standardrolltjänster och följande rolltjänster på rolltjänstsidan för webbserverhanteraren (IIS): **ASP.NET**, **Windows-autentisering**, **Komprimering av dynamiskt innehåll** och **IIS 6-hanteringskompatibilitet**.
-   Om IIS körs i IIS 5.0-isoleringsläge misslyckas installationen. Inaktivera IIS 5.0-isoleringsläget innan du installerar WSUS 3.0 SP2.
-   Om någon IIS-komponent är installerad i 32-bitars kompatibilitetsläge på en 64-bitars plattform, kanske installationen av WSUS 3.0 SP2 misslyckas. Alla IIS-komponenter ska vara installerade i enhetligt läge på 64-bitars plattformar.

### Proxyservrar

Med WSUS 3.0 SP2 tillåts endast proxyserver med stöd för HTTP. Du rekommenderas att konfigurera en sekundär proxyserver som kör HTTPS med kommandoraden (**wsusutil configuresslproxy**) innan du konfigurerar WSUS-servern från konfigurationsguiden eller administratörskonsolen.

### Webbplatser som körs på port 80

Om du har två eller flera webbplatser som körs på port 80 (exempelvis Windows SharePoint Services) bör du ta bort alla utom en innan du installerar WSUS. I annat fall kan det hända att serverns klienter inte kan uppdateras automatiskt.

### Antivirusprogram

När du installerar WSUS 3.0 SP2 kanske du måste inaktivera antivirusprogrammen innan du kan utföra installationen. När du har inaktiverat antivirusprogrammet måste du starta om datorn innan du installerar WSUS. Omstart av datorn förhindrar att filerna låses när installationsprogrammet måste komma åt dem. När installationen är klar måste du komma ihåg att aktivera antivirusprogrammet igen. Mer information om hur du inaktiverar och aktiverar antivirusprogrammet finns på respektive leverantörs webbplats.

 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939886.Caution(WS.10).gif" />Varning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Den här lösningen kan göra datorn och nätverket mer sårbart för attacker från skadliga program och virus. Vi rekommenderar inte den här lösningen, men förser dig ändå med den här informationen så att du kan använda lösningen efter eget omdöme. Du gör detta på egen risk.

Antivirusprogram bidrar till att skydda datorn från virus. Hämta inte och öppna inte filer från källor som du inte litar på, besök inte webbplatser som du inte litar på och öppna inte e-postbilagor när antivirusprogrammet är inaktiverat.
</td>
</tr>
</tbody>
</table>
 

### Alternativ för nästlade utlösare i SQL Server

Om du planerar att använda en SQL Server-databas som arkiv för Windows Server Update Services-data måste SQL Server-administratören kontrollera att alternativet för nästlade utlösare är aktiverat på servern innan WSUS-administratören installerar WSUS 3.0 SP2. Alternativet för nästlade utlösare är som standard aktiverat men kan inaktiveras av SQL Server-administratören. Installationsprogrammet till WSUS 3.0 SP2 aktiverar alternativet RECURSIVE\_TRIGGERS, som är databasspecifikt. Installationsprogrammet till WSUS 3.0 SP2 aktiverar emellertid inte alternativet för nästlade utlösare, som tillämpas på hela servern.

### Begränsningar och krav för fjärrstyrd SQL

Med WSUS 3.0 SP2 är det möjligt att köra en kompatibel version av SQL Server på en annan dator än den där programmet WSUS 3.0 SP2 körs. Följande krav avser en fjärrinstallation av SQL.

-   Du kan inte använda en server som är konfigurerad som en domänkontrollant som backend i fjärr-SQL-paret.
-   Det går inte att köra Terminal Services på den dator som ska fungera som frontend-server i en fjärrinstallation av SQL.
-   Både frontend- och backend-datorn måste vara kopplade till en Active Directory-domän. Om frontend- och backend-datorerna tillhör olika domäner måste domänerna vara betrodda i den andra domänen innan du installerar WSUS.
-   Om WSUS 2.0 redan har installerats i en fjärrstyrd SQL-konfiguration och du vill uppgradera till WSUS 3.0 SP2, måste du göra följande innan du installerar WSUS:
    1.  Avinstallera WSUS 2.0 (med hjälp av **Lägg till eller ta bort program** i Kontrollpanelen) och försäkra dig om att den befintliga databasen förblir oförändrad.
    2.  Installera SQL Server 2005 SP2 eller SQL Server 2008 och uppgradera den befintliga databasen.

### IIS startas om när WSUS 3.0 SP2 installeras

IIS startas om utan meddelande i installationsprogrammet för WSUS 3.0 SP2, vilket kan påverka befintliga webbplatser. Du rekommenderas att meddela de användare som påverkar före installationen. Observera att IIS startas under installationen av WSUS 3.0 SP2 om IIS inte körs.

Förutsättningar för Windows Small Business Server
-------------------------------------------------

När WSUS 3.0 SP2 installeras i Windows Small Business Server gäller följande förutsättningar.

### Om den virtuella IIS-roten är begränsad till vissa IP-adresser eller domännamn

Vissa installationer av Windows Small Business Server kan ha sin standard-IIS-webbplats konfigurerad för **IP-adress och domännamnsrestriktioner**. I så fall kan det hända att Windows Update-klienten på servern inte kan uppdateras automatiskt. Avlägsna begränsningen innan du installerar WSUS 3.0 SP2.

### Om du använder en ISA-proxyserver

-   Om en ISA-proxyserver används för Internet-åtkomst i Windows Small Business Server måste du ange **proxyserverinställningar, proxyservernamn och port** i **Inställningar**.
-   Om ISA använder Windows-autentisering måste uppgifterna om proxyservern anges med formatet *DOMÄN*\\*användare*. Användaren måste vara medlem i gruppen Internet-användare.

### Om du har lagt till ett undernät i nätverket utan att använda Windows Small Business Server-guider

Under installationen av WSUS-servern installeras två IIS v-rötter på servern: SelfUpdate och ClientWebService. Under installationen placeras också vissa filer under standardwebbplatsens rotkatalog (på port 80) som gör det möjligt för klientdatorer att uppdateras automatiskt via standardwebbplatsen. Standardwebbplatsen konfigureras vanligtvis till att neka åtkomst till alla andra IP-adresser än localhost eller till vissa undernät som är kopplade till servern. Klientdatorer som inte finns på localhost eller dessa specifika undernät kan därför inte uppdateras automatiskt. Gör så här om du har lagt till ett undernät i nätverket utan att använda Microsoft Windows Small Business Server-guider:

1.  Expandera **Avancerad hantering** i Serverhantering, expandera **Internet Information Services**, expandera **Webbplatser**, expandera **Standardwebbplats**, högerklicka på den virtuella katalogen **Selfupdate** och klicka sedan på **Egenskaper**.
2.  Klicka på **Katalogsäkerhet**.
3.  Klicka på **Redigera** under **IP-adress och domännamnsrestriktioner** och klicka sedan på **Beviljas åtkomst**.
4.  Klicka på **OK**, högerklicka på den virtuella katalogen **ClientWebService** och klicka sedan på **Egenskaper**.
5.  Klicka på **Katalogsäkerhet**.
6.  Klicka på **Redigera** under **IP-adress och domännamnsrestriktioner** och klicka sedan på **Beviljas åtkomst**.

Systemkrav för fjärrkonsolinstallation av WSUS 3.0 SP2
------------------------------------------------------

Fjärrkonsolen till WSUS 3.0 SP2 kan installeras på något av följande operativsystem:

-   Windows Server 2008 R2, Windows Server 2008 SP1 eller senare versioner, Windows Server 2003 SP2 eller senare versioner, Windows Small Business Server 2003, Windows Small Business Server 2005 eller Windows Small Business Server 2008, Windows Vista eller Windows XP Professional SP3 eller senare versioner.

Systemkrav för installation av WSUS-klient
------------------------------------------

WSUS-klientprogramvaran för automatiska uppdateringar kan installeras på något av följande operativsystem:

-   Windows Server 2008 R2, Windows Server 2008 SP1 eller senare versioner, Windows Server 2003 SP2 eller senare versioner, Windows Small Business Server 2003, Windows Small Business Server 2005 eller Windows Small Business Server 2008, Windows Vista, Windows XP Professional RTM, Windows XP Professional SP1, Windows XP Professional SP2, Windows XP Professional SP3 eller senare versioner, Windows 2000 SP4 eller Windows 7-klient.

Krav och rekommendationer vid uppgradering
------------------------------------------

Följande versioner av WSUS kan uppgraderas till WSUS 3.0 SP2 och kräver inte att den tidigare versionen avinstalleras:

-   WSUS 2.0, 2.0 SP1, 3.0 och 3.0 SP1.

Det går inte att uppgradera från WSUS 1.0 till WSUS 3.0 SP2. Avinstallera SUS 1.0 (Software Update Services) innan du installerar WSUS 3.0 SP2.

Windows Server 2008 R2 kräver WSUS 3.0 SP2. Om du installerar Windows Server 2008 R2 bör du installera WSUS 3.0 SP2. Installera inte WSUS 3.0 SP1 i Windows Server 2008 R2.

#### Innan du uppgraderar till WSUS 3.0 SP2

1.  Kontrollera eventuella nya fel i händelseloggarna, problem med synkroniseringen mellan underordnade och överordnade servrar samt problem med klientrapporter. Åtgärda eventuella problem innan du uppgraderar.

2.  Alternativt kan du köra DBCC CHECKDB för att kontrollera att WSUS-databasen har indexerats korrekt. Mer information om DBCC CHECKDB finns i [DBCC CHECKDB](http://go.microsoft.com/fwlink/?linkid=86948).

3.  Säkerhetskopiera WSUS-databasen. Observera att den nya databasen läggs till i standardkatalogen *enhet*\\WSUS (*enhet* är den lokala NTFS-enhet med mest ledigt utrymme) i installationsprogrammet för WSUS 3.0 SP2. Om det redan finns en säkerhetskopia av databasen i katalogen kan den komma att skrivas över. Du rekommenderas att spara en säkerhetskopia av databasen i den befintliga versionen av WSUS på en annan plats innan du uppgraderar till WSUS 3.0 SP2.

4.  Om du manuellt har ändrat den port som används av WSUS (det vill säga om du inte använde verktyget Wsusutil) och kör Software Update Services 1.0 eller WSUS 2.0, bör du öppna standardwebbplatsen innan du avinstallerar SUS 1.0 eller 64-bitarsversionen av WSUS 2.0.

5.  Om det finns öppna anslutningar till en befintlig WSUS-databas (till exempel om SQL Server Management Studio har öppnats) kan installationen misslyckas. Stäng alla anslutningar innan du installerar WSUS 3.0 SP2.

### Återställa från en misslyckad uppgradering

Gör så här om du uppgraderar från en tidigare version av WSUS till WSUS 3.0 SP2 och uppgraderingen misslyckas (av en annan orsak än att du försöker utföra en otillåten uppgradering från SUS 1.0).

1.  Installera om den tidigare versionen av WSUS.
2.  Återställ databasen från den säkerhetskopia som du gjorde tidigare innan du försöker uppgradera. Uppgraderingen slutförs inte korrekt om det finns en befintlig WSUS 3.0 SP2-databas från en tidigare installation. I de flesta fall skapas dessutom en automatisk säkerhetskopia. Platsen för säkerhetskopian anges i filen WSUSSetup.log.
3.  Läs i loggarna för information om felorsaken och åtgärda problemet.
4.  Installera WSUS 3.0 SP2.

### Om datornamnet ändras före uppgraderingen till WSUS 3.0 SP2 kan uppgraderingen misslyckas

Om du ändrar datornamnet efter installationen av WSUS 2.0 och innan uppgraderingen till WSUS 3.0 SP2 kan uppgraderingen misslyckas.

Ta bort och lägg till grupperna ASPNET och WSUS-administratörer igen genom att använda följande skript. Kör sedan uppgraderingen igen.

        ```

### Om du har migrerat från MSDE till SQL Server 2008 eller SQL Server 2005 på WSUS 2.0 måste du ändra ett registervärde

Om du har en installation av WSUS 2.0 och har migrerat till SQL Server 2008 eller SQL Server 2005 måste du ändra värdet i **HKLM\\SOFTWARE\\Microsoft\\Update Services\\Server\\Setup\\WmsdeInstalled** från 1 till 0. Om du inte gör detta innan du uppgraderar till WSUS 3.0 SP2 kommer uppgraderingen att misslyckas.

### Om du avinstallerar WSUS 3.0 SP2 och lämnar kvar loggfilerna kan de ha felaktiga behörighetsinställningar efter en ominstallation

Om du avinstallerar WSUS 3.0 SP2 kan du behålla installationsloggfilerna om du så önskar. När du ominstallerar WSUS 3.0 SP2 kan det hända att de gamla loggfilerna förlorar sina behörighetsinställningar (oftast endast för WSUS-administratörer). Du rekommenderas att kontrollera loggfilernas behörighetsinställningar efter installation.

### Om WSUS 2.0-klienter har uppdateringar med status "Inte tillämpliga" visas dessa uppdateringar som "Okänt" en kort tid efter uppgraderingen till WSUS 3.0 SP2

Om en befintlig WSUS 2.0-server har klienter med **Inte tillämpliga** uppdateringar, kan dessa uppdateringar anges som **Okänt** en kort tid efter att du har uppgraderat till WSUS 3.0 SP2. Uppdateringens status återgår till **Inte tillämpliga** nästa gång klienten utför en genomsökning.

Installera WSUS 3.0 SP2
-----------------------

Installationsguiden till WSUS på [http://go.microsoft.com/fwlink/?LinkId=139836](http://go.microsoft.com/fwlink/?linkid=139836) innehåller anvisningar om hur du installerar WSUS 3.0 SP2 via Serverhanteraren i Windows eller via filen WSUSetup.exe.

Fullständig information om hur du installerar och använder WSUS finns i:

WSUS-distributionshandboken på [http://go.microsoft.com/fwlink/?LinkId=139832](http://go.microsoft.com/fwlink/?linkid=139832).

WSUS-operatörshandboken på [http://go.microsoft.com/fwlink/?LinkId=139838](http://go.microsoft.com/fwlink/?linkid=139838).

Kommandoradsparametrar för obevakade WSUS 3.0 SP2-installationer
----------------------------------------------------------------

Du kan utföra obevakade installationer av WSUS 3.0 SP2 med hjälp av kommandoradsparametrar. I tabellen nedan visas kommandoradsparametrarna för installation av WSUS 3.0 SP2.

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
<td style="border:1px solid black;">Avinstallera.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/p</strong></td>
<td style="border:1px solid black;">Kontroll av förutsättningar. Granskar systemet och rapporterar eventuella nödvändiga förutsättningar som saknas.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/?, /h</strong></td>
<td style="border:1px solid black;">Visa kommandoradsparametrar och deras beskrivningar.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/g</strong></td>
<td style="border:1px solid black;">Uppgradera från föregående version av WSUS. (Uppgradering från SUS 1.0 är inte tillåten.) Den enda giltiga parametern med det här alternativet är /q (tyst installation). Den enda giltiga egenskapen med det här alternativet är DEFAULT_WEBSITE.</td>
</tr>
</tbody>
</table>
  
I tabellen nedan visas kommandoradsegenskaper för WSUS 3.0 SP2.
  
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
<td style="border:1px solid black;">Sökväg till innehållskatalog. Standardvärdet är <em>WSUS-installationsenhet\WSUS\WSUS-innehåll</em>, där <em>WSUS-installationsenhet</em> är den lokala enhet med mest ledigt utrymme.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">WYUKON_DATA_DIR</td>
<td style="border:1px solid black;">Sökväg till datakatalogen för Windows Internal Database.</td>
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
<td style="border:1px solid black;">0=installera WSUS-servern, 1=installera endast konsol</td>
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
<td style="border:1px solid black;">0=behåll loggfiler, 1=radera loggfiler (används med installationsparametern /u)</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">CREATE_DATABASE</td>
<td style="border:1px solid black;">0=använd aktuell databas, 1=skapa databas</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">PROGRESS_WINDOW_HANDLE</td>
<td style="border:1px solid black;">Fönsterreferens för att returnera förloppsmeddelanden i Windows Installer</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">MU_ROLLUP</td>
<td style="border:1px solid black;">1=delta i programmet för kvalitetsförbättring av Microsoft Update, 0=delta inte i programmet</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">FRONTEND_SETUP</td>
<td style="border:1px solid black;">1=skriv inte innehållsplatsen till databasen, 0=skriv innehållsplatsen till databasen (för NLB)</td>
</tr>
</tbody>
</table>
  
### Exempel på användningsområden
  
```  
WSUSSetup.exe /q DEFAULT\_WEBSITE=0 (installera i tyst läge med port 8530) WSUSSetup.exe /q /u (avinstallera WSUS)  
```
 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939886.Important(WS.10).gif" />Viktigt</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Om du installerar WSUS 3.0 SP2 i tyst läge (/q) och datorn inte har alla komponenter som krävs, skapas en fil med namnet WSUSPreReqCheck.xml som sparas i katalogen %TEMP%.
</td>
</tr>
</tbody>
</table>
 

<span id="BKMK_KnownIssues"></span>
Kända problem
-------------

-   När installationsguiden till WSUS har slutförts utan fel ombes användaren att klicka på **Slutför**. I sällsynta fall visas en feldialogruta med meddelandet **Ett fel inträffade vid kommunikation med servern och guiden måste stängas. Du kan starta om guiden WSUS-serverkonfiguration från sidan Alternativ i WSUS 3.0-konsolen.** Kontrollera att installationsinställningarna har sparats genom att öppna sidan **Alternativ** i WSUS-administrationskonsolen och kontrollera inställningarna i alla avsnitt.
-   **Lokaliserade versioner av WUA-klienten (Windows Update Agent) görs tillgängliga efter WSUS 3.0 SP2**. Detta beror på lokaliseringsplanerna för Windows 7. Mellan lanseringen av WSUS 3.0 SP2 och lanseringen av den lokaliserade versionen av WUA-klienten har klienten endast stöd för fem språk (engelska, tyska, franska, spanska och japanska).
-   **De nya uppdaterings- och datorstatusrapporterna som infördes i SP2 fungerar inte i miljöer där WSUS 3.0 SP1-servrar nedströms hanteras från en WSUS 3.0 SP2-server**. Om de nya rapporterna körs för en SP1-server visas felmeddelandet ”Ett fel inträffade när rapporten genererades. Försök att köra rapporten igen och kontakta nätverksadministratören om problemet kvarstår.” Problemet löses inte genom att köra rapporten igen. Felet är inte heller relaterat till nätverksfunktioner. De nya rapporterna är beroende av API-funktioner som saknas i SP1, men rapporterna blockeras inte i SP2-administrationskonsolen vid hantering av SP1-servrar.
-   **Det går inte att uppgradera till WSUS 3.0 SP2 om SSL har konfigurerats utan certifikatnamn**. Det krävs ett certifikatnamn vid konfigurering av SSL.
-   **Om WSUS 3.0 SP2 kör Windows Internal Database som har installerats i Windows Server 2008 går det inte att uppgradera till Windows Server 2008 R2**. Innan uppgraderingen till Windows Server 2008 R2 fortsätter visas en kompatibilitetsrapport där du instrueras att inaktivera Windows Internal Database. Du måste uppgradera Windows Internal Database för att kunna fortsätta uppgraderingen till Windows Server 2008 R2. Instruktioner och mer information om uppgradering av Windows Internal Database finns i [Så hämtar du senaste Service Pack för Windows Internal Database](http://go.microsoft.com/fwlink/?linkid=162104) (http://go.microsoft.com/fwlink/?LinkId=162104).

Upphovsrättsmeddelande
----------------------

Informationen i det här dokumentet, bland annat URL:er och andra referenser till webbplatser, kan ändras utan föregående meddelande. Såvida inte annat anges är alla företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser som förekommer i exemplen fiktiva. Alla likheter med verkliga företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser eller händelser är oavsiktliga. Ansvaret för att upphovsrättslagar följs ligger på användaren. Ingen del av det här dokumentet får reproduceras, lagras eller infogas i ett informationssystem eller överföras i någon form, med något medel (elektroniska eller mekaniska medier, fotokopiering, inspelning eller någon annan form av reproduktion) eller för något ändamål utan uttrycklig skriftlig tillåtelse från Microsoft Corporation.

För innehållet i detta dokument kan Microsoft inneha patent, patentansökningar, varumärken, copyright eller andra rättigheter som regleras av upphovsrättslagar. Innehav av detta dokument medför inga rättigheter till patent, varumärken, copyright eller andra upphovsrättsskyddade produkter utöver vad som uttryckligen anges i ett skriftligt licensavtal med Microsoft.

© 2009 Microsoft Corporation. Med ensamrätt.

Microsoft, Active Directory, ActiveX, Authenticode, Excel, InfoPath, Internet Explorer, MSDN, Outlook, Visual Studio, Win32, Windows, Windows Server och Windows Vista är varumärken som tillhör företag i Microsoft-gruppen.

Alla andra varumärken tillhör respektive ägare.
