---
TOCTitle: 'Steg 6: Skapa en datorgrupp'
Title: 'Steg 6: Skapa en datorgrupp'
ms:assetid: '6039e5dc-d2ce-4d4b-b737-17ebcadbd4a7'
ms:contentKeyID: 18152794
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720536(v=WS.10)'
---

Steg 6: Skapa en datorgrupp
===========================

Datorgrupper spelar en viktig roll i WSUS-distributioner, även när det handlar om enkla distributioner. Med hjälp av datorgrupper kan du ange att uppdateringar ska installeras på specifika datorer. Det finns två standardgrupper: Alla datorer och Ej tilldelade datorer. Som standard läggs klientdatorerna till i båda grupperna vid första kontakten med WSUS-servern.

Du kan skapa egna datorgrupper. En fördel med att skapa egna datorgrupper är att du då kan testa uppdateringarna innan de distribueras och installeras på samtliga klientdatorer. Om testresultatet är tillfredsställande kan du gå vidare med uppdateringarna för gruppen Alla datorer. Du kan skapa ett valfritt antal egna grupper.

Att konfigurera datorgrupper är en process i tre steg. Först anger du hur du tänker lägga till datorer i respektive datorgrupper. Det finns två alternativ: *manuell tilldelning från server* och *automatisk tilldelning från klient*. Med manuell tilldelning lägger du själv till datorerna i respektive grupp med hjälp av WSUS. Med automatisk tilldelning läggs klientdatorerna till med hjälp av grupprinciper eller registernycklar. Därefter skapar du datorgruppen i WSUS. Slutligen flyttar du datorerna till grupperna med hjälp av den metod du valde i det första steget.

I det här dokumentet beskrivs hur du använder manuell tilldelning från servern och flyttar datorerna till respektive grupper med hjälp av WSUS-konsolen. Om du har ett stort antal klientdatorer som ska tilldelas grupper kan du använda automatisk tilldelning från klienterna och flytta datorerna till olika grupper.

Använd steg 6 om du vill konfigurera en testgrupp som innehåller minst en dator.

Det här steget innehåller följande procedurer:

-   Ange manuell tilldelning från server.
-   Skapa en grupp.
-   Flytta datorer till gruppen.

**Så här anger du vilken metod som ska användas för tilldelning av datorer**
1.  Klicka på **Alternativ** och därefter på **Datoralternativ** i WSUS-konsolens verktygsfält.

2.  I rutan **Datoralternativ** markerar du **Använd aktiviteten Tilldela datorer i Windows Server Update Services**.

3.  Klicka på **Spara inställningar** under **Aktiviteter** och klicka därefter på **OK** när bekräftelsedialogrutan visas.

**Så här skapar du en grupp**
1.  Klicka på **Datorer** i WSUS-konsolens verktygsfält.

2.  Klicka på **Skapa en datorgrupp** under **Aktiviteter**.

3.  Skriv **Test** i rutan **Öppna** och klicka på **OK**.

Använd nästa procedur när du vill lägga till en lämplig klientdator i testgruppen. En klientdator som är lämplig för testning är en dator med program- och maskinvara som är representativ för de flesta datorer i nätverket, men som inte har något central roll. På det sättet kan du avgöra hur de uppdateringar du godkänner kommer att fungera på datorer som liknar testdatorn.

**Så här lägger du till en dator i gruppen Test manuellt**
1.  Klicka på **Datorer** i WSUS-konsolens verktygsfält.

2.  I rutan **Grupper** klickar du på gruppen för den dator du vill flytta.

3.  Markera den dator du vill flytta i listan över datorer.

4.  Klicka på **Flytta markerad dator** under **Aktiviteter**.

5.  I dialogrutan **Datorgrupp** markerar du den grupp som datorn ska flyttas till och klickar därefter på **OK**.
