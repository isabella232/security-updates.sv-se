---
TOCTitle: 'Steg 7: Godkänna och distribuera uppdateringar i WSUS 3.0'
Title: 'Steg 7: Godkänna och distribuera uppdateringar i WSUS 3.0'
ms:assetid: '88fac442-a9d3-4e74-92f6-3822b7237af1'
ms:contentKeyID: 18152906
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708475(v=WS.10)'
---

Steg 7: Godkänna och distribuera uppdateringar i WSUS 3.0
=========================================================

I det här steget ska du godkänna en uppdatering för klientdatorerna i gruppen Test. Datorerna i gruppen kommer att kontakta WSUS-servern inom de närmaste 24 timmarna. Efter dessa 24 timmar kan du använda rapportfunktionen i WSUS och avgöra om uppdateringarna har distribuerats till datorerna. Om testningen avlöper väl kan du därefter godkänna samma uppdateringar för resten av datorerna i organisationen.

**Steg 7 innehåller följande procedurer**:

-   Godkänna och distribuera en uppdatering.
-   Kontrollera uppdateringens status.

**Så här godkänner du och distribuerar en uppdatering**
1.  Klicka på **Uppdateringar** i WSUS-administratörskonsolen. Då visas en sammanfattning av uppdateringarna i standardvyerna (**Alla uppdateringar**, **Kritiska uppdateringar**, **Säkerhetsuppdateringar** och **WSUS-uppdateringar**). Använd **Alla uppdateringar** i den här proceduren.

2.  I listan över uppdateringar markerar du de uppdateringar som ska godkännas för installation. Information om den valda uppdateringen finns i den understa fönsterrutan i fönstret Uppdateringar. Om du vill markera flera intilliggande uppdateringar håller du ned **SKIFT** och klickar på de önskade uppdateringarna. Om du vill markera flera uppdateringar som inte ligger intill varandra håller du ned **CTRL** medan du klickar.

3.  Högerklicka på markeringen och klicka på **Godkänn**. Dialogrutan **Automatiska uppdateringar** öppnas.

4.  Markera en av grupperna (till exempel **Test**) och klicka på pilen till vänster om den. Nu visas en snabbmeny med alternativen **Godkänd för installation**, **Godkänd för borttagning**, **Ej godkänd**, **Tidsgräns**, **Samma som för överordnade** och **Tillämpa på underordnade**. Klicka på **Godkänd för installation** och sedan på **OK**.

5.  Nu visas ett nytt fönster, **Godkännandeförlopp**, som visar förloppet för de olika aktiviteterna som påverkar godkännandet av uppdateringarna. När godkännandet är klart stänger du fönstret genom att klicka på **Stäng**.

| ![](images/Cc708475.note(WS.10).gif)Obs!                                                             |
|-----------------------------------------------------------------------------------------------------------------------------------|
| Det finns många alternativ för godkännande av uppdateringar. Du kan till exempel ange tidsgränser och avinstallera uppdateringar. |

Efter 24 timmar kan du använda rapportfunktionen i WSUS och ta reda på om uppdateringarna har distribuerats till datorerna.

**Så här kontrollerar du status för en uppdatering**
1.  Klicka på **Rapporter** i den vänstra fönsterrutan i WSUS-administratörskonsolen.

2.  På sidan **Rapporter** visas ett antal standardiserade rapporter. Klicka på rapporten **Sammanfattad uppdateringsstatus**. Fönstret **Uppdateringsrapport** visas.

3.  Om du vill filtrera listan med uppdateringar markerar du önskat villkor (till exempel **Inkludera uppdateringar i dessa klassificeringar**) och klickar sedan på **Kör rapport** i fönstrets verktygsfält.

4.  Fönstret **Uppdateringsrapport** visas. Du kan kontrollera status för enskilda uppdateringar genom att välja en uppdatering i fönstrets vänstra del. Den sista delen i rapportfönstret visar statussammanfattningen för uppdateringen.

5.  Du kan spara eller skriva ut rapporten genom att klicka på respektive ikon i verktygsfältet.

Om uppdateringarna har distribuerats felfritt i gruppen Test kan du godkänna samma uppdateringar för de övriga datorerna i organisationen.
