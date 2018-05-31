---
TOCTitle: 'Steg 3: Konfigurera nätverksanslutning för WSUS 3.0'
Title: 'Steg 3: Konfigurera nätverksanslutning för WSUS 3.0'
ms:assetid: 'dbc9d9f7-cf52-4539-9f9e-3e823273218a'
ms:contentKeyID: 18152962
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708602(v=WS.10)'
---

Steg 3: Konfigurera nätverksanslutning för WSUS 3.0
===================================================

När du har installerat WSUS 3.0 startas konfigurationsguiden automatiskt. Du kan även starta guiden senare på sidan **Alternativ** i WSUS 3.0-konsolen.

Innan du börjar att konfigurera ser du till att du har svaren på följande frågor:

1. Är serverns brandvägg konfigurerad så att klienterna kan få tillgång till servern?

2. Kan den här datorn ansluta till den överordnade servern (till exempel Microsoft Update)?

3. Har du namnet på proxyservern och användaridentifieringen för proxyservern till hands, om detta behövs?

Som standard är WSUS konfigurerat för att hämta uppdateringar från Microsoft Update. Om det finns en proxyserver i nätverket kan du konfigurera WSUS för att använda proxyservern. Om det finns en brandvägg mellan WSUS och Internet kan du behöva konfigurera den så att uppdateringar kan hämtas.

| ![](images/Cc708602.note(WS.10).gif)Obs!                                                                                                                     |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du måste ha en Internet-anslutning för att kunna hämta uppdateringar från Microsoft Update. Med WSUS kan du importera uppdateringar även till nätverk som inte är anslutna till Internet. |

**Steg 3 innehåller följande procedurer**:

-   Konfigurera brandväggen.
-   Ange hur servern ska hämta uppdateringarna (från Microsoft Update eller från en annan WSUS-server).
-   Konfigurera proxyserverinställningar så att uppdateringar kan hämtas.

**Så här konfigurerar du brandväggen**
-   Om företaget har en brandvägg mellan WSUS och Internet kan du behöva konfigurera den så att uppdateringar kan hämtas. WSUS-servern använder port 80 för HTTP-protokollet och port 443 för HTTPS-protokollet när uppdateringar hämtas från Microsoft Update. Inställningarna är inte konfigurerbara.

-   Om organisationen inte tillåter att port 80 eller 443 är öppna för alla adresser kan du begränsa åtkomsten till att gälla följande domäner. Då fungerar kommunikationen mellan WSUS, Automatiska uppdateringar och Microsoft Update:

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

| ![](images/Cc708602.note(WS.10).gif)Obs!                                                                                                                                                                                      |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dessa instruktioner om hur du konfigurerar brandväggen avser företagsbrandväggar som är placerade mellan WSUS och Internet. Eftersom all nätverkstrafik till och från WSUS initieras av WSUS behöver du inte konfigurera Windows Firewall på WSUS-servern. |

Även om anslutningen mellan Microsoft Update och WSUS kräver att portarna 80 och 443 är öppna, kan du konfigurera flera WSUS-server för synkronisering med en egen port.

I de följande två procedurerna förutsätts det att du använder konfigurationsguiden. I ett senare avsnitt i det här steget får du lära dig att starta snapin-modulen Administration av WSUS och konfigurera servern på sidan **Alternativ**.

**Så här anger du hur servern ska hämta uppdateringar**
1.  Välj överordnad server genom att klicka på **Nästa** i konfigurationsguiden efter att du har gått med i Microsofts förbättringsprogram.

2.  Om du väljer att synkronisera från Microsoft Update är du klar i och med denna sida. Klicka på **Nästa** eller välj **Ange proxyserver** i det vänstra fönstret.

3.  Om du väljer att synkronisera från en annan WSUS-server, anger du servernamnet och porten som servern använder för att kommunicera med den överordnade servern.

4.  Om du vill använda SSL markerar du kryssrutan **Använd SSL vid synkronisering av uppdateringsinformation**. I så fall ska servrarna använda port 443 för synkroniseringen. (Kontrollera att både den här servern och den överordnade servern stöder SSL.)

