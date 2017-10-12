---
TOCTitle: 'Steg 3: Konfigurera nätverksanslutningen'
Title: 'Steg 3: Konfigurera nätverksanslutningen'
ms:assetid: 'cd77566d-7780-4ce4-aa56-41183c65c4a7'
ms:contentKeyID: 18152992
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708559(v=WS.10)'
---

Steg 3: Konfigurera nätverksanslutningen
========================================

När du har installerat WSUS är det dags att gå till WSUS-konsolen, konfigurera WSUS och komma igång. Som standard är WSUS konfigurerat för att hämta uppdateringar från Microsoft Update. Om det finns en proxyserver på nätverket använder du WSUS-konsolen och konfigurerar WSUS för att använda proxyservern. Om det finns en brandvägg mellan WSUS och Internet kan du behöva konfigurera den så att uppdateringar kan hämtas.

| ![](images/Cc708559.note(WS.10).gif)Obs!                                                                                                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du måste ha en Internet-anslutning för att kunna hämta uppdateringar från Microsoft Update. Med WSUS kan du importera uppdateringar även till nätverk som inte är anslutna till Internet. Mer information finns i vitboken “Deploying Microsoft Windows Server Update Services” (på engelska). |

Steg 3 innehåller följande procedurer:

-   Konfigurera brandväggen så att uppdateringar kan hämtas.
-   Öppna WSUS-konsolen.
-   Konfigurera proxyserverinställningar så att uppdateringar kan hämtas.

**Så här konfigurerar du brandväggen**
-   Om företaget har en brandvägg mellan WSUS och Internet kan du behöva konfigurera den så att uppdateringar kan hämtas. WSUS-servern använder port 80 för HTTP-protokollet och port 443 för HTTPS-protokollet när uppdateringar hämtas från Microsoft Update. Inställningarna är inte konfigurerbara.

-   Om organisationen inte tillåter att dessa portar och protokoll används för att öppna alla adresser, kan du begränsa åtkomsten till att gälla följande domäner. Då fungerar kommunikationen mellan WSUS, Automatiska uppdateringar och Microsoft Update:

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

| ![](images/Cc708559.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ovanstående instruktioner om hur du konfigurerar brandväggen avser företagsbrandväggar som är placerade mellan WSUS och Internet. Eftersom all nätverkstrafik till och från WSUS initieras av WSUS behöver du inte konfigurera Windows Firewall på WSUS-servern. Även om anslutningen mellan Microsoft Update och WSUS kräver att portarna 80 och 443 är öppna, kan du konfigurera flera WSUS-server för synkronisering med en egen port. Mer information om hur du synkroniserar WSUS-servrar med hjälp av en egen port finns i vitboken “Deploying Microsoft Windows Server Update Services”. |

**Så här öppnar du WSUS-konsolen**
-   Klicka på **Start** på WSUS-servern, peka på **Alla program** och därefter på **Administrativa verktyg**. Klicka därefter på **Microsoft Windows Server Update Services**.

| ![](images/Cc708559.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du måste vara medlem i säkerhetsgruppen WSUS-administratörer eller den lokala säkerhetsgruppen Administratörer på den server där WSUS är installerat för att kunna använda WSUS-konsolen. Om du inte lägger till **http://&lt;***WSUS-webbplatsens namn***&gt;** i listan över webbplatser i zonen Lokalt intranät i Internet Explorer på Windows Server 2003, blir du ombedd att ange inloggningsinformation varje gång du öppnar WSUS-konsolen. Om du ändrar porttilldelningen i IIS efter att du har installerat WSUS, måste du uppdatera genvägen på **Start**-menyn manuellt. Du kan även öppna WSUS-konsolen från Internet Explorer på valfri server eller dator i nätverket genom att ange följande URL: **http://***WSUSservernamn***/WSUSAdmin** |

**Så här anger du en proxyserver**
1.  Klicka på **Alternativ** och därefter på **Synkroniseringsalternativ** i WSUS-konsolens verktygsfält.

2.  I rutan **Proxyserver** markerar du kryssrutan **Använd proxyserver vid synkronisering** och skriver sedan proxyserverns namn och portnummer (standard är port 80) i respektive rutor.

3.  Om du vill ansluta till proxyservern med särskild användaridentifiering, markerar du kryssrutan **Använd användaridentifiering för att ansluta till proxyservern** och anger sedan användarnamn, domän och användarens lösenord i respektive rutor. Om du vill aktivera grundläggande autentisering för användare som ansluter till proxyservern, markerar du kryssrutan **Tillåt grundläggande autentisering (lösenordet skickas i klartext)**.

4.  Klicka på **Spara inställningar** under **Aktiviteter** och klicka därefter på **OK** i bekräftelsedialogrutan.
