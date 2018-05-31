---
TOCTitle: 'Steg 3: Konfigurera nätverksanslutningarna'
Title: 'Steg 3: Konfigurera nätverksanslutningarna'
ms:assetid: '42a144c5-f08e-4a6e-b360-47ddea77bd24'
ms:contentKeyID: 21799551
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939815(v=WS.10)'
---

Steg 3: Konfigurera nätverksanslutningarna
==========================================

När du har installerat Windows Server Update Services 3.0 Service Pack 2 (WSUS 3.0 SP2) startas konfigurationsguiden automatiskt. Du kan också köra guiden senare på sidan **Alternativ** i administrationskonsolen för WSUS.

Innan du påbörjar konfigureringen måste du se till att du har svaren på följande frågor:

1. Är serverns brandvägg konfigurerad så att klienterna kan få tillgång till servern?

2. Kan den här datorn ansluta till den överordnade servern (till exempel Microsoft Update)?

3. Har du namnet på proxyservern och användarautentiseringsuppgifterna för proxyservern till hands, om du skulle behöva dem?

Som standard är WSUS 3.0 SP2 konfigurerat för att hämta uppdateringar från Microsoft Update. Om det finns en proxyserver i nätverket kan du konfigurera WSUS 3.0 SP2 för att använda proxyservern. Om det finns en brandvägg mellan WSUS och Internet kan du behöva konfigurera den så att det går att hämta uppdateringar till WSUS.

 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939815.note(WS.10).gif" />Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Även om det krävs Internetanslutning för att hämta uppdateringar från Microsoft Update, kan du med WSUS importera uppdateringar till nätverk som inte är anslutna till Internet.
</td>
</tr>
</tbody>
</table>
 

Steg 3 innehåller följande procedurer:

-   Konfigurera brandväggen.
-   Ange hur servern ska hämta uppdateringarna (från Microsoft Update eller från en annan WSUS-server).
-   Konfigurera proxyserverinställningar så att uppdateringar kan hämtas till WSUS.

**Så här konfigurerar du brandväggen**
-   Om företaget har en brandvägg mellan WSUS och Internet kan du behöva konfigurera den så att uppdateringar kan hämtas till WSUS. WSUS-servern använder port 80 för HTTP-protokollet och port 443 för HTTPS-protokollet när uppdateringar hämtas från Microsoft Update. Inställningarna är inte konfigurerbara.

-   Om organisationen inte tillåter att port 80 eller 443 öppnas för alla adresser kan du begränsa åtkomsten till att gälla följande domäner, så att kommunikationen fungerar mellan WSUS, Automatiska uppdateringar och Microsoft Update:

    -   http://windowsupdate.microsoft.com
    -   http://\*.windowsupdate.microsoft.com
    -   https://\*.windowsupdate.microsoft.com
    -   http://\*.update.microsoft.com
    -   https://\*.update.microsoft.com
    -   http://\*.windowsupdate.com
    -   http://download.windowsupdate.com
    -   http://download.microsoft.com
    -   http://\*.download.windowsupdate.com
    -   http://wustat.windows.com
    -   http://ntservicepack.microsoft.com

 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939815.note(WS.10).gif" />Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Dessa instruktioner om hur du konfigurerar brandväggen avser företagsbrandväggar som är placerade mellan WSUS och Internet. Eftersom all nätverkstrafik till och från WSUS initieras av WSUS behöver du inte konfigurera Windows-brandväggen på WSUS-servern.
</td>
</tr>
</tbody>
</table>
 

Även om anslutningen mellan Microsoft Update och WSUS kräver att portarna 80 och 443 är öppna, kan du konfigurera flera WSUS-server för synkronisering med en egen port.

I de följande två procedurerna förutsätts det att du använder konfigurationsguiden. I ett senare avsnitt i det här steget får du lära dig att starta snapin-modulen Administration av WSUS och konfigurera servern på sidan Alternativ.

**Så här anger du hur servern ska hämta uppdateringar**
1.  Välj överordnad server genom att klicka på **Nästa** i konfigurationsguiden efter att du har gått med i programmet för kvalitetsförbättring av Microsoft Update.

2.  Om du väljer att synkronisera från Microsoft Update är du klar med sidan Alternativ. Klicka på **Nästa** eller välj **Ange proxyserver** i navigeringsfönstret.

3.  Om du väljer att synkronisera från en annan WSUS-server, anger du servernamnet och porten som servern använder för att kommunicera med den överordnade servern.

