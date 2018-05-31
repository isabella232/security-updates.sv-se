---
TOCTitle: 'Steg 6: Skapa en datorgrupp för uppdateringar'
Title: 'Steg 6: Skapa en datorgrupp för uppdateringar'
ms:assetid: 'fe219654-eae8-45ca-a44b-c1e05c3c3e93'
ms:contentKeyID: 18153002
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708629(v=WS.10)'
---

Steg 6: Skapa en datorgrupp för uppdateringar
=============================================

Datorgrupper spelar en viktig roll i WSUS-distributioner, även när det handlar om enkla distributioner. Med hjälp av datorgrupper kan du ange att uppdateringar ska installeras på specifika datorer. Det finns två standardgrupper: Alla datorer och Ej tilldelade datorer. Som standard läggs klientdatorerna till i båda grupperna vid första kontakten med WSUS-servern.

Du kan skapa egna datorgrupper. En fördel med att skapa egna datorgrupper är att du då kan testa uppdateringarna innan de distribueras och installeras på samtliga klientdatorer. Om testresultatet är tillfredsställande kan du gå vidare med uppdateringarna för gruppen Alla datorer. Du kan skapa ett valfritt antal egna grupper.

**Så här skapar du datorgrupper**
1.  Ange hur du tänker lägga till datorer i respektive datorgrupper. Det finns två alternativ: manuell tilldelning från server och automatisk tilldelning från klient. Med manuell tilldelning lägger du själv till datorerna i respektive grupp med hjälp av WSUS. Med automatisk tilldelning läggs klientdatorerna till med hjälp av grupprinciper eller registernycklar.

2.  Skapa datorgruppen på WSUS.

3.  Flytta datorerna till grupper med den metod som du väljer i steg 1.

I det här avsnittet beskrivs hur du använder manuell tilldelning från servern och flyttar datorerna till respektive grupper med hjälp av WSUS-administratörskonsolen. Om du har flera klientdatorer som ska tilldelas grupper kan du använda automatisk tilldelning från klienterna och flytta datorerna till olika grupper.

Använd steg 6 om du vill konfigurera en testgrupp som innehåller minst en dator.

**Steg 6 innehåller följande procedurer:**

-   Skapa en grupp.
-   Lägga till en dator i gruppen.

**Så här skapar du en grupp**
1.  Expandera **Datorer** i WSUS-administratörskonsolen och välj **Alla datorer**.

2.  Högerklicka på **Alla datorer** eller gå till fönstret **Åtgärder** och klicka på **Lägg till datorgrupp**.

3.  Dialogrutan **Lägg till datorgrupp** visas. Ange namnet på den nya gruppen.

Använd nästa procedur när du vill lägga till en lämplig klientdator i testgruppen. En klientdator som är lämplig för testning är en dator med program- och maskinvara som är representativ för de flesta datorer i nätverket, men som inte har något central roll. På det sättet kan du avgöra hur de uppdateringar du godkänner kommer att fungera på datorer som liknar testdatorn.

**Så här lägger du till en dator i gruppen**
1.  Klicka på **Datorer** i WSUS-administratörskonsolen.

2.  Klicka på gruppen för datorn som du vill flytta.

3.  Klicka på den dator du vill flytta i listan med datorer.

4.  Högerklicka på **Ändra medlemskap**.

5.  Dialogrutan **Ange datorgruppsmedlemskap** visas med en lista med grupper.

6.  Markera den grupp som du vill flytta datorn till och klicka på **OK**.
