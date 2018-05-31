---
TOCTitle: 'Steg 5: Konfigurera Automatiska uppdateringar'
Title: 'Steg 5: Konfigurera Automatiska uppdateringar'
ms:assetid: '5da6d10a-6ff1-4de8-b53a-4893bf8bd9fa'
ms:contentKeyID: 18152792
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720532(v=WS.10)'
---

Steg 5: Konfigurera Automatiska uppdateringar
=============================================

För WSUS-klientdatorer krävs en kompatibel version av Automatiska uppdateringar. När WSUS installeras konfigureras IIS automatiskt för distribution av den senaste versionen av Automatiska uppdateringar till de klientdatorer som ska kontakta WSUS-servern.

Vilket sätt som bäst lämpar sig för konfigurering av Automatiska uppdateringar beror på nätverksmiljön. I en Active Directory-miljö kan du använda ett domänbaserat grupprincipobjekt (GPO). I en miljö utan Active Directory använder du det lokala grupprincipobjektet. Oavsett om du använder det lokala grupprincipobjektet eller ett domänbaserat GPO, måste du peka ut WSUS-servern i klientdatorernas konfiguration och sedan konfigurera Automatiska uppdateringar.

Följande instruktioner förutsätter att Active Directory körs i nätverket. Procedurerna förutsätter även att du kan använda grupprinciper och använder sådana i nätverket. Du måste skapa ett nytt GPO för WSUS-inställningar och länka objektet till domänen.

Mer information om grupprinciper finns på webbplatsen Group Policy Tech Center ([http://go.microsoft.com/fwlink/?LinkID=47375](http://go.microsoft.com/fwlink/?linkid=47375)).

**Steg 5 innehåller följande procedurer**:

-   Lägga till den administrativa mallen för WSUS.
-   Konfigurera Automatiska uppdateringar.
-   Peka ut klientdatorn för WSUS-servern.
-   Manuellt initiera identifiering från WSUS-servern.

Utför de första tre procedurerna på ett domänbaserat GPO. Du måste skapa ett nytt GPO eller använda ett befintligt. Om du använder Group Policy Management Console (GPMC) när du hanterar grupprincipobjekt navigerar du till det GPO som du vill ändra och klickar sedan på **Redigera**.

För att kunna visa principinställningar när du hanterar WSUS måste du se till att den administrativa mallen för WSUS, wuau.adm, har lagts till i redigeraren för grupprincipobjekt. Eftersom wuau.adm finns som standard i operativsystemet bör den redan finnas i redigeraren för grupprincipobjekt.

**Så här lägger du till den administrativa mallen för WSUS**
1.  I objektredigeraren för grupprinciper klickar du på någon av noderna för **administrativa mallar**.

2.  Klicka på **Lägg till/ta bort mallar** på **Åtgärd**-menyn och klicka sedan på **Lägg till**.

3.  I dialogrutan **Principmallar** klickar du på **wuau.adm** och därefter på **Öppna**.

4.  Klicka på **Stäng** i dialogrutan **Lägg till/ta bort mallar**.

**Så här konfigurerar du Automatiska uppdateringar**
1.  I objektredigeraren för grupprinciper expanderar du **Datorkonfiguration**, därefter **Administrativa mallar**, sedan **Windows-komponenter** och klickar därefter på **Windows Update**.

2.  Dubbelklicka på **Konfigurera automatiska uppdateringar** i informationsfönstret.

3.  Klicka på **Aktiverad** och gör sedan något av följande:

    -   **Meddela om hämtning och installation**: När du väljer det här alternativet meddelas en inloggad administratör innan hämtningen börjar och innan uppdateringarna installeras.
    -   **Hämta automatiskt och meddela om installation**: När du väljer det här alternativet hämtas uppdateringarna automatiskt och därefter meddelas inloggade administratörer före installation.
    -   **Hämta automatiskt och schemalägg installationen**: Om Automatiska uppdateringar har konfigurerats för schemalagd installation måste du även ange dag och tidpunkt för när installationen ska ske.
    -   **Låt lokala administratörer välja**: Med det här alternativet kan lokala administratörer använda Automatiska uppdateringar på Kontrollpanelen och själva välja konfigurationsalternativ. De kan till exempel välja en egen tidpunkt för schemalagd installation. Lokala administratörer kan inte inaktivera Automatiska uppdateringar.

4.  Klicka på **OK**.

| ![](images/Cc720532.note(WS.10).gif)Obs!                                                                                             |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Alternativet **Låt lokala administratörer välja** visas bara om Automatiska uppdateringar automatiskt har uppdaterats till en version som är kompatibel med WSUS. |

**Så här pekar du ut klientdatorn för WSUS-servern**
1.  I objektredigeraren för grupprinciper expanderar du **Datorkonfiguration**, därefter **Administrativa mallar**, sedan **Windows-komponenter** och klickar därefter på **Windows Update**.

2.  Klicka på **Ange sökväg till tjänsten Microsoft Update på intranätet** i informationsfönstret.

3.  Klicka på **Aktiverad** och ange URL:en för samma WSUS-server i rutan **Ange intranätserver för identifiering av uppdateringar** och i rutan **Ange intranätserver för statistik**. Skriv till exempel *http://servernamn* i båda rutorna och klicka på **OK**.

| ![](images/Cc720532.note(WS.10).gif)Obs!                                                                                                                                                                                                   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du använder det lokala grupprincipobjektet för att ange en sökväg från datorn till WSUS, träder inställningen omedelbart i kraft och datorn visas i WSUS-konsolen efter en kort stund. Du kan påskynda processen genom att initiera en identifieringscykel manuellt. |

När du har installerat och konfigurerat en klientdator tar det några minuter innan den visas på sidan **Datorer** i WSUS-konsolen. För klientdatorer som har konfigurerats med ett domänbaserat grupprincipobjekt, tar det omkring 20 minuter efter att grupprincipen uppdateras (d.v.s. använder eventuella nya inställningar för klientdatorn). Som standard uppdateras grupprincipen i bakgrunden var 90:e minut med en slumpmässig avvikelse på 0 till 30 minuter. Om du vill uppdatera grupprincipen oftare än så kan du gå till kommandotolken på klientdatorn och skriva: **gpupdate /force**.

För klientdatorer som har konfigurerats med det lokala grupprincipobjektet används grupprincipen omedelbart och uppdateringen tar ungefär 20 minuter.

När grupprincipen har använts kan du initiera identifiering manuellt. Om du initierar identifieringen manuellt behöver du inte vänta 20 minuter på att klientdatorn ska kontakta WSUS.

**Så här initierar du manuellt identifiering från WSUS server**
1.  Klicka på **Start** på klientdatorn och sedan på **Kör**.

2.  Skriv **cmd** i rutan **Öppna** och klicka sedan på **OK**.

3.  I kommandotolken skriver du **wuauclt.exe /detectnow**. Det här kommandoradsalternativet anger att Automatiska uppdateringar direkt ska kontakta WSUS-servern.
