---
TOCTitle: 'Steg 7: Godkänna och installera uppdateringar'
Title: 'Steg 7: Godkänna och installera uppdateringar'
ms:assetid: '38db25a9-6702-4e43-b536-764e8814afc6'
ms:contentKeyID: 18152797
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720504(v=WS.10)'
---

Steg 7: Godkänna och installera uppdateringar
=============================================

I det här steget ska du godkänna en uppdatering för klientdatorerna i gruppen Test. Datorerna i gruppen kommer alla att kontakta WSUS-servern inom de närmaste 24 timmarna. Efter dessa 24 timmar kan du använda rapportfunktionen i WSUS och avgöra om uppdateringarna har distribuerats till datorerna. Om testningen avlöper väl kan du därefter godkänna samma uppdatering för resten av datorerna i organisationen.

Steg 7 innehåller följande procedurer:

-   Godkänna och distribuera en uppdatering.
-   Köra rapporten Status för uppdateringar.

**Så här godkänner du och distribuerar en uppdatering**
1.  Klicka på **Uppdateringar** i WSUS-konsolens verktygsfält. Som standard är listan över uppdateringar filtrerad så att endast kritiska uppdateringar och säkerhetsuppdateringar som har godkänts för identifiering på klientdatorer visas. Använd standardfiltret för den här proceduren.

2.  I listan över uppdateringar markerar du de uppdateringar som ska godkännas för installation. Information om en markerad uppdatering finns på fliken **Information**. När du vill markera flera intilliggande uppdateringar håller du ned SKIFT och klickar på de önskade uppdateringarna. När du vill markera flera uppdateringar som inte ligger intill varandra håller du ned CTRL medan du klickar.

3.  Klicka på **Ändra godkännande** under **Uppdateringsaktiviteter**. Dialogrutan **Automatiska uppdateringar** öppnas.

4.  I listan **Gruppinställningar för godkännande för de valda uppdateringarna** klickar du på **Installera** i listan i kolumnen **Godkännande** för gruppen Test. Klicka därefter på **OK**.

| ![](images/Cc720504.note(WS.10).gif)Obs!                                                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Det finns många alternativ för godkännande av uppdateringar. Du kan till exempel ange tidsgränser och avinstallera uppdateringar. Mer information om dessa alternativ finns i vitboken “Microsoft Windows Server Update Services Operations Guide” (på engelska). |

Efter 24 timmar kan du använda rapportfunktionen i WSUS och ta reda på om uppdateringarna har distribuerats till datorerna.

**Så här kör du rapporten Status för uppdateringar.**
1.  Klicka på **Rapporter** i WSUS-konsolens verktygsfält.

2.  Klicka på **Status för uppdateringar** på sidan **Rapporter**.

3.  Om du vill filtrera listan med uppdateringar markerar du de villkor som ska användas under **Vy** och klickar sedan på **Verkställ**.

4.  Om du vill visa uppdateringsstatus först per datorgrupp och därefter per dator, klickar du och visar uppdateringsvyn på önskat sätt.

5.  Om du vill skriva ut rapporten Status för uppdateringar klickar du på **Skriv ut rapport** under **Aktiviteter**.

Om uppdateringarna har distribuerats felfritt i gruppen Test kan du godkänna samma uppdateringar för de övriga datorerna i organisationen.
