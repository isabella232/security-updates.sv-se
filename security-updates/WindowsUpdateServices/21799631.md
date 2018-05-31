---
TOCTitle: 'Steg 2: Installera WSUS Server eller administrationskonsolen'
Title: 'Steg 2: Installera WSUS Server eller administrationskonsolen'
ms:assetid: '6db6fcb0-c55d-43b9-9b07-4040c6267759'
ms:contentKeyID: 21799631
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939859(v=WS.10)'
---

Steg 2: Installera WSUS Server eller administrationskonsolen
============================================================

När du har kontrollerat att servern uppfyller minimisystemkraven och att de kontobehörigheter som krävs har beviljats, är du klar att installera Windows Server Update Services 3.0 Service Pack 2 (WSUS 3.0 SP2). Starta installationen av WSUS 3.0 SP2 genom att följa instruktionerna för det operativsystem och den typ av installation (antingen med Serverhanteraren eller filen WSUSSetup.exe) som du använder.

Om du använder Serverhanteraren
-------------------------------

**Så här startar du installationen av WSUS 3.0 SP2 Server med hjälp av Serverhanteraren**
1.  Logga in på den server där du ska installera WSUS 3.0 SP2 med ett konto som är medlem i den lokala gruppen Administratörer.

2.  Klicka på **Start**, peka på **Administrationsverktyg** och klicka sedan på **Serverhanteraren**.

3.  Klicka på **Lägg till roller** under Rollsammanfattning i rutan till höger i fönstret Serverhanteraren.

4.  Om sidan Innan du börjar visas klickar du på **Nästa**.

5.  Markera **Windows Server Update Services** på sidan Välj serverroller.

6.  Klicka på **Nästa** på sidan Windows Server Update Services.

7.  Klicka på **Installera** på sidan Bekräfta installationsinställningarna.

8.  När installationsguiden för WSUS 3.0 SP2 startar hoppar du över nästa avsnitt och går till proceduren Så här fortsätter du att installera WSUS 3.0 SP2.

Om du använder filen WSUSSetup.exe
----------------------------------

**Så här startar du installationen av WSUS 3.0 SP2 Server eller administrationskonsolen för WSUS 3.0 SP2 med hjälp av filen WSUSSetup.exe**
1.  Logga in på den server där du ska installera WSUS 3.0 SP2 med ett konto som är medlem i den lokala gruppen Administratörer.

2.  Dubbelklicka på installationsfilen **WSUSSetup.exe**.

3.  När installationsguiden för Windows Server Update Services 3.0 SP2 startar går du till proceduren Så här fortsätter du att installera WSUS 3.0 SP2.

Använda installationsguiden för WSUS 3.0 SP2
--------------------------------------------

Installationsguiden för WSUS startas med Serverhanteraren eller med filen WSUSSetup.exe.

**Så här fortsätter du att installera WSUS 3.0 SP2**
1.  Klicka på **Nästa** på välkomstsidan i installationsguiden för Windows Server Update Services 3.0.

2.  Klicka på **Fullständig serverinstallation inklusive administratörskonsol** på sidan Val av installationsläge om du vill installera WSUS-servern på de här datorn, eller på **Enbart administratörskonsol** om du endast vill installera administrationskonsolen.

3.  Läs igenom villkoren på sidan Licensavtal, klicka på **Jag accepterar villkoren i licensavtalet** och sedan på **Nästa**.

4.  Du kan ange varifrån klienterna ska hämta uppdateringar på sidan Välj källa för uppdateringar i installationsguiden. Som standard är kryssrutan **Spara uppdateringar lokalt** markerad och uppdateringarna sparas på WSUS-servern på den plats som du anger. Om du avmarkerar kryssrutan **Spara uppdateringar lokalt** hämtas godkända uppdateringar till klientdatorerna genom att de ansluts till Microsoft Update. Markera ditt val och klicka sedan på **Nästa**.

5.  På sidan Databasalternativ markerar du det program som används för att hantera WSUS 3.0-databasen. Som standard installeras Windows Internal Database av installationsguiden.

    Om du inte vill använda Windows Internal Database anger du en instans av SQL Server för WSUS som ska användas genom att klicka på **Använd en befintlig databasserver på datorn** eller **Använder en befintlig databasserver på en fjärrdator**. Ange instansnamnet i lämplig ruta. Instansnamnet ska visas som ett &lt;*serverNamn*&gt;\\&lt;*instansNamn*&gt;, där *serverNamn* är namnet på servern och *instansNamn* är namnet på SQL-instansen. Markera ditt val och klicka sedan på **Nästa**.

6.  Om du har valt att ansluta till SQL Server görs ett försök att ansluta WSUS till den angivna instansen av SQL Server på sidan **Ansluter till SQL Server-instans**. När anslutningen har upprättats fortsätter du genom att klicka på **Nästa**.

7.  På sidan Val av webbplats anger du vilken webbplats som ska användas av WSUS. Om du vill använda standardwebbplatsen på port 80 markerar du **Använd den befintliga standardwebbplatsen i IIS**. Om du redan har en webbplats på port 80 kan du skapa en alternativ webbplats på port 8530 genom att markera **Skapa en webbplats för Windows Server Update Services 3.0 SP2**. Klicka på **Nästa**.

8.  Gå igenom de gjorda valen på sidan **Installation av Microsoft Windows Server Update Services kan påbörjas** och klicka på **Nästa**.

9.  På den sista sidan i installationsguiden anges om installationen av WSUS har slutförts eller inte. När du har klickat på **Slutför** startas konfigurationsguiden.

Nästa steg
----------

[Steg 3: Konfigurera nätverksanslutningarna](https://technet.microsoft.com/42a144c5-f08e-4a6e-b360-47ddea77bd24).

Ytterligare resurser
--------------------

[Steg-för-steg-guide för Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)
