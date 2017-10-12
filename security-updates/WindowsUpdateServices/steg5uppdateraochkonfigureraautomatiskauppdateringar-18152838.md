---
TOCTitle: 'Steg 5: Uppdatera och konfigurera automatiska uppdateringar'
Title: 'Steg 5: Uppdatera och konfigurera automatiska uppdateringar'
ms:assetid: '4ac8d574-f48e-4d9d-86c9-9aeb0f57e750'
ms:contentKeyID: 18152838
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720533(v=WS.10)'
---

Steg 5: Uppdatera och konfigurera automatiska uppdateringar
===========================================================

För WSUS-klientdatorer krävs en kompatibel version av Automatiska uppdateringar. När WSUS installeras konfigureras IIS automatiskt för distribution av den senaste versionen av Automatiska uppdateringar till de klientdatorer som ska kontakta WSUS-servern.

| ![](images/Cc720533.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du kan för de flesta versionerna av Automatiska uppdateringar ange en sökväg till WSUS-servern och programversionerna uppdateras automatiskt till den WSUS-kompatibla versionen. Den version av Automatiska uppdateringar som ingår i Windows XP utan Service Packs kan emellertid inte uppdateras automatiskt. Om du har Windows XP utan Service Packs i nätverksmiljön och aldrig tidigare har använt SUS (Software Update Services) går du till dokumentet “Deploying Microsoft Windows Server Update Services” (på engelska) för vidare instruktioner. |

Vilket sätt som bäst lämpar sig för konfigurering av Automatiska uppdateringar beror på nätverksmiljön. I en Active Directory-miljö kan du använda ett Active Directory-baserat grupprincipobjekt (GPO). I en miljö utan Active Directory använder du det lokala grupprincipobjektet. Oavsett om du använder det lokala grupprincipobjektet eller ett GPO som är lagrat på en domänkontrollant, måste du peka ut WSUS-servern i klientdatorernas konfiguration och sedan konfigurera Automatiska uppdateringar.

Följande instruktioner förutsätter att Active Directory körs i nätverket. Procedurerna förutsätter även att du redan har konfigurerat och kan använda grupprinciper och använder sådana i nätverket. Du måste skapa ett nytt GPO (grupprincipobjekt) för WSUS-inställningar och länka objektet till domännivån.

Mer information om grupprinciper finns på sidan om [Group Policy](http://go.microsoft.com/fwlink/?linkid=47375) på http://go.microsoft.com/fwlink/?LinkID=47375 (texten kan vara på engelska).

Steg 5 innehåller följande procedurer:

-   Läsa in den administrativa mallen för WSUS.
-   Konfigurera Automatiska uppdateringar.
-   Peka ut WSUS-servern i klientdatorernas konfigurationer.
-   Initiera identifiering på klientdatorn manuellt.

Utföra nästföljande tre procedurer på ett Active Directory-baserat GPO.

**Så här lägger du till den administrativa mallen för WSUS**
1.  I objektredigeraren för gruppprinciper klickar du på någon av noderna för **administrativa mallar**.

2.  Klicka på **Lägg till/ta bort mallar** på **Åtgärd**-menyn.

3.  Klicka på **Lägg till**.

4.  I dialogrutan **Principmallar** klickar du på **wuau.adm** och därefter på **Öppna**.

5.  Klicka på **Stäng** i dialogrutan **Lägg till/ta bort mallar**.

**Så här konfigurerar hur automatiska uppdateringar ska fungera**
1.  I objektredigeraren för grupprinciper expanderar du **Datorkonfiguration**, därefter **Administrativa mallar**, sedan **Windows-komponenter** och klickar därefter på **Windows Update**.

2.  Dubbelklicka på **Konfigurera automatiska uppdateringar** i informationsfönstret.

3.  Klicka på **Aktiverad** och gör sedan något av följande:

    -   **Meddela om hämtning och installation.** När du väljer det här alternativet meddelas en inloggad administratör före hämtning och installation av uppdateringarna.
    -   **Hämta automatiskt och meddela om installation.** När du väljer det här alternativet hämtas uppdateringarna automatiskt och därefter meddelas inloggade administratörer före installation.
    -   **Hämta automatiskt och schemalägg installationen.** Om Automatiska uppdateringar har konfigurerats för schemalagd installation måste du även ange dag och tidpunkt när installationen ska ske.
    -   **Låt lokala adminstratörer välja.** Med det här alternativet kan lokala administratörer använda Automatiska uppdateringar på Kontrollpanelen och själva välja konfigurationsalternativ. De kan till exempel välja en egen tidpunkt för schemalagd installation. Lokala administratörer kan inte inaktivera Automatiska uppdateringar.

4.  Klicka på **OK**.

| ![](images/Cc720533.note(WS.10).gif)Obs!                                                                                              |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Alternativet **Låt lokala adminstratörer välja** visas endast om Automatiska uppdateringar automatiskt har uppdaterats till en version som är kompatibel med WSUS. |

**Så här pekar du ut WSUS-servern i klientdatorns konfiguration**
1.  I objektredigeraren för grupprinciper expanderar du **Datorkonfiguration**, därefter **Administrativa mallar**, sedan **Windows-komponenter** och klickar därefter på **Windows Update**.

2.  Klicka på **Ange sökväg till tjänsten Microsoft Update på intranätet** i informationsfönstret.

3.  Klicka på **Aktiverad** och ange URL:en för samma WSUS-server i rutan **Ange intranätserver för identifiering av uppdateringar** och i rutan **Ange intranätserver för statistik** . Skriv till exempel **http://***servernamn* i båda rutorna.

4.  Klicka på **OK**.

| ![](images/Cc720533.note(WS.10).gif)Obs!                                                                                                                                                                                                        |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du använder det lokala grupprincipobjektet för att ange en sökväg från datorn till WSUS, träder inställningen omedelbart i kraft och datorn visas i WSUS-konsolen efter ungefär 20 minuter. Du kan påskynda processen genom att initiera en identifieringscykel manuellt. |

När du har installerat och konfigurerat en klientdator tar det några minuter innan den visas på sidan **Datorer** i WSUS-konsolen. För klientdatorer som har konfigurerats med ett Active Directory-baserat grupprincipobjekt, tar det omkring 20 minuter efter att grupprincipen uppdateras (d.v.s. använder eventuella nya inställningar för klientdatorn). Som standard uppdateras grupprincipen i bakgrunden var 90:e minut med en slumpmässig avvikelse på 0 till 30 minuter. Om du vill uppdatera grupprincipen oftare än så kan du gå till kommandotolken på klientdatorn och skriva: **gpupdate /force**.

För klientdatorer som har konfigurerats med det lokala grupprinicpobjektet används grupprincipen omedelbart och det tar ungefär 20 minuter.

När grupprincipen har använts kan du initiera identifiering manuellt. Om du utför det här steget behöver du inte vänta 20 minuter på att klientdatorn ska kontakta WSUS.

**Så här initierar du manuellt identifiering från WSUS server**
1.  Klicka på **Start** på klientdatorn och sedan på **Kör**.

2.  Skriv **cmd** och klicka sedan på **OK**.

3.  I kommandotolken skriver du **wuauclt.exe /detectnow**. Det här kommandoradsalternativet anger att Automatiska uppdateringar direkt ska kontakta WSUS-servern.
