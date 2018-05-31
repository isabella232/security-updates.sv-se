---
TOCTitle: 'Steg 5: Konfigurera klientuppdateringar'
Title: 'Steg 5: Konfigurera klientuppdateringar'
ms:assetid: '5ae60ead-3e94-456c-a692-c0f193ea5d5a'
ms:contentKeyID: 21799608
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939830(v=WS.10)'
---

Steg 5: Konfigurera klientuppdateringar
=======================================

I Windows Server Update Services 3.0 (WSUS 3.0 SP2) konfigurerar installationsprogrammet för WSUS automatiskt IIS för distribution av den senaste versionen av Automatiska uppdateringar till de klientdatorer som kontaktar WSUS-servern.

Vilket sätt som bäst lämpar sig för konfigurering av Automatiska uppdateringar beror på nätverksmiljön. I en miljö där katalogtjänsten Active Directory® används kan du använda ett befintligt domänbaserat grupprincipobjekt eller skapa ett nytt grupprincipobjekt. I en miljö utan Active Directory använder du det lokala grupprincipobjektet. I det här steget ska du konfigurera Automatiska uppdateringar och sedan dirigera klientdatorerna till WSUS-servern.

Följande procedurer förutsätter att Active Directory körs i nätverket. Procedurerna förutsätter även att du kan använda grupprinciper och använder sådana för att hantera nätverket.

Mer information om grupprinciper finns på webbplatsen Group Policy Tech Center [http://go.microsoft.com/fwlink/?LinkID=47375](http://go.microsoft.com/fwlink/?linkid=47375).

 
-

Steg 5 Procedurer
-----------------

I steg 4 slutförde du konfigureringen av vilka uppdateringar som du vill hämta. Den här uppsättningen procedurer använder du när du ska konfigurera automatiska uppdateringar för klientdatorer.

1.  Konfigurera Automatiska uppdateringar i grupprincip.
2.  Dirigera en klientdator till WSUS-servern.
3.  Starta identifiering från WSUS-servern manuellt.

De två första procedurerna utförs i ett domänbaserat grupprincipobjekt som du väljer och den tredje proceduren i Kommandotolken på klientdatorn.

**Så här konfigurerar du Automatiska uppdateringar**
1.  Leta reda på det grupprincipobjekt som du vill konfigurera WSUS för i konsolen Grupprinciphantering och klicka sedan på **Redigera**.

2.  Visa **Datorkonfiguration**, **Administrativa mallar**, **Windows-komponenter** i konsolen Grupprinciphantering och klicka sedan på **Windows Update**.

3.  Dubbelklicka på **Konfigurera automatiska uppdateringar** i informationsfönstret.

4.  Klicka på **Aktiverad** och gör sedan något av följande:

    -   **Meddela om hämtning och installation**. När du väljer det här alternativet meddelas en inloggad administratör innan hämtningen börjar och innan uppdateringarna installeras.
    -   **Hämta automatiskt och meddela om installation**. När du väljer det här alternativet hämtas uppdateringarna automatiskt och därefter meddelas inloggade administratörer före installation.
    -   **Hämta automatiskt och schemalägg installationen**. När du väljer det här alternativet börjar uppdateringarna hämtas automatiskt och installeras sedan på den dag och tid som du anger.
    -   **Låt lokala administratörer välja**. När du väljer det här alternativet kan lokala administratörer använda Automatiska uppdateringar på Kontrollpanelen och själva ange ett konfigurationsalternativ. De kan till exempel välja en egen tidpunkt för schemalagd installation. Lokala administratörer kan inte inaktivera Automatiska uppdateringar.

5.  Klicka på **OK**.

**Så här dirigerar du klientdatorer till WSUS-servern**
1.  Dubbelklicka på **Ange sökväg till tjänsten Microsoft Update på intranätet** i informationsfönstret för **Windows Update**.

2.  Klicka på **Aktiverad** och ange URL:en för samma WSUS-server i rutan **Ange intranätserver för identifiering av uppdateringar** och i rutan **Ange intranätserver för statistik**. Skriv till exempel *http://servernamn* i båda rutorna och klicka på **OK**.

 
<table style="border:1px solid black;">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" ><img src="images/Dd939830.note(WS.10).gif" />Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Om du använder det lokala grupprincipobjektet för att ange en sökväg från datorn till WSUS, träder inställningen omedelbart i kraft och datorn visas i administrationskonsolen för WSUS efter en kort stund. Du kan påskynda processen genom att initiera en identifieringscykel manuellt.
</td>
</tr>
</tbody>
</table>
 

När du har installerat och konfigurerat en klientdator tar det flera minuter innan datorn visas på sidan **Datorer** i administrationskonsolen för WSUS. För klientdatorer som har konfigurerats med ett domänbaserat grupprincipobjekt kan det ta omkring 20 minuter efter att grupprincipen uppdateras (d.v.s. använder eventuella nya inställningar för klientdatorn). Som standard uppdateras grupprincipen i bakgrunden var 90:e minut med en slumpmässig avvikelse på 0 till 30 minuter. Om du vill uppdatera grupprincipen oftare än så kan du gå till Kommandotolken på klientdatorn och skriva **gpupdate /force**.

För klientdatorer som har konfigurerats med det lokala grupprincipobjektet används grupprincipen omedelbart och uppdateringen tar ungefär 20 minuter.

Om du initierar identifieringen manuellt behöver du inte vänta 20 minuter på att klientdatorn ska kontakta WSUS.

**Så här startar du identifiering från WSUS-servern manuellt**
1.  Klicka på **Start** på klientdatorn och sedan på **Kör**.

2.  Skriv **cmd** i rutan **Öppna** och klicka sedan på **OK**.

3.  Skriv **wuauclt.exe /detectnow** i Kommandotolken. Det här kommandoradsalternativet anger att Automatiska uppdateringar direkt ska kontakta WSUS-servern.

Nästa steg
----------

[Steg 6: Konfigurera datorgrupper](https://technet.microsoft.com/70518732-2179-4e41-9609-7f9999867f41).

Ytterligare resurser
--------------------

[Steg-för-steg-guide för Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)
