---
TOCTitle: 'Viktigt-fil för Windows Server Update Services'
Title: 'Viktigt-fil för Windows Server Update Services'
ms:assetid: '4244109a-395a-4ff8-9989-ea55ab0964a3'
ms:contentKeyID: 18152662
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720505(v=WS.10)'
---

Viktigt-fil för Windows Server Update Services
==============================================

I det här dokumentet beskrivs kända problem som påverkar Windows Server Update Services (WSUS). Det innehåller rekommendationer och krav för att installera WSUS.

| ![](images/Cc720505.note(WS.10).gif)Obs!                                                                                         |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du kan hämta det här dokumentet på Microsoft Download Center på [http://go.microsoft.com/fwlink/?LinkId=48126](http://go.microsoft.com/fwlink/?linkid=48126). |

Innan du börjar
---------------

#### Problem 1: IIS måste vara installerat

För Microsoft® Windows Server™ Update Services (WSUS) krävs att IIS (Internet Information Services) är installerat. På Microsoft Windows Server 2003 och Microsoft Windows® 2000 Server installeras dock inte IIS som standard. Därför kan installationsprogrammet för Windows Server Update Services stoppas. I så fall visas ett meddelande om att IIS inte är installerat.

Så här installerar du IIS:

1.  Öppna kontrollpanelen.
2.  Dubbelklicka på **Lägg till eller ta bort program**.
3.  Klicka på **Lägg till/ta bort Windows-komponenter**.
4.  Klicka på **Programserver** i listan **Komponenter**.
5.  Klicka på **Information**.
6.  Markera kryssrutan **ASP.NET**. Aktivera **COM+-åtkomst till nätverket** så markeras IIS (Internet Information Services) automatiskt.
7.  Välj **Internet Information Services (IIS)** och klicka sedan på **Information** så visas listan över IIS-komponenter.
8.  Markera de valfria komponenter som du vill installera. Den valfria WWW-tjänstkomponenten innehåller viktiga underkomponenter, som Active Server Pages och Remote Administration (HTML). Om du vill visa och välja de underkomponenterna klickar du på WWW-tjänst och sedan på Information. Klicka på OK tills guiden Windows-komponenter visas igen.
9.  Klicka på **Nästa** och slutför guiden Windows-komponenter.
10. När du har installerat IIS kör du installationsprogrammet för Windows Server Update Services.

#### Problem 2: För servrar som kör Windows 2000 Server behövs minst en webbplats i IIS innan du installerar WSUS

Om det inte finns några webbplatser i IIS när installationen körs kan installationsprogrammet misslyckas med att skapa en webbplats. Det här kan till exempel inträffa om webbplatsen Software Update Services (SUS) 1.0 var den enda webbplatsen i IIS och du tog bort den innan du började installera WSUS.

Om så är fallet måste du skapa en ny webbplats med hjälp av snapin-modulen IIS-hanteraren. När du har gjort det kan du markera den webbplatsen eller ange en ny webbplats i installationsprogrammet för WSUS.

Om du redan har försökt installera WSUS och installationen misslyckades eftersom det saknades webbplatser öppnar du snapin-modulen IIS-hanteraren och tar bort webbplats nummer ett. Följ därefter de steg som beskrevs ovan och kör installationsprogrammet igen.

#### Problem 3: Installera obligatoriska komponenter

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
<td style="border:1px solid black;">Information om operativsystem med Windows Server 2003 finns i avsnittet om <a href="http://go.microsoft.com/fwlink/?linkid=47251">uppdatering av BITS 2.0 (Background Intelligent Transfer Service ) och WinHTTP 5.1 för Windows Server 2003</a> (KB842773) på Download Center (http://go.microsoft.com/fwlink/?LinkId=47251).
Information om operativsystem med Windows Server 2000 finns i avsnittet om <a href="http://go.microsoft.com/fwlink/?linkid=46794">uppdateringar av BITS 2.0 (Background Intelligent Transfer Service ) och WinHTTP 5.1 för Windows Server 2000</a> (KB842773) på Download Center (http://go.microsoft.com/fwlink/?LinkId=47251).</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Windows Server 2003</td>
<td style="border:1px solid black;">Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003</td>
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47358">Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003</a>
Du kan även gå till <a href="http://go.microsoft.com/fwlink/?linkid=47370">Windows Update</a> och söka efter information om kritiska uppdateringar och Service Pack. Installera Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Windows Server 2003</td>
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
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47359">Internet Explorer 6 Service Pack 1</a></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Windows 2000 Server</td>
<td style="border:1px solid black;">Microsoft .NET Framework Version 1.1 Redistributable Package</td>
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47369">Microsoft .NET Framework Version 1.1 Redistributable Package</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Windows 2000 Server</td>
<td style="border:1px solid black;">Microsoft .NET Framework 1.1 Service Pack 1</td>
<td style="border:1px solid black;"><a href="http://go.microsoft.com/fwlink/?linkid=47368">Microsoft .NET Framework 1.1 Service Pack 1</a>
Du kan även gå till <a href="http://go.microsoft.com/fwlink/?linkid=47370">Windows Update</a> och söka efter information om kritiska uppdateringar och Service Pack. Installera Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2000.</td>
</tr>
</tbody>
</table>
 

Förutom de här kraven installeras eller konfigureras vid behov .NET version 1.1 på servern. (ASP.NET konfigureras av installationsprogrammet för WSUS.)

#### Installera MSDE 2000 på Windows 2000

Om du använder Windows 2000 för WSUS och inte har åtkomst till Microsoft SQL Server 2000 ska du installera Microsoft SQL Server 2000 Desktop Engine (MSDE) innan du kör installationsprogrammet för WSUS. Om MSDE redan är installerat på WSUS-servern behöver du inte installera en särskild instans för WSUS. Ange istället namnet på den befintliga instansen när du installerar WSUS.

Installationen av MSDE på Windows 2000 Server görs i fyra steg. Först måste du hämta och expandera MSDE-arkivet till en mapp på WSUS-servern. Sedan använder du en kommandotolk och kommandoradsalternativ och kör installationsprogrammet för MSDE, anger ett sa-lösenord och tilldelar WSUS som instansnamn. När MSDE-installationen slutförs kontrollerar du att WSUS-instansen körs som en NT-tjänst. Slutligen måste du lägga till en säkerhetsuppdatering i MSDE för att skydda WSUS-servern.

#### Steg 1: Hämta och expandera MSDE-arkivet

Du måste hämta och expandera MSDE-arkivet till en mapp på WSUS-servern. Läs mer i [Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) version A](http://go.microsoft.com/fwlink/?linkid=47366).

#### Steg 2: Installera MSDE

Använd en kommandotolk och kommandoradsalternativ och kör installationsprogrammet för MSDE, ange ett sa-lösenord och tilldela WSUS som instansnamn. När MSDE-installationen slutförs kontrollerar du att WSUS-instansen körs som en NT-tjänst.

Så här installerar du MSDE, anger ett sa-lösenord och tilldelar ett instansnamn:

1.  I kommandotolken går du till installationsmappen för MSDE (se "Steg 1: Hämta och expandera MSDE-arkivet.”)
2.  Skriv: **setup sapwd="***lösenord***" instans=WSUS**
    där *lösenord* är ett starkt lösenord för sa-kontot på den aktuella MSDE-instansen och där **instans** är namnet på databasinstansen. Du kan även använda standardinstansnamnet (i stället för "WSUS") för WSUS-databasen. Om du väljer det alternativet behöver du inte skriva **instans=WSUS** i kommandoradsparametern. Med det kommandot startas installationsprogrammet för MSDE och sa-lösenordet ställs in. Namnet på den aktuella MSDE-instansen anges till det värde du anger.

#### Steg 3: Kontrollera att WSUS-instansen för MSDE är installerad

Kontrollera att WSUS-instansen för MSDE visas.

1.  Klicka på **Start** och sedan på **Kör**.
2.  Skriv **services.msc** i rutan **Öppna** och klicka på **OK**.

Bläddra nedåt i listan över tjänster och kontrollera att tjänsten MSSQL$WSUS (om du använde "WSUS" som instans) eller MSSQLSERVER (om du använde standardinstansnamnet) finns där.

#### Steg 4: Starta MSDE-instansen

I slutet av MSDE-installationen måste du starta instansen. Om du använde "WSUS" som instans startar du "MSSQL$WSUS". Om du använde standardinstansnamnet startar du MSSQLSERVER. Om du inte startar tjänsten kan inte WSUS använda databasinstansen.

#### Steg 5: Uppdatera MSDE

Du måste hämta och installera den säkerhetsuppdatering som beskrivs i rapporten [MS03-031: Kumulativ säkerhetskorrigering för SQL Server](http://go.microsoft.com/fwlink/?linkid=47364).

Om du vill hämta säkerhetsuppdateringen går du till [SQL Server 2000 (32 bitar) Säkerhetskorrigering MS03-031](http://go.microsoft.com/fwlink/?linkid=47363).

#### Problem 4: Krav på diskutrymme

Här följer lägsta krav på diskutrymme vid installation av Windows Server Update Services

-   1 GB på systempartitionen
-   2 GB för den volym där databasfilerna ska lagras
-   6 GB, baserat på innehållsprojicering

#### Problem 5: Tidigare versioner av WSUS måste avinstalleras med hjälp av Lägg till/ta bort program innan du kan installera den senaste versionen

Om du planerar att installera Windows Server Update Services på en server där Windows Update Services Beta 1 eller Beta 2 är installerat, måste du först avinstallera den tidigare versionen med hjälp av Lägg till/ta bort program på Kontrollpanelen.

#### Problem 6: För WSUS krävs att alternativet för nästlade utlösare aktiveras i SQL Server

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

#### Problem 7: Kommandoradsparametrar i installationsprogrammet för WSUS

Du kan utföra oövervakade installationer av WSUS. Mer information om det och om kommandoradsparametrar finns i bilaga (appendix) A om oövervakad installation i [Deploying Microsoft Windows Server Update Services](http://go.microsoft.com/fwlink/?linkid=41777).

Kända problem
-------------

#### Problem 1: IIS Lockdown

Om du kör IIS (Internet Information Services) på en dator med Windows 2000 Server, installerar du den senaste versionen av IIS Lockdown (med URLScan) från sidan IIS Lockdown Tool på Microsoft TechNet. Microsoft rekommenderar att du installerar verktyget till skydd för IIS-servrarna. IIS Lockdown avaktiverar onödiga funktioner i IIS, vilket leder till minskad säkerhetsrisk.

| ![](images/Cc720505.note(WS.10).gif)Obs!                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| De här komponenterna installeras inte tillsammans med WSUS. Du måste installera dem manuellt. Du behöver inte installera IIS Lockdown på datorer med Windows Server 2003. Där ingår redan funktionen. |

#### Problem 2: Det går inte att ändra WSUS-konfigurationen direkt i databasen

I Windows Server Update Services lagras konfigurationsdata i en databas (MSDE eller SQL Server). Det går dock inte att ändra konfigurationsdata direkt i databasen. Administratörer avråds från att försöka ändra WSUS-konfigurationen på det sättet. WSUS-konfigurationen ska ändras via WSUS-konsolen eller API-anrop.

#### Problem 3: Active Scripting måste aktiveras innan administrationswebbplatsen för WSUS kan användas

På administratörens dator måste Internet Explorer konfigureras så att Active Scripting tillåts innan du kan använda Internet Explorer för att gå till administrationswebbplatsen för WSUS.

#### Problem 4: IIS startas om när WSUS installeras

Installationsprogrammet för Windows Server Update Services startar om IIS utan föregående meddelande. Det här kan påverka befintliga webbplatser i organisationen.

#### Problem 5: Ändra åtkomsten till den virtuella katalogen för administrationspunkterna i WSUS eller SMS

Som standard är den virtuella innehållskatalogen för Windows Server Update Services inställd för anonym åtkomst. Om du ändrar inställningen så att autentisering krävs får klienterna meddelande om autentiseringsfel och nekas åtkomst när de ska hämta uppdateringar Det här är ett känt problem. Winhttp.dll använder fel autentiseringskontext när implicit autentisering krävs, och autentiseringen misslyckas därför. Du förhindrar problemet genom att kontrollera att administrationspunkterna för WSUS-servern och SMS är konfigurerade för anonym åtkomst till de virtuella katalogerna i IIS.

#### Problem 6: När du installerar WSUS på Windows Small Business Server 2003 måste åtkomstinställningarna för de virtuella rötterna i WSUS på standardwebbplatsen ändras så att WSUS-klienterna kan uppdateras automatiskt från servern

WSUS-servern installerar två virtuella rötter, SelfUpdate och ClientWebService, samt några filer under hemkatalogen för standardwebbplatsen (på port 80). På så sätt kan klienterna uppdateras automatiskt via standardwebbplatsen. Som standard är standardwebbplatsen på Windows Small Business Server 2003 konfigurerad så att åtkomst nekas till andra IP eller localhost än serverns egna. Det innebär att de virtuella rötterna SelfUpdate och ClientWebService nekas åtkomst och att klienterna inte uppdateras automatiskt. Utför följande för standardwebbplatsens virtuella rötter SelfUpdate och ClientWebService när du vill ge klienterna åtkomst så att de kan uppdateras automatiskt:

1.  Klicka på den virtuella roten **Egenskaper** och därefter på **Katalogsäkerhet**. Klicka på **IP-adress och domännamnsrestriktioner** och därefter på **Redigera**.
2.  Markera **Beviljas åtkomst** och klicka sedan på **OK**. Stäng alla egenskapssidor.

#### Problem 7: Installera WSUS på Small Business Server - integreringsproblem

-   Om Windows Small Business Server 2003 använder en ISA-proxyserver för åtkomst till Internet måste du manuellt ange följande i användargränssnittet **Inställningar**: proxyserverinställningar, proxyservernamn och port.
-   Om Windows-autentisering används i ISA ska proxyserverns referenser anges med formatet "DOMAIN\\user" (där användaren tillhör gruppen "Internet-användare").

#### Problem 8: När du flyttar en dator från en datorgrupp till en annan kan det ta upp till en timme innan datorn visas i den nya gruppen på administrationskonsolen

När en dator tilldelas en målgrupp för första gången förändras informationen på datorn i enlighet med gruppinformationen. Informationen uppdateras regelbundet eller varje timme. När du flyttar en dator från en datorgrupp till en annan kan det därför ta upp till en timme innan informationen uppdateras på klienten och ändringarna visas i WSUS-administrationskonsolen.

#### Problem 9: Om du installerar WSUS på en medlemsserver och sedan vill uppgradera medlemsservern till domänkontrollant måste du först avinstallera WSUS

Om du installerar WSUS på en medlemsserver och sedan vill uppgradera medlemsservern till domänkontrollant gör du så här:

1.  Avinstallera WSUS.
2.  Uppgradera servern till domänkontrollant.
3.  Installera om WSUS.

#### Problem 10: Om du vill degradera en WSUS-server från domänkontrollant till en medlemsserver måste du först avinstallera WSUS

Om du kör WSUS-servern på en domänkontrollant och vill degradera domänkontrollanten till en medlemsserver gör du följande

1.  Avinstallera WSUS och behåll databasen.
2.  Skapa ett användarkonto med namnet ASPNET.
3.  Skriv **aspnet\_regiis -i** i kommandotolken.
4.  Installera om WSUS och använd den gamla databasen.

#### Problem 11: Om .NET Framework 1.0 eller 2.0 installeras efter WSUS visas inte WSUS-administrationskonsolen

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

#### Problem 12: Begränsningar för fjärr-SQL

Det fungerar mindre bra att köra databasprogramvara på en annan dator än den där resten av WSUS är installerat.

-   Du kan inte använda Windows 2000 Server som frontend-dator i en fjärrkonfiguration.
-   Du kan inte använda en server som är konfigurerad som domänkontrollant som frontend eller backend i en fjärrkonfiguration.
-   WMSDE och MSDE kan inte användas som databasprogram på backend-datorn.
-   Det går inte att installera en fjärrstyrd SQL-server (som ska användas som WSUS-databas) om Terminal Services har installerats på fjärrservern och körs i programläge. När du installerar SQL Server på en Terminal Services-server måste du göra följande:
    1.  Innan du kör inställningsprogrammet öppnar du kommandotolken och skriver: **change user /install**
    2.  Kör installationsprogrammet för SQL Server.
    3.  När du har kört installationsprogrammet skriver du följande i kommandotolken: **change user /execute**
-   Om du ska kunna installera en WSUS-databas för fjärr-SQL Server så måste du vara medlem i den lokala administratörssäkerhetsgruppen för både frontend-datorn och backend-datorn.
-   Mer information om problem med fjärr-SQL finns i bilaga (appendix) C om fjärr-SQL i [Deploying Microsoft Windows Server Update Services](http://go.microsoft.com/fwlink/?linkid=41777).

#### Problem 13: En underordnad replikserver kan ha färre godkännanden än den överordnade servern

En underordnad replikserver kan ha färre godkännanden än den överordnade servern. Det beror på att installationsgodkännanden inte förs vidare till en underordnad server förrän innehållet i sin helhet har hämtats till den överordnade servern.

#### Problem 14: Om synkroniseringen misslyckas försöker du igen

Om synkroniseringen misslyckas visas eventuellt ett felmeddelande. I så fall försöker du igen.

#### Problem 15: När du försöker komma åt WSUS-konsolen visas ett felmeddelande om System.IO.FileNotFoundException

Om du får följande felmeddelande kan du behöva justera behörigheterna för kontona Nätverkstjänst eller ASP.NET:

System.IO.FileNotFoundException: File or Assembly name *xxxxxx*.dll, or one of its dependencies, was not found

Där *xxxx* kan vara vilket namn som helst.

För att lösa det här problemet för Windows Server 2003-operativsystem ger du kontot Nätverkstjänst läs- och skrivbehörighet till %systemroot%\\Temp. I Windows 2000 Server ger du kontot ASP.NET läs- och skrivbehörighet till %systemroot%\\Temp.

#### Problem 16: SQL Säkerhetskorrigering MS03-031 (KB815495)

Den här uppdateringen kan visas som installerad på WSUS-servern även om installationen på klienten misslyckades. På grund av det kan paketet erbjudas klienten på nytt. Du kommer förbi problemet genom att ta bort uppdateringsgodkännandet på servern.

#### Problem 17: IIS-inställningarna går förlorade vid RTM-uppgradering

Om du installerar WSUS RTM på en server med en tidigare version av WSUS (till exempel RC) avinstalleras den tidigare versionen och den nya versionen installeras. Det innebär att virtuella rötter och filer som associerats med WSUS i IIS tas bort.

Om du installerade WSUS på standardwebbplatsen går alla WSUS-relaterade inställningar för virtuella rötter förlorade. Om du till exempel har konfigurerat virtuella WSUS-rötter för SSL i syfte att skydda WUS måste du konfigurera om dem efter installation av RTM-versionen av WSUS. Obs! Du får ett meddelande på WSUS-konsolen om att SSL inte är aktiverat.

Om WSUS var installerat på en annan webbplats än standardwebbplatsen går alla övriga inställningar på webbplatsnivån förlorade.

#### Problem 18: Använda host headers

Om du vill använda host headers för standardwebbplatsen (WSUS-webbplatsen) i IIS måste du lägga till alternativet för alla otilldelade eller en tilldelad IP-adress i listan över IP-adresser utan host headers för standardwebbplatsen. Alternativet eller adressen läggs även till för en webbplats som inte är standard.

**Varning!** Detta kan leda till att funktionerna Windows® SharePoint® Services och Exchange avbryts.

#### Problem 19: URL-adressen till WSUS-konsolen måste läggas till i listan Tillförlitliga platser och Lokalt intranät på datorer där Internet Explorer Hardening är aktiverat

Om Internet Explorer Hardening (kallas även komponenten Microsoft Windows Server 2003 Internet Explorer Enhanced Security Configuration) är aktiverat på en dator och du inte lägger till WSUS-konsolen i listan Tillförlitliga platser och Lokalt intranät, ombeds du ange användaridentifiering varje gång du öppnar en sida i WSUS-konsolen

Så här lägger du till WSUS-konsolen i zonerna **Lokalt intranät** och **Tillförlitliga platser**:

1.  Öppna **Internet-alternativ** (klicka till exempel på **Start**, peka på **Kontrollpanelen** och klicka därefter på **Internet-alternativ**).
2.  På fliken **Säkerhet** klickar du på **Lokalt intranät** och därefter på **Platser**. Klicka sedan på **Avancerat** och lägg till URL-adressen (http://*WSUSServername*/WSUSAdmin). Klicka därefter på **OK**.
3.  Klicka på **Tillförlitliga platser** och sedan på **Platser**. Lägg till URL-adressen för WSUS-konsolen och klicka på **OK**. Stäng sedan **Internet-alternativ** genom att klicka på **OK** igen.

#### Problem 20: Uppgradering från versionskandidat av WSUS misslyckas

Uppgradering från versionskandidaten för WSUS kan misslyckas till följd av problem med trädvyn för automatisk uppdatering. Problemet kan uppstå om flera klienter uppdateras automatiskt samtidigt som du försöker uppgradera.

Så här löser du problemet:

1.  Koppla bort WSUS-servern från nätverket så att klienterna inte kan ansluta till den.
2.  Skriv följande kommando i kommandotolken: **iisrestart /reset** och tryck sedan på RETUR.
3.  Kör uppgraderingen.

#### Problem 21: Vissa godkännanden från SUS 1.0 kan inte överföras till WSUS.

När du migrerar från SUS 1.0 till WSUS går det inte att överföra alla godkännanden från SUS 1.0-servern till WSUS-servern. Det beror på att ett antal uppdateringar som fanns tillgängliga för SUS 1.0 inte längre finns tillgängliga för WSUS. Eftersom WSUS hanterar fler uppdateringar än SUS kan det dessutom finnas viktiga uppdateringar på WSUS-servern som inte är godkända när migreringen är slutförd.

Microsoft rekommenderar dig att granska dessa icke godkända uppdateringar på WSUS-servern efter att du har migrerat från SUS 1.0.

Mer information om migrering från SUS 1.0 till WSUS finns i [instruktionerna för hur du migrerar från SUS (Software Update Services) till WSUS (Windows Server Update Services)](http://go.microsoft.com/fwlink/?linkid=48042) på http://go.microsoft.com/fwlink/?LinkId=48042.

#### Problem 22: Åtgärda den här registerposten innan du uppgraderar till WSUS 2.0 Service Pack 1 om du har migrerat WMSDE till SQL Server

Om du tänker uppgradera WSUS 2.0 till Service Pack 1 och har migrerat WMSDE-installationen till SQL Server (fjärrstyrd eller lokal) bör du se till att åtgärda följande registerpost:

HKLM\\Software\\Microsoft\\Update Services\\Server\\Setup\\WmsdeInstalled

Värdet bör ändras från 1 till 0.

#### Problem 23: Migrera en SQL-fjärrinstallation till WSUS 2.0 Service Pack 1

Så här migrerar du till WSUS 2.0 Service Pack 1 med en SQL-fjärrkonfiguration:

1) Kör installationspaketet på klientdatorn utan växlar och välj uppgradering.

2) Kör installationspaketet på serverdatorn utan växlar och välj uppgradering.

#### Copyright

Informationen i det här dokumentet visar Microsoft Corporations aktuella hållning i de ämnen som tas upp vid publiceringstillfället. Eftersom Microsoft snabbt måste agera efter förändringar på marknaden ska den inte tolkas som bindande från Microsofts sida, och Microsoft kan inte heller garantera korrektheten i informationen efter publiceringsdatumet.

Det här dokumentet är endast avsett som information. MICROSOFT GER INGA GARANTIER, UTTRYCKLIGA, UNDERFÖRSTÅDDA ELLER LAGSTADGADE, VAD GÄLLER INFORMATIONEN I DET HÄR DOKUMENTET.

Ansvaret för att följa upphovsrättslagar ligger på användaren. Ingen del av det här dokumentet får reproduceras, lagras eller infogas i ett informationssystem eller överföras i någon form, med något medel (elektroniska eller mekaniska medier, fotokopiering, inspelning eller någon annan form av reproduktion) eller för något ändamål utan uttrycklig skriftlig tillåtelse från Microsoft Corporation.

För innehållet i det här dokumentet kan Microsoft inneha patent, patentansökningar, varumärken, copyright eller andra rättigheter som regleras av upphovsrättslagar. Innehav av detta dokument medför inga rättigheter till patent, varumärken, copyright eller andra upphovsrättsskyddade produkter utöver vad som uttryckligen anges i ett skriftligt licensavtal med Microsoft.

Om inget annat anges är de exempel på företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser som nämns i det här dokumentet påhittade, och alla eventuella kopplingar till verkliga företag, organisationer, produkter, domännamn, e-postadresser, logotyper, personer, platser och händelser är helt oavsiktliga.

© 2005 Microsoft Corporation. Med ensamrätt.

Microsoft, SQL Server, Windows och Windows Server är antingen registrerade varumärken eller varumärken som tillhör Microsoft Corporation i USA och eller andra länder.

Namnen på befintliga företag och produkter som nämns här kan vara varumärken som tillhör respektive ägare.
