---
TOCTitle: 'Steg 2: Installera WSUS på servern'
Title: 'Steg 2: Installera WSUS på servern'
ms:assetid: 'f593532c-e92e-47f3-914a-38a6c2519e94'
ms:contentKeyID: 18152984
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708622(v=WS.10)'
---

Steg 2: Installera WSUS på servern
==================================

När du har gått igenom installationskraven är du redo att installera WSUS. Du måste logga in på den server där du ska installera WSUS med ett konto som är medlem i den lokala gruppen Administratörer. Endast den som är medlem i den lokala gruppen Administratörer kan installera WSUS.

I följande procedur används standardalternativen för installation av WSUS för Windows Server 2003, vilket omfattar databasprogrammet Windows SQL Server 2000 Desktop Engine (WMSDE), lokal lagring av uppdateringar och placering av IIS-standardwebbplatsen på port 80. Du hittar procedurer för egna installationsalternativ, till exempel för andra operativsystem, annan databasprogramvara eller webbplatser med egna portnummer, i vitboken “Deploying Microsoft Windows Server Update Services” (på engelska).

**Så här installerar du WSUS på Windows Server 2003**
1.  Dubbelklicka på installationsfilen **WSUSSetup.exe**.

    | ![](images/Cc708622.note(WS.10).gif)Obs!                                                                                                                                                                  |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Den senaste versionen av WSUSSetup.exe finns på [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=47374) för Windows Server Update Services på http://go.microsoft.com/fwlink/?LinkId=47374 (texten kan vara på engelska). |

2.  Klicka på **Nästa** på **välkomstsidan** i guiden.

3.  Läs villkoren i licensavtalet noggrant. Klicka därefter på **Jag accepterar villkoren i licensavtalet** och därefter på **Nästa**.

4.  På sidan **Välj källa för uppdateringar** anger du varifrån klientdatorerna ska hämta uppdateringarna. Om du markerar kryssrutan **Spara uppdateringar lokalt** lagras uppdateringarna på WSUS-servern och du väljer själv en lagringsplats i filsystemet. Om du väljer att inte lagra uppdateringar lokalt kommer klientdatorerna att ansluta till Microsoft Update och hämta godkända uppdateringar därifrån.

    Behåll standardalternativen och klicka på **Nästa**.

    ![](images/Cc708622.fa6ac6a6-6814-4b7e-96e8-e08af5e534b8(WS.10).gif)

5.  På sidan **Databasalternativ** markerar du det program som ska användas för hantering av WSUS-databasen. Om Windows Server 2003 körs på den dator där du installerar WSUS tillfrågas du som standard om WMSDE ska installeras.

    Om du inte kan använda WMSDE måste du ange en SQL Server-instans för WSUS. Klicka i så fall på **Använd en befintlig databasserver på den här datorn** och skriv instansnamnet i rutan **Välj namn på SQL Server-instans**. Mer information om andra databasalternativ än WMSDE finns i vitboken “Deploying Microsoft Windows Server Update Services”.

    Behåll standardalternativen och klicka på **Nästa**.

    ![](images/Cc708622.bc0b73ad-b338-437c-a3c7-0299e819840d(WS.10).gif)

6.  På sidan **Val av webbplats** anger du vilken webbplats som ska användas av WSUS. På sidan finns även två viktiga URL:er som baseras på valet: den URL som du anger att WSUS-klientdatorerna ska använda för att hämta uppdateringar och URL:en för WSUS-konsolen där du konfigurerar WSUS.

    Om det redan finns en webbplats på port 80 skapar du WSUS-webbplatsen på en egen port. Mer information om hur du kör WSUS på en egen port finns i vitboken “Deploying Microsoft Windows Server Update Services”.

    Behåll standardalternativet och klicka på **Nästa**.

    ![](images/Cc708622.64ed7643-a050-4f54-bf9f-04cf7931adc0(WS.10).gif)

7.  På sidan **Spegla inställningar för uppdateringar** kan du ange WSUS-serverns administrationsroll. Hoppa över den här skärmen om det här är den första WSUS-servern på nätverket eller om du vill använda en distribuerad topologi.

    Om du vill använda en central topologi och det redan finns WSUS-servrar på nätverket, markerar du kryssrutan och anger namnet på en annan WSUS-server i rutan **Servernamn**. Mer information om administrationsroller finns i vitboken “Deploying Microsoft Windows Server Update Services”.

    Behåll standardalternativet och klicka på **Nästa**.

    ![](images/Cc708622.f26e09d5-983c-418d-8511-8960850403ef(WS.10).gif)

8.  På sidan **Installation av Microsoft Windows Server Update Services kan påbörjas** går du igenom de gjorda valen och klickar på **Nästa**.

    ![](images/Cc708622.20de7d09-3d30-4867-9253-6f353dd1923d(WS.10).gif)

9.  Klicka på **Slutför** när du på den sista sidan i guiden får ett meddelande om att WSUS-installationen har slutförts.