5.  Om det är en replikserver markerar du kryssrutan **Det här är en replik av den överordnade servern**.

6.  Vid den här punkten är du klar med konfigurationen av den överordnade servern. Klicka på **Nästa** eller välj **Ange proxyserver** i den vänstra panelen.

**Så här konfigurerar du inställningar för proxyserver**
1.  Markera kryssrutan **Använd en proxyserver vid synkronisering** på sidan **Ange proxyserver** i konfigurationsguiden och skriv sedan proxyserverns namn och portnummer (port 80 som standard) i motsvarande rutor.

2.  Om du vill ansluta till proxyservern med särskild användaridentifiering markerar du kryssrutan **Använd användaridentifiering för att ansluta till proxyservern** och anger sedan användarnamn, domän och användarens lösenord i respektive rutor. Om du vill aktivera grundläggande autentisering för användaranslutningen till proxyservern markerar du kryssrutan **Tillåt grundläggande autentisering (lösenordet skickas i klartext)**.

3.  Vid den här punkten är du klar med konfigurationen av proxyservern. Klicka på **Nästa** för att gå till nästa sida där du gör inställningar för synkroniseringen.

I de följande två procedurerna förutsätts det att du använder snapin-modulen Administration av WSUS för konfigurationen. I dessa två procedurer visas hur du startar snapin-modulen Administration av WSUS och konfigurerar servern på sidan **Alternativ**.

**Så här startar du WSUS-administratörskonsolen**
-   Klicka på **Start**, peka på **Alla program** och därefter på **Administrativa verktyg**. Klicka därefter på **Microsoft Windows Server Update Services 3.0**.

| ![](images/Cc708602.note(WS.10).gif)Obs!                                                                                                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| För att kunna använda alla funktioner i WSUS-konsolen måste du tillhöra säkerhetsgruppen WSUS-administratörer eller den lokala gruppen Administratörer på servern där WSUS installeras. De som tillhör säkerhetsgruppen WSUS-rapportörer har skrivskyddad åtkomst till administratörskonsolen. |

**Så här anger du en uppdateringskälla och proxyserver**
1.  Klicka på **Alternativ** i den vänstra panelen i WSUS-konsolen, under namnet på den här servern, och klicka sedan på **Uppdateringskälla och proxyserver** i den mellersta panelen.

2.  En dialogruta med flikarna **Uppdateringskälla** och **Proxyserver** visas.

3.  Välj varifrån den här servern ska hämta uppdateringar på fliken **Uppdateringskälla**. Om du väljer att synkronisera från Microsoft Update (standardvärdet) är du klar i och med denna guidesida.

4.  Om du väljer att synkronisera från en annan WSUS-server måste du ange porten som servrarna ska kommunicera genom (standardvärdet är port 80). Om du väljer en annan port måste du se till att båda servrarna kan använda den porten.

5.  Du kanske också måste ange om du vill använda SSL när du synkroniserar från den överordnade WSUS-servern. I så fall kommer användarna att använda port 443 när de synkroniserar från den överordnade servern.

6.  Om den här servern är en replik av den andra WSUS-servern markerar du kryssrutan **Det här är en replik av den överordnade servern**. I detta fall måste alla uppdateringar bara godkännas på den överordnade WSUS-servern.

7.  På fliken **Proxyserver** markerar du kryssrutan **Använd proxyserver vid synkronisering** och skriver sedan proxyserverns namn och portnummer (standard är port 80) i respektive rutor.

8.  Om du vill ansluta till proxyservern med särskild användaridentifiering markerar du kryssrutan **Använd användaridentifiering för att ansluta till proxyservern** och anger sedan användarnamn, domän och användarens lösenord i respektive rutor. Om du vill aktivera grundläggande autentisering för användare som ansluter till proxyservern markerar du kryssrutan **Tillåt grundläggande autentisering (lösenordet skickas i klartext)**.

9.  Spara inställningarna genom att klicka på **OK**.
