---
TOCTitle: 'Steg 7: Godkänna och distribuera WSUS-uppdateringar'
Title: 'Steg 7: Godkänna och distribuera WSUS-uppdateringar'
ms:assetid: 'c4e58e17-d5e3-4194-8f26-b459e0c03b86'
ms:contentKeyID: 21799686
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939909(v=WS.10)'
---

Steg 7: Godkänna och distribuera WSUS-uppdateringar
===================================================

I de här steget godkänner du en uppdatering för datorer i testgruppen för Windows Server Update Services 3.0 Service Pack 2 (WSUS 3.0 SP2). Datorerna i gruppen kontaktar WSUS-servern automatiskt inom de närmaste 24 timmarna för att hämta uppdateringen. Du kan använda rapportfunktionen i WSUS för att avgöra huruvida uppdateringarna har distribuerats till testdatorerna. När testerna har slutförts utan problem kan du godkänna uppdateringarna för lämpliga datorgrupper i organisationen.

Steg 7 Procedurer
-----------------

-   Godkänna och distribuera en uppdatering.
-   Kontrollera status för en uppdatering.

**Så här godkänner du och distribuerar en uppdatering**
1.  Klicka på **Uppdateringar** i administrationskonsolen för WSUS. En sammanfattad uppdateringsstatus visas för **Alla uppdateringar**, **Kritiska uppdateringar**, **Säkerhetsuppdateringar** och **WSUS-uppdateringar**.

2.  Klicka på **Uppdateringar som datorer behöver** i avsnittet **Alla uppdateringar**.

3.  I listan över uppdateringar markerar du de uppdateringar som du vill godkänna för installation i testdatorgruppen. Information om en markerad uppdatering visas i det nedersta fönstret på panelen Uppdateringar. Om du vill markera flera intilliggande uppdateringar håller du **SKIFT** nedtryckt och klickar på uppdateringarna. Om du vill markera flera uppdateringar som inte ligger intill varandra håller **CTRL** nedtryckt medan du klickar på uppdateringarna.

4.  Högerklicka på markeringen och klicka på **Godkänn**.

5.  Markera testgruppen i dialogrutan **Godkänn uppdateringar** och klicka sedan på nedpilen.

6.  Klicka på **Godkänd för installation** och sedan på **OK**.

7.  Fönstret Godkännandeförlopp öppnas och visar förloppet för de uppgifter som ingår i godkännandet av uppdateringar. Klicka på **Stäng** när godkännandet har slutförts.

Efter 24 timmar kan du använda rapportfunktionen i WSUS och ta reda på huruvida uppdateringarna har distribuerats till datorerna i testgruppen.

**Så här kontrollerar du status för en uppdatering**
1.  Klicka på **Rapporter** i navigeringsfönstret i administrationskonsolen för WSUS.

2.  Klicka på rapporten **Sammanfattad uppdateringsstatus** på sidan **Rapporter**. Fönstret **Uppdateringsrapporter** visas.

3.  Om du vill filtrera listan över uppdateringar markerar du de villkor som du vill använda (till exempel **Inkludera uppdateringar i dessa klassificeringar**) och klickar sedan på **Kör rapport** i fönstrets verktygsfält.

4.  Fönstret **Uppdateringsrapport** visas. Du kan kontrollera status för enskilda uppdateringar genom att välja en uppdatering i fönstrets vänstra del. Den sista delen i rapportfönstret visar statussammanfattningen för uppdateringen.

5.  Du kan spara eller skriva ut rapporten genom att klicka på respektive ikon i verktygsfältet.

6.  När du har testat uppdateringarna kan du godkänna dem för installation i lämpliga datorgrupper i organisationen.

Ytterligare resurser
--------------------

[Steg-för-steg-guide för Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)

Mer information om hur du använder WSUS 3.0 SP2 finns i:

WSUS-distributionshandboken på [http://go.microsoft.com/fwlink/?LinkId=139832](http://go.microsoft.com/fwlink/?linkid=139832).

WSUS-operatörshandboken på [http://go.microsoft.com/fwlink/?LinkId=139838](http://go.microsoft.com/fwlink/?linkid=139838).
