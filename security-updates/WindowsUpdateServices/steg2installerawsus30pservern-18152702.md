---
TOCTitle: 'Steg 2: Installera WSUS 3.0 på servern'
Title: 'Steg 2: Installera WSUS 3.0 på servern'
ms:assetid: '191e62a0-7671-41eb-9841-17c64313fa68'
ms:contentKeyID: 18152702
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720469(v=WS.10)'
---

Steg 2: Installera WSUS 3.0 på servern
======================================

När du har sett till att servern uppfyller installationskraven är du klar att installera WSUS 3.0. Du måste logga in på den server där du ska installera WSUS 3.0 med ett konto som är medlem i den lokala gruppen Administratörer. Endast den som är medlem i den lokala gruppen Administratörer kan installera WSUS 3.0.

I proceduren nedan används standardalternativen för WSUS-installationen, som bland annat innebär att Windows Internal Database installeras för WSUS 3.0-databasen, uppdateringar lagras lokalt och standardwebbplatsen för IIS använder port 80.

**Så här installerar du WSUS 3.0**
1.  Dubbelklicka på installationsfilen **WSUSSetup.exe**.

2.  Klicka på **Nästa** på **välkomstsidan** i installationsguiden.

3.  Klicka på **Fullständig serverinstallation inklusive administratörskonsol** på sidan **Val av installationsläge** om du vill installera servern på den här datorn, eller **Enbart administratörskonsol** om du bara vill installera administratörskonsolen.

4.  Läs igenom villkoren noggrant på sidan **Licensavtal**. Klicka därefter på **Jag accepterar villkoren i licensavtalet** och därefter på **Nästa**.

    ![](images/Cc720469.fa6ac6a6-6814-4b7e-96e8-e08af5e534b8(WS.10).gif)

5.  På sidan **Välj källa för uppdateringar** i installationsguiden anger du varifrån klientdatorerna ska hämta uppdateringarna. Om du markerar kryssrutan **Spara uppdateringar lokalt** lagras uppdateringarna på WSUS 3.0-servern och du väljer själv en lagringsplats i filsystemet. Om du väljer att inte lagra uppdateringar lokalt kommer klientdatorerna att ansluta till Microsoft Update och hämta godkända uppdateringar därifrån. Behåll standardalternativen och klicka på **Nästa**.

    ![](images/Cc720469.c8bac396-ca39-4491-8b0c-742a0e470535(WS.10).gif)

6.  På sidan **Databasalternativ** markerar du det program som ska användas för hantering av WSUS 3.0-databasen. Om Windows Server 2003 körs på den dator där du installerar WSUS tillfrågas du som standard om Windows Internal Database ska installeras.

7.  Om du inte vill använda Windows Internal Database måste du ange en SQL Server-instans för WSUS. Klicka i så fall på **Använda** **en befintlig databasserver på den här datorn** och skriv instansnamnet i rutan. Instansnamnet ska visas som ett &lt;*serverNamn*&gt;\\&lt;*instansNamn*&gt;, där *serverNamn* är namnet på servern och *instansNamn* är namnet på SQL-instansen. Markera ditt val och klicka sedan på **Nästa**.

8.  På sidan **Ansluter till SQL Server-instans** försöker WSUS att ansluta till angiven instans av SQL Server. När anslutningen har upprättats fortsätter du genom att klicka på **Nästa**.

    ![](images/Cc720469.36c6af0c-a61e-4151-ae50-c754a106cb1b(WS.10).gif)

9.  På sidan **Val av webbplats** anger du vilken webbplats som ska användas av WSUS 3.0. Om du vill använda standardwebbplatsen för IIS på port 80 väljer du det första alternativet. Om du redan har en webbplats på port 80 kan du skapa en alternativ webbplats på port 8530 genom att välja det andra alternativet. Behåll standardalternativet och klicka på **Nästa**.

10. Gå igenom de gjorda valen på sidan **Installation av Microsoft Windows Server Update Services kan påbörjas** och klicka på **Nästa**.

11. På den sista sidan i installationsguiden anges om installationen av WSUS 3.0 har slutförts eller inte. När du klickar på **Slutför** startas konfigurationsguiden.
