---
TOCTitle: Viktigt för WSUS med Service Pack 1
Title: Viktigt för WSUS med Service Pack 1
ms:assetid: '937ecfe9-e8e0-41ac-85f7-4b65956f3d1e'
ms:contentKeyID: 18152848
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708486(v=WS.10)'
---

Viktigt för WSUS med Service Pack 1
===================================

I det här dokumentet beskrivs kända problem som påverkar Windows Server Update Services med Service Pack 1 (WSUS med SP1). Direkt efter informationen om WSUS med SP1 hittar du all den information som redan ingår i originalinformationen om WSUS. Här finns rekommendationer och krav för installation av WSUS. Du kan hämta WSUS med SP1 på [Microsoft Download Center](http://go.microsoft.com/fwlink/?linkid=67516).

Nyheter i WSUS med SP1
----------------------

WSUS med SP1 är ett service pack som ger förbättringar i WSUS i fråga om säkerhet, tillförlitlighet, skalbarhet, kompatibilitet och prestanda. Det här är de nya egenskaperna och förbättringarna:

-   Klientsupport för Windows Vista: Datorer där Windows Vista körs kan uppdateras med hjälp av WSUS med SP1-servern.
-   Hantering av fler språk: Kan användas för alla Office- och Windows Vista-språk.
-   Ny version av WMSDE: Med WSUS with SP1 uppgraderas WMSDE-instansen till WMSDE SP4 (WSUS RTM använder WMSDE SP3).
-   Förbättringar av prestanda: WSUS med SP1 omfattar olika förbättringar av prestanda, som ökar användargränssnittets svarstider.
-   Alla snabbkorrigeringar: WSUS med SP1 innehåller alla ändringar och snabbkorrigeringar sedan WSUS RTM.
-   Funktioner för SQL Server 2005.

Innan du påbörjar uppgradering av WSUS med SP1
----------------------------------------------

Följande problem är specifika för uppgradering av WSUS med SP1. Observera att de problem och krav som beskrivs i avsnittet ”Innan du börjar” i originalversionen fortfarande gäller, även om de inte behandlas här. Till exempel gäller fortfarande de installationskrav som nämns i originalversionen av ”Innan du börjar”.

**Obs!**   När du har lagt till SP1 i WSUS 2.0 kan du inte avinstallera det. Om du avinstallerar SP1 avinstalleras hela produkten.

**Viktigt!**   I det här dokumentet finns information om hur du redigerar registret. Var noga med att säkerhetskopiera registret innan du gör några ändringar. Ta reda på hur du gör för att återställa registret om det skulle uppstå problem. Mer information om säkerhetskopiering, återställning och redigering av registret finns i följande artikel i Microsoft Knowledge Base:

[Beskrivning av registret i Microsoft Windows](http://support.microsoft.com/kb/256986) (http://support.microsoft.com/kb/256986/)

#### Problem 1: Se till att du har tillräckligt med diskutrymme för säkerhetskopiering av databasen

När du uppgraderar från WSUS RTM skapas en säkerhetskopia av WSUS-databasen automatiskt vid installationen av WSUS med SP1. Därför måste du se till att diskutrymmet i WSUS-serverns filsystem räcker till att säkerhetskopiera WSUS-databasen. Annars lyckas inte installationen av WSUS med SP1.

**Så här kontrollerar du att det finns tillräckligt med diskutrymme**
1.  Öppna Utforskaren och gå till mappen med WSUS-databasen. Databasen installeras som standard här:

    
        ```
2.  Tryck på **CTRL**, välj **SUSDB.MDF** och **SUSDB\_log.LDF**. Högerklicka sedan och välj **Egenskaper**.

3.  I dialogrutan **Arkiv** läser du av värdet under **Storlek på disk**. Du måste ha minst så mycket ledigt diskutrymme för att kunna installera WSUS med SP1.

4.  Klicka på **Den här datorn** på **Start**-menyn. Kontrollera att det finns så mycket utrymme som krävs på den disk där WSUS installerats.

Om installationen av WSUS med SP1 av någon anledning skulle misslyckas återställer du den säkerhetskopierade databasen manuellt. Instruktioner om hur du återställer WSUS-databasen hittar du i [handboken till WSUS](http://technet2.microsoft.com/windowsserver/en/library/05f2e884-ae62-4c90-9681-6c9f2f3c9fd91033.mspx).

#### Problem 2: Med WSUS med SP1 uppgraderar du endast WSUS RTM

Du kan endast använda WSUS med SP1 till att uppgradera WSUS RTM. Just nu går det inte att uppgradera från förhandsversionen av WSUS. Om du har installerat förhandsversionen av WSUS eller någon tidigare version av WSUS måste du avinstallera den och sedan köra WSUS med SP1.

#### Problem 3: Serverns IIS-tjänst stoppas under uppgraderingen till WSUS med SP1

Installationsprogrammet för uppgradering till WSUS med SP1 stoppar IIS-tjänsten (Internet Information Services) på servern under själva uppgraderingen. Det innebär att du under uppgraderingen inte kommer att kunna använda alla de webbplatser som är kopplade till IIS-installationen på servern. IIS startas automatiskt igen när uppgraderingen är färdig.

#### Problem 4: Under uppgraderingen bör du inte köra några program som anropar API:er för WSUS

Anrop till API:er (Application Interface) för WSUS stör installationen av WSUS med SP1, vilket gör att uppgraderingen misslyckas (ett meddelande visas som talar om att du måste starta om servern för att kunna slutföra uppgraderingen).

#### Problem 5: När du uppgraderar till WSUS med SP1 kan du bli tvungen att avaktivera dina antivirusprogram

När du uppgraderar WSUS med WSUS med SP1 kan du eventuellt bli tvungen att avaktivera dina antivirusprogram innan du kan uppgradera eller lägga till SP1. När du har avaktiverat antivirusprogrammen startar du om Windows Server-datorn innan du uppgraderar med Service Pack. På så sätt kommer inte de filer som krävs vid uppgraderingsprocessen att låsas. När installationen är klar ser du till att aktivera antivirusprogrammet igen. Exakt hur du går tillväga för att avaktivera och aktivera just ditt antivirusprogram kan du läsa om på virusprogramtillverkarens webbplats.

| ![](images/Cc708486.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                  |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Den här lösningen kan göra datorn eller nätverket mer mottagligt för attacker från användare med skadligt uppsåt samt för skadliga program, till exempel virus. Vi rekommenderar inte den här lösningen men erbjuder den här informationen så att du kan använda metoden under eget ansvar. Du använder metoden på egen risk. |

| ![](images/Cc708486.note(WS.10).gif)Obs!                                                                                                                                                                                               |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Antivirusprogram är utformade för att skydda datorn mot virus. När antivirusprogrammet är avaktiverat bör du aldrig hämta eller öppna filer från någon källa som du inte litar på, besöka webbplatser som du inte litar på eller öppna bilagor i e-postmeddelanden. |

#### Problem 6: Om du använder en proxyserver kan användarnamn och lösenord för proxykonfigurationen raderas vid SP1-uppgradering

Om du använder en proxyserver kan det hända att användarnamn och lösenord för proxykonfigurationen raderas vid SP1-uppgraderingen. Då kan ett felmeddelande om ogiltig parameter visas vid synkroniseringen av uppdateringar från Microsoft Servers. Du löser problemet genom att återställa användarnamn och lösenord för proxykonfigurationen och synkronisera om servern.

#### Problem 7: Så här återställer du efter ett misslyckat försök att uppgradera, så att WSUS-servern återställs till ett konsekvent tillstånd och du kan göra om uppgraderingen.

Om uppgraderingen till WSUS med SP1 misslyckas kan WSUS-installationen hamna i ett inkonsekvent eller oanvändbart tillstånd. För att kunna försöka uppgradera till WSUS med SP1 igen måste du återställa WSUS-installationen till ett konsekvent tillstånd. Med hjälp av den säkerhetskopia som du skapade av databasen i början av uppgraderingen kan du återställa WSUS-servern till det läge den hade före uppgraderingen.

Om uppgraderingen misslyckas gör du så här för att försöka uppgradera till WSUS med SP1 en gång till:

**Försöka uppgradera till WSUS med SP1 en gång till**
1.  Ta reda på var säkerhetskopian av databasen finns med hjälp av innehållet i filen WSUSSetup\_%timestamp%.log. Filen hittar du i följande mapp:

    -   %programfiles%\\Update Services\\LogFiles

2.  Återställ databasen på WSUS-datorn med säkerhetskopian med hjälp av följande:

    -   osql.exe -S &lt;Databasinstans&gt; -E -Q "USE master ALTER DATABASE SUSDB SET SINGLE\_USER WITH ROLLBACK IMMEDIATE RESTORE DATABASE SUSDB FROM DISK=N'&lt;Sökvägtillsäkerhetskopieraddatabas&gt;' WITH REPLACE ALTER DATABASE SUSDB SET MULTI\_USER"
    -   Kom ihåg att ersätta &lt;Databasinstans&gt; och &lt;Sökvägtillsäkerhetskopieraddatabas&gt; med värden från din egen installation.
    -   För &lt;Databasinstans&gt; använder du värdet i följande registernyckel:
    -   HKLM\\Software\\Microsoft\\Update Services\\Server\\Setup\\SqlServerName
    -   För &lt;Sökvägtillsäkerhetskopieraddatabas&gt; använder du det värde som identifierades i steg 1

3.  Avinstallera WSUS men behåll WSUS-databasen, loggfilerna och uppdateringsfilerna när du uppmanas att ta bort dem. (Se till att avmarkera alla alternativ i **Remove Microsoft Windows Server Update Services**.)

4.  Installera om WSUS RTM (originalversionen, inte WSUS med SP1). Använd den befintliga databasen när du uppmanas att göra det. Då återställs WSUS-systemet till konsekvent tillstånd.

5.  Installera WSUS med SP1.

**Obs!**    Det går inte att använda säkerhetskopian av databasen från steg 1 ovan direkt vid en ren installation av WSUS med SP1. Databasschemat har ändrats så att databasen inte är kompatibel förrän du har uppdaterat till WSUS med SP1.

#### Problem 8: Ibland händer det att uppgradering till WSUS med SP1 misslyckas när WMSDE-databasen har migrerats

Lösningen varierar beroende på om migreringen är till en lokal SQL-server eller en fjärr-SQL-server.

#### WMSDE-databasen migrerad till en lokal SQL 2000-server

Ett registreringsnyckelvärde måste ändras för att installationspaketet för WSUS med SP1 ska känna av att det inte finns någon WMSDE-databas att uppdatera.

Om du har migrerat WMSDE till en lokal SQL 2000-server måste du utföra följande registerändring innan du kan försöka uppgradera till WSUS med SP1:

-   Ändra värdet för följande registreringsnyckel från 1 till 0:
    -   HKLM\\Software\\Microsoft\\Update Services\\Server\\Setup\\WmsdeInstalled  

#### WMSDE-databasen migrerad till en fjärr-SQL 2000-server

Två registreringsnyckelvärden måste ändras för att installationspaketet för WSUS med SP1 ska känna av att det inte finns någon WMSDE-databas att uppdatera. Uppdateringen måste först göras på backend-servern och sedan på frontend-servern.  

Om du har migrerat WMSDE till en fjärr-SQL-server måste du utföra följande registreringsändring innan du kan försöka uppgradera till WSUS med SP1:

1.  Ändra värdet för följande registreringsnyckel från 1 till 0:
    -   HKLM\\Software\\Microsoft\\Update Services\\Server\\Setup\\WmsdeInstalled 
2.  Ändra värdet för följande registreringsnyckel från 0x80 till 0x20:
    -   HKLM\\Software\\Microsoft\\Update Services\\Server\\Setup\\InstallType 

När du har uppdaterat registreringsnycklarnas värden initierar du uppgraderingen på backend-servrarna och sedan på frontend-servrarna.

#### Problem 9: WSUS med SP1 kan inte användas till att uppdatera WSUS-servrar som installerats med fjärr-SQL-distributioner

Du måste köra installationspaketet för WSUS med SP1 på både frontend-servrar och backend-servrar.

**Uppgradera till WSUS med SP1 när fjärr-SQL används**
1.  Kör installationspaketet på frontend-servrarna utan växlar och välj att uppgradera.

2.  Kör installationspaketet på backend-servrarna utan växlar och välj att uppgradera.

#### Problem 10: Om du ändrar datornamnet innan du uppgraderar till WSUS med SP1 kan uppgraderingen misslyckas

Om du ändrar datornamn efter att du har installerat WSUS RTM och innan du uppgraderar till WSUS med SP1 kan uppgraderingen till WSUS med SP1 misslyckas.

Med hjälp av följande skript kan du ta bort och lägga tillbaka ASPNET- och WSUS-administratörsgrupperna. Kör sedan uppgraderingen en gång till.

        ```
| ![](images/Cc708486.note(WS.10).gif)Obs!                                                  |
|------------------------------------------------------------------------------------------------------------------------|
| Du kan bli tvungen att ersätta &lt;ContentDirectory&gt; på sista raden med sökvägen till lagringsplatsen för innehåll. |

Här följer det ursprungliga innehållet i filen Viktigt för WSUS
---------------------------------------------------------------

Följande är det ursprungliga innehållet i filen Viktigt för WSUS. WSUS med SP1 utgör *inte* någon lösning på följande problem. Innehållet bifogas för att underlätta för användaren.

Innan du börjar
---------------

#### Problem 1: IIS måste vara installerat

För Microsoft® Windows Server™ Update Services (WSUS) krävs att IIS (Internet Information Services) är installerat. På Microsoft Windows Server 2003 och Microsoft Windows® 2000 Server installeras dock inte IIS som standard. Därför kan installationsprogrammet för Windows Server Update Services stoppas. I så fall visas ett meddelande om att IIS inte är installerat.

Så här installerar du IIS:

1.  Öppna kontrollpanelen.
2.  Dubbelklicka på **Lägg till eller ta bort program**.
3.  Klicka på **Lägg till/ta bort Windows-komponenter**.
4.  Klicka på **Programserver** i listan **Komponenter**.
5.  Klicka på **Information**.
6.  Markera kryssrutan **ASP.NET**. Aktivera **COM+-åtkomst till nätverket** så markeras IIS (Internet Information Services) automatiskt.
7.  Välj **Internet Information Services (IIS)** och klicka sedan på **Information** så visas listan över IIS-komponenter.
8.  Markera de valfria komponenter som du vill installera. Den valfria WWW-tjänstkomponenten innehåller viktiga underkomponenter, som Active Server Pages och Remote Administration (HTML). Om du vill visa och välja de underkomponenterna klickar du på WWW-tjänst och sedan på Information. Klicka på OK tills guiden Windows-komponenter visas igen.
9.  Klicka på **Nästa** och slutför guiden Windows-komponenter.
10. När du har installerat IIS kör du installationsprogrammet för Windows Server Update Services.

#### Problem 2: För servrar som kör Windows 2000 Server behövs minst en webbplats i IIS innan du installerar WSUS

Om det inte finns några webbplatser i IIS när installationen körs kan installationsprogrammet misslyckas med att skapa en webbplats. Det här kan till exempel inträffa om webbplatsen Software Update Services (SUS) 1.0 var den enda webbplatsen i IIS och du tog bort den innan du började installera WSUS.

Om så är fallet måste du skapa en ny webbplats med hjälp av snapin-modulen IIS-hanteraren. När du har gjort det kan du markera den webbplatsen eller ange en ny webbplats i installationsprogrammet för WSUS.

Om du redan har försökt installera WSUS och installationen misslyckades eftersom det saknades webbplatser öppnar du snapin-modulen IIS-hanteraren och tar bort webbplats nummer ett. Följ därefter de steg som beskrevs ovan och kör installationsprogrammet igen.

#### Problem 3: Installera obligatoriska komponenter

#### Programvarukrav

I följande tabell visas vilken programvara som krävs för de olika operativsystemen. Kontrollera att WSUS-servern uppfyller kraven innan du kör installationsprogrammet för WSUS. Om datorn måste startas om när installationen har slutförts för någon av uppdateringarna ska du starta om datorn innan du installerar WSUS.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Operativsystem</th>
<th style="border:1px solid black;" >Krav</th>
<th style="border:1px solid black;" >Hämtningar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Alla operativsystem</td>
<td style="border:1px solid black;">Microsoft Internet Information Services (IIS) 5.0</td>
<td style="border:1px solid black;">Installera från operativsystem.
Se problem 1: IIS måste vara installerat.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Alla operativsystem</td>
<td style="border:1px solid black;">Background Intelligent Transfer Service (BITS) 2.0</td>
<td style="border:1px solid black;">Information för Windows Server 2003-operativsystem finns i Uppdatering för BITS (Background Intelligent Transfer Service) 2.0 och WinHTTP 5.1 Windows Server 2003 (KB842773) på Download Center (<a href="http://go.microsoft.com/fwlink/?linkid=47251">http://go.microsoft.com/fwlink/?LinkId=47251</a>).
Information för Windows Server 2000-operativsystem finns i Uppdatering för Background Intelligent Transfer Service (BITS) 2.0 och WinHTTP 5.1 Windows 2000 (KB842773) på Download Center (<a href="http://go.microsoft.com/fwlink/?linkid=46794">http://go.microsoft.com/fwlink/?LinkId=46794</a>).</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Windows Server 2003</td>
<td style="border:1px solid black;">Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003</td>
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47358">Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003</a>
Du kan även gå till <a href="http://go.microsoft.com/fwlink/?linkid=47370">Windows Update</a> och söka efter information om kritiska uppdateringar och Service Pack. Installera Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Windows Server 2003</td>
<td style="border:1px solid black;">Databasprogramvara som är fullständigt kompatibel med Microsoft SQL</td>
<td style="border:1px solid black;">Inte tillämpligt</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Windows 2000 Server</td>
<td style="border:1px solid black;">Databasprogramvara som är fullständigt kompatibel med Microsoft SQL</td>
<td style="border:1px solid black;">Om du inte använder Microsoft SQL Server 2000 kan du installera Microsoft SQL Server 2000 Desktop Engine (MSDE 2000). Det görs i flera steg. Mer information finns i Installera MSDE på Windows 2000 nedan.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Windows 2000 Server</td>
<td style="border:1px solid black;">Microsoft Internet Explorer 6.0 Service Pack 1</td>
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47359">Internet Explorer 6 Service Pack 1</a></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Windows 2000 Server</td>
<td style="border:1px solid black;">Microsoft .NET Framework Version 1.1 Redistributable Package</td>
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47369">Microsoft .NET Framework Version 1.1 Redistributable Package</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Windows 2000 Server</td>
<td style="border:1px solid black;">Microsoft .NET Framework 1.1 Service Pack 1</td>
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47368">Microsoft .NET Framework 1.1 Service Pack 1</a>
Du kan även gå till <a href="http://go.microsoft.com/fwlink/?linkid=47370">Windows Update</a> och söka efter information om kritiska uppdateringar och Service Pack. Installera Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2000.</td>
</tr>
</tbody>
</table>
 

Förutom de här kraven installeras eller konfigureras vid behov .NET version 1.1 på servern. (ASP.NET konfigureras av installationsprogrammet för WSUS.)

#### Installera MSDE 2000 på Windows 2000

Om du använder Windows 2000 för WSUS och inte har åtkomst till Microsoft SQL Server 2000 ska du installera Microsoft SQL Server 2000 Desktop Engine (MSDE) innan du kör installationsprogrammet för WSUS. Om MSDE redan är installerat på WSUS-servern behöver du inte installera en särskild instans för WSUS. Ange istället namnet på den befintliga instansen när du installerar WSUS.

Installationen av MSDE på Windows 2000 Server görs i fyra steg. Först måste du hämta och expandera MSDE-arkivet till en mapp på WSUS-servern. Sedan använder du en kommandotolk och kommandoradsalternativ och kör installationsprogrammet för MSDE, anger ett sa-lösenord och tilldelar WSUS som instansnamn. När MSDE-installationen slutförs kontrollerar du att WSUS-instansen körs som en NT-tjänst. Slutligen lägger du till en säkerhetskorrigering för MSDE som skyddar WSUS-servern.

#### Steg 1: Hämta och expandera MSDE-arkivet

Du måste hämta och expandera MSDE-arkivet till en mapp på WSUS-servern. Läs mer i [Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) Release A](http://go.microsoft.com/fwlink/?linkid=47366).

#### Steg 2: Installera MSDE

Använd en kommandotolk och kommandoradsalternativ och kör installationsprogrammet för MSDE, ange ett sa-lösenord och tilldela WSUS som instansnamn. När MSDE-installationen slutförs kontrollerar du att WSUS-instansen körs som en NT-tjänst.

Så här installerar du MSDE, anger ett sa-lösenord och tilldelar ett instansnamn:

1.  I kommandotolken går du till installationsmappen för MSDE (se "Steg 1: Hämta och expandera MSDE-arkivet.”)
2.  Skriv: **setup sapwd="***lösenord***" instans=WSUS**
    där *lösenord* är ett starkt lösenord för sa-kontot på den aktuella MSDE-instansen och där **instans** är namnet på databasinstansen. Du kan även använda standardinstansnamnet (i stället för "WSUS") för WSUS-databasen. Om du väljer det alternativet behöver du inte skriva **instans=WSUS** i kommandoradsparametern. Med det kommandot startas installationsprogrammet för MSDE och sa-lösenordet ställs in. Namnet på den aktuella MSDE-instansen anges till det värde du anger.

#### Steg 3: Kontrollera att WSUS-instansen för MSDE är installerad

1.  Klicka på **Start** och sedan på **Kör**.
2.  Skriv **services.msc** i rutan **Öppna** och klicka på **OK**.

Bläddra nedåt i listan över tjänster och kontrollera att tjänsten MSSQL$WSUS (om du använde "WSUS" som instans) eller MSSQLSERVER (om du använde standardinstansnamnet) finns där.

#### Steg 4: Starta MSDE-instansen

I slutet av MSDE-installationen måste du starta instansen. Om du använde "WSUS" som instans startar du "MSSQL$WSUS". Om du använde standardinstansnamnet startar du MSSQLSERVER. Om du inte startar tjänsten kan inte WSUS använda databasinstansen.

#### Steg 5: Uppdatera MSDE

Du måste hämta och installera den säkerhetskorrigering som beskrivs i [MS03-031: Kumulativ säkerhetskorrigering för SQL Server](http://go.microsoft.com/fwlink/?linkid=47364).

Information om hur du hämtar säkerhetskorrigeringen finns i [SQL Server 2000 (32 bitar) Säkerhetskorrigering MS03-031](http://go.microsoft.com/fwlink/?linkid=47363).

#### Problem 4: Krav på diskutrymme

Här följer lägsta krav på diskutrymme vid installation av Windows Server Update Services

-   1 GB på systempartitionen
-   2 GB för den volym där databasfilerna ska lagras
-   6 GB, baserat på innehållsprojicering

#### Problem 5: Tidigare versioner av WSUS måste avinstalleras med hjälp av Lägg till/ta bort program innan du kan installera den senaste versionen

Om du planerar att installera Windows Server Update Services på en server där Windows Update Services Beta 1 eller Beta 2 är installerat, måste du först avinstallera den tidigare versionen med hjälp av Lägg till/ta bort program på Kontrollpanelen.

#### Problem 6: För WSUS krävs att alternativet för nästlade utlösare aktiveras i SQL Server

Alternativet är som standard aktiverat men kan inaktiveras av SQL Server-administratören.

Om du planerar att använda en SQL Server-databas som arkiv för Windows Server Update Services-data måste SQL Server-administratören kontrollera att alternativet för nästlade utlösare är aktiverat på servern innan WSUS-administratören installerar WSUS och anger databasen vid installation.

Installationsprogrammet för WSUS aktiverar alternativet RECURSIVE\_TRIGGERS, som är ett databasspecifikt alternativ. Alternativet för nästlade utlösare aktiveras dock inte, eftersom det är ett globalt serveralternativ.

Använd följande om du vill ta reda på om nästlade utlösare är aktiverade:

**sp\_configure 'nested triggers'**

När du vill aktivera alternativet för nästlade utlösare i SQL Server kör du följande från en batchfil på datorn där SQL Server körs:

**sp\_configure 'nested triggers', 1**

**GO**

**RECONFIGURE**

**GO**

#### Problem 7: Kommandoradsparametrar i installationsprogrammet för WSUS

Du kan utföra oövervakade installationer av WSUS. Mer information om det och om kommandoradsparametrar finns i bilaga (appendix) A om oövervakad installation i [Deploying Microsoft Windows Server Update Services](http://go.microsoft.com/fwlink/?linkid=41777).

Kända problem
-------------

#### Problem 1: IIS Lockdown

Om du kör IIS (Internet Information Services) på en dator med Windows 2000 Server, installerar du den senaste versionen av IIS Lockdown (med URLScan) från sidan IIS Lockdown Tool på Microsoft TechNet. Microsoft rekommenderar att du installerar verktyget till skydd för IIS-servrarna. IIS Lockdown fungerar så att sårbara funktioner i IIS stängs av. Därmed minskar risken för intrång.

| ![](images/Cc708486.note(WS.10).gif)Obs!                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| De här komponenterna installeras inte tillsammans med WSUS. Du måste installera dem manuellt. Du behöver inte installera IIS Lockdown på datorer med Windows Server 2003. Där ingår redan funktionen. |

#### Problem 2: Det går inte att ändra WSUS-konfigurationen direkt i databasen

I Windows Server Update Services lagras konfigurationsdata i en databas (MSDE eller SQL Server). Det går dock inte att ändra konfigurationsdata direkt i databasen. Administratörer avråds från att försöka ändra WSUS-konfigurationen på det sättet. WSUS-konfigurationen ska ändras via WSUS-konsolen eller API-anrop.

#### Problem 3: Active Scripting måste aktiveras innan administrationswebbplatsen för WSUS kan användas

På administratörens dator måste Internet Explorer konfigureras så att Active Scripting tillåts innan du kan använda Internet Explorer för att gå till administrationswebbplatsen för WSUS.

#### Problem 4: IIS startas om när WSUS installeras

Installationsprogrammet för Windows Server Update Services startar om IIS utan föregående meddelande. Det här kan påverka befintliga webbplatser i organisationen.

#### Problem 5: Ändra åtkomsten till den virtuella katalogen för administrationspunkterna i WSUS eller SMS

Som standard är den virtuella innehållskatalogen för Windows Server Update Services inställd för anonym åtkomst. Om du ändrar inställningen så att autentisering krävs får klienterna meddelande om autentiseringsfel och nekas åtkomst när de ska hämta uppdateringar Det här är ett känt problem. Winhttp.dll använder fel autentiseringskontext när implicit autentisering krävs, och autentiseringen misslyckas därför. Du förhindrar problemet genom att kontrollera att administrationspunkterna för WSUS-servern och SMS är konfigurerade för anonym åtkomst till de virtuella katalogerna i IIS.

#### Problem 6: När du installerar WSUS på Windows Small Business Server 2003 måste åtkomstinställningarna för de virtuella rötterna i WSUS på standardwebbplatsen ändras så att WSUS-klienterna kan uppdateras automatiskt från servern

WSUS-servern installerar två virtuella rötter, SelfUpdate och ClientWebService, samt några filer under hemkatalogen för standardwebbplatsen (på port 80). På så sätt kan klienterna uppdateras automatiskt via standardwebbplatsen. Som standard är standardwebbplatsen på Windows Small Business Server 2003 konfigurerad så att åtkomst nekas till andra IP eller localhost än serverns egna. Det innebär att de virtuella rötterna SelfUpdate och ClientWebService nekas åtkomst och att klienterna inte uppdateras automatiskt. Utför följande för standardwebbplatsens virtuella rötter SelfUpdate och ClientWebService när du vill ge klienterna åtkomst så att de kan uppdateras automatiskt:

1.  Klicka på den virtuella roten **Egenskaper** och därefter på **Katalogsäkerhet**. Klicka på **IP-adress och domännamnsrestriktioner** och därefter på **Redigera**.
2.  Markera **Beviljas åtkomst** och klicka sedan på **OK**. Stäng alla egenskapssidor.

#### Problem 7: Installera WSUS på Small Business Server - integreringsproblem

-   Om Windows Small Business Server 2003 använder en ISA-proxyserver för åtkomst till Internet måste du manuellt ange följande i användargränssnittet **Inställningar**: proxyserverinställningar, proxyservernamn och port.
-   Om Windows-autentisering används i ISA ska proxyserverns referenser anges med formatet "DOMAIN\\user" (där användaren tillhör gruppen "Internet-användare").

#### Problem 8: När du flyttar en dator från en datorgrupp till en annan kan det ta upp till en timme innan datorn visas i den nya gruppen på administrationskonsolen

När en dator tilldelas en målgrupp för första gången förändras informationen på datorn i enlighet med gruppinformationen. Informationen uppdateras regelbundet eller varje timme. När du flyttar en dator från en datorgrupp till en annan kan det därför ta upp till en timme innan informationen uppdateras på klienten och ändringarna visas i WSUS-administrationskonsolen.

#### Problem 9: Om du installerar WSUS på en medlemsserver och sedan vill uppgradera medlemsservern till domänkontrollant måste du först avinstallera WSUS

Om du installerar WSUS på en medlemsserver och sedan vill uppgradera medlemsservern till domänkontrollant gör du så här:

1.  Avinstallera WSUS.
2.  Uppgradera servern till domänkontrollant.
3.  Installera om WSUS.

#### Problem 10: Om du vill degradera en WSUS-server från domänkontrollant till en medlemsserver måste du först avinstallera WSUS

Om du kör WSUS-servern på en domänkontrollant och vill degradera domänkontrollanten till en medlemsserver gör du följande

1.  Avinstallera WSUS och behåll databasen.
2.  Skapa ett användarkonto med namnet ASPNET.
3.  Skriv **aspnet\_regiis -i** i kommandotolken.
4.  Installera om WSUS och använd den gamla databasen.

#### Problem 11: Om .NET Framework 1.0 eller 2.0 installeras efter WSUS visas inte WSUS-administrationskonsolen

Det beror på att .NET Framework 1.0 registreras med IIS och att .NET Framework 1.1 krävs för WSUS-servern. Du löser problemet genom att öppna aspnet\_regiis.exe och köra följande kommandon, där *webbplats-id* är värdet i följande registernyckel:

HKLM\\Software\\Microsoft\\WindowsUpdateServices\\Server\\Setup\\IISTargetWebsiteIndex

-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\ReportingWebService
-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\ClientWebService
-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\SimpleAuthWebService
-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\WSUSAdmin
-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\AdministrationWebService
-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\ServrSyncWebService
-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\DssAuthWebService
-   %windir%\\Microsoft.NET\\Framework\\v1.1.4322\\\\aspnet\_regiis.exe -s W3SVC\\&lt;*webbplats-id*&gt;\\ROOT\\Content

#### Problem 12: Begränsningar för fjärr-SQL

Det fungerar mindre bra att köra databasprogramvara på en annan dator än den där resten av WSUS är installerat.

-   Du kan inte använda Windows 2000 Server som frontend-dator i en fjärrkonfiguration.
-   Du kan inte använda en server som är konfigurerad som domänkontrollant som frontend eller backend i en fjärrkonfiguration.
-   WMSDE och MSDE kan inte användas som databasprogram på backend-datorn.
-   Installation av fjärr-SQL Server (för användning som WSUS-databas) misslyckas om Terminal Services är installerad på fjärrservern och körs i programläge. När du installerar SQL Server på en server med Terminal Services måste du göra följande:
    1.  Innan du kör inställningsprogrammet öppnar du kommandotolken och skriver: "change user /install".
    2.  Kör installationsprogrammet för SQL Server.
    3.  När du har kört installationsprogrammet skriver du följande i kommandotolken: "change user /execute".
-   Om du ska kunna installera en WSUS-databas för fjärr-SQL Server så måste du vara medlem i den lokala administratörssäkerhetsgruppen för både frontend-datorn och backend-datorn.
-   Mer information om problem med fjärr-SQL finns i bilaga (appendix) C om fjärr-SQL i [Deploying Microsoft Windows Server Update Services](http://go.microsoft.com/fwlink/?linkid=41777).

#### Problem 13: En underordnad replikserver kan ha färre godkännanden än den överordnade servern

En underordnad replikserver kan ha färre godkännanden än den överordnade servern. Det beror på att installationsgodkännanden inte förs vidare till en underordnad server förrän innehållet i sin helhet har hämtats till den överordnade servern.

#### Problem 14: Om synkroniseringen misslyckas försöker du igen

Om synkroniseringen misslyckas ska du börja med att försöka synkronisera servern igen. Om synkroniseringen misslyckas igen läser du vidare i den felsökningsinformation som du hittar i handboken till WSUS.

#### Problem 15: När du försöker komma åt WSUS-konsolen visas ett felmeddelande om System.IO.FileNotFoundException

Om du får följande felmeddelande kan du behöva justera behörigheterna för kontona Nätverkstjänst eller ASP.NET:

System.IO.FileNotFoundException: File or Assembly name *xxxxxx*.dll, or one of its dependencies, was not found

Där *xxxx* kan vara vilket namn som helst.

För att lösa det här problemet för Windows Server 2003-operativsystem ger du kontot Nätverkstjänst läs- och skrivbehörighet till %systemroot%\\Temp. I Windows 2000 Server ger du kontot ASP.NET läs- och skrivbehörighet till %systemroot%\\Temp.

#### Problem 16: SQL Säkerhetskorrigering MS03-031 (KB815495)

Den här uppdateringen kan visas som installerad på WSUS-servern även om installationen på klienten misslyckades. På grund av det kan paketet erbjudas klienten på nytt. Du kommer förbi problemet genom att ta bort uppdateringsgodkännandet på servern.

#### Problem 17: IIS-inställningarna går förlorade vid RTM-uppgradering

Om du installerar WSUS RTM på en server med en tidigare version av WSUS (till exempel RC) avinstalleras den tidigare versionen och den nya versionen installeras. Det innebär att virtuella rötter och filer som associerats med WSUS i IIS tas bort.

Om du installerade WSUS på standardwebbplatsen går alla WSUS-relaterade inställningar för virtuella rötter förlorade. Om du till exempel har konfigurerat virtuella WSUS-rötter för SSL i syfte att skydda WUS måste du konfigurera om dem efter installation av RTM-versionen av WSUS. Obs! Du får ett meddelande på WSUS-konsolen om att SSL inte är aktiverat.

Om WSUS var installerat på en annan webbplats än standardwebbplatsen går alla övriga inställningar på webbplatsnivån förlorade.

#### Problem 18: Använda host headers

Om du vill använda host headers för standardwebbplatsen (WSUS-webbplatsen) i IIS måste du lägga till alternativet för alla otilldelade eller en tilldelad IP-adress i listan över IP-adresser utan host headers för standardwebbplatsen. Alternativet eller adressen läggs även till för en webbplats som inte är standard.

**Varning**! Det här kan leda till att Microsoft SharePoint och Exchange inte fungerar tillsammans.

#### Problem 19: URL-adressen till WSUS-konsolen måste läggas till i listan Tillförlitliga platser och Lokalt intranät på datorer där Internet Explorer Hardening är aktiverat

Om Internet Explorer Hardening (kallas även komponenten Microsoft Windows Server 2003 Internet Explorer Enhanced Security Configuration) är aktiverat på en dator och du inte lägger till WSUS-konsolen i listan Tillförlitliga platser och Lokalt intranät, ombeds du ange användaridentifiering varje gång du öppnar en sida i WSUS-konsolen

Så här lägger du till WSUS-konsolen i zonerna **Lokalt intranät** och **Tillförlitliga platser**:

1.  Öppna **Internet-alternativ** (klicka till exempel på **Start**, peka på **Kontrollpanelen** och klicka därefter på **Internet-alternativ**).
2.  På fliken **Säkerhet** klickar du på **Lokalt intranät** och därefter på **Platser**. Klicka sedan på **Avancerat** och lägg till URL-adressen (http://*WSUSServername*/WSUSAdmin). Klicka därefter på **OK**.
3.  Klicka på **Tillförlitliga platser** och sedan på **Platser**. Lägg till URL-adressen för WSUS-konsolen och klicka på **OK**. Stäng sedan **Internet-alternativ** genom att klicka på **OK** igen.

#### Copyright

Informationen i det här dokumentet visar Microsoft Corporations aktuella hållning i de ämnen som tas upp vid publiceringstillfället. Eftersom Microsoft snabbt måste agera efter förändringar på marknaden ska den inte tolkas som bindande från Microsofts sida, och Microsoft kan inte heller garantera korrektheten i informationen efter publiceringsdatumet.

Det här dokumentet är endast avsett som information. MICROSOFT GER INGA GARANTIER, UTTRYCKLIGA, UNDERFÖRSTÅDDA ELLER LAGSTADGADE, VAD GÄLLER INFORMATIONEN I DET HÄR DOKUMENTET.

Ansvaret för att följa upphovsrättslagar ligger på användaren. Ingen del av det här dokumentet får reproduceras, lagras eller infogas i ett informationssystem eller överföras i någon form, med något medel (elektroniska eller mekaniska medier, fotokopiering, inspelning eller någon annan form av reproduktion) eller för något ändamål utan uttrycklig skriftlig tillåtelse från Microsoft Corporation.

För innehållet i det här dokumentet kan Microsoft inneha patent, patentansökningar, varumärken, copyright eller andra rättigheter som regleras av upphovsrättslagar. Innehav av detta dokument medför inga rättigheter till patent, varumärken, copyright eller andra upphovsrättsskyddade produkter utöver vad som uttryckligen anges i ett skriftligt licensavtal med Microsoft.

Om inget annat anges är de exempel på företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser som nämns i det här dokumentet påhittade, och alla eventuella kopplingar till verkliga företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser är helt oavsiktliga.

© 2006 Microsoft Corporation. Med ensamrätt.

Microsoft, SQL Server, Windows och Windows Server är antingen registrerade varumärken eller varumärken som tillhör Microsoft Corporation i USA och eller andra länder.

Namnen på befintliga företag och produkter som nämns här kan vara varumärken som tillhör respektive ägare.