4.  Om du vill använda SSL markerar du kryssrutan **Använd SSL vid synkronisering av uppdateringsinformation**. I så fall ska servrarna använda port 443 för synkroniseringen. (Kontrollera att både den här servern och den överordnade servern stöder SSL.)

5.  Om detta är en replikserver markerar du kryssrutan **Det här är en replik av den överordnade servern**.

6.  Du är nu klar med konfigurationen av den överordnade servern. Klicka på **Nästa** eller välj **Ange proxyserver** i det vänstra navigeringsfönstret.

**Så här konfigurerar du inställningar för proxyserver**
1.  Markera kryssrutan **Använd en proxyserver vid synkronisering** på sidan **Ange proxyserver** i konfigurationsguiden och skriv sedan proxyserverns namn och portnummer (port 80 som standard) i motsvarande rutor.

2.  Om du vill ansluta till proxyservern med särskild användaridentifiering markerar du kryssrutan **Använd användaridentifiering för att ansluta till proxyservern** och anger sedan användarnamn, domän och användarens lösenord i respektive rutor. Om du vill aktivera grundläggande autentisering för användaranslutningen till proxyservern markerar du kryssrutan **Tillåt grundläggande autentisering (lösenordet skickas i klartext)**.

3.  Du är nu klar med konfigurationen av proxyservern. Klicka på **Nästa** för att gå till nästa sida, där du kan börja konfigurera synkroniseringsprocessen.

I de följande två procedurerna förutsätts det att du använder snapin-modulen Administration av WSUS för konfigurationen. I de här två procedurerna visas hur du startar snapin-modulen Administration av WSUS och konfigurerar servern på sidan **Alternativ**.

**Så här startar du administrationskonsolen för WSUS**
-   Starta administrationskonsolen för WSUS genom att klicka på **Start**, peka på **Alla program**, på **Administrationsverktyg** och sedan klicka på **Microsoft Windows Server Update Services 3.0**.

 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939815.note(WS.10).gif" />Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Om du ska kunna använda alla funktioner i konsolen måste du logga in som medlem av säkerhetsgruppen WSUS-administratörer eller den lokala säkerhetsgruppen Administratörer på den server där WSUS har installerats. Medlemmar av säkerhetsgruppen WSUS-rapportörer har skrivskyddad åtkomst till konsolen.
</td>
</tr>
</tbody>
</table>
 

**Så här anger du en uppdateringskälla och proxyserver**
1.  Klicka på **Alternativ** i det vänstra fönstret under namnet på den här servern i WSUS-konsolen och klicka sedan på **Uppdateringskälla och proxyserver** i fönstret i mitten.

    En dialogruta med flikarna **Uppdateringskälla** och **Proxyserver** visas.

2.  Välj varifrån den här servern ska hämta uppdateringar på fliken **Uppdateringskälla**. Om du väljer att synkronisera från Microsoft Update (standardvärdet) är du klar i och med denna guidesida.

3.  Om du väljer att synkronisera från en annan WSUS-server måste du ange den port som servrarna ska kommunicera genom (standardvärdet är port 80). Om du väljer en annan port måste du se till att båda servrarna kan använda den porten.

4.  Du kanske också måste ange om du vill använda SSL när du synkroniserar från den överordnade WSUS-servern. I så fall kommer användarna att använda port 443 när de synkroniserar från den överordnade servern.

5.  Om den här servern är en replik av den andra WSUS-servern markerar du kryssrutan **Det här är en replik av den överordnade servern**. I detta fall måste alla uppdateringar bara godkännas på den överordnade WSUS-servern.

6.  På fliken **Proxyserver** markerar du kryssrutan **Använd proxyserver vid synkronisering** och skriver sedan proxyserverns namn och portnummer (standard är port 80) i respektive rutor.

7.  Om du vill ansluta till proxyservern med särskild användaridentifiering markerar du kryssrutan **Använd användaridentifiering för att ansluta till proxyservern** och anger sedan användarnamn, domän och användarens lösenord i respektive rutor. Om du vill aktivera grundläggande autentisering för användare som ansluter till proxyservern markerar du kryssrutan **Tillåt grundläggande autentisering (lösenordet skickas i klartext)**.

8.  Spara inställningarna genom att klicka på **OK**.

Nästa steg
----------

[Steg 4: Konfigurera uppdateringar och synkronisering](https://technet.microsoft.com/deeaa7e1-9b50-45cb-9537-d75f70de3405).

Ytterligare resurser
--------------------

[Steg-för-steg-guide för Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)
