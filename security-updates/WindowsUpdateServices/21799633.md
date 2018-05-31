---
TOCTitle: 'Steg 6: Konfigurera datorgrupper'
Title: 'Steg 6: Konfigurera datorgrupper'
ms:assetid: '70518732-2179-4e41-9609-7f9999867f41'
ms:contentKeyID: 21799633
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939860(v=WS.10)'
---

Steg 6: Konfigurera datorgrupper
================================

Datorgrupper är en viktig del i distributioner av Windows Server Update Services 3.0 Service Pack 2 (WSUS 3.0 SP2). Med hjälp av datorgrupper kan du testa uppdateringar och ange att uppdateringar ska installeras på specifika datorer. Det finns två standardgrupper: Alla datorer och Ej tilldelade datorer. Som standard läggs klientdatorerna till i båda grupperna vid första kontakten med WSUS-servern.

Du kan skapa så många anpassade datorgrupper som du behöver för att hantera uppdateringar i organisationen. Du rekommenderas att skapa minst en datorgrupp där du kan testa uppdateringarna innan de distribueras till andra datorer i organisationen.

Steg 6 Procedurer
-----------------

1.  Skapa en testdatorgrupp.
2.  Flytta minst en dator till testgruppen.

**Så här skapar du en testgrupp**
1.  Visa **Datorer** i administrationskonsolen för WSUS och markera **Alla datorer**.

2.  Högerklicka på **Alla datorer** och klicka på **Lägg till datorgrupp**.

3.  Fyll i **Namn** för den nya testgruppen i dialogrutan **Lägg till datorgrupp** och klicka på **Lägg till**.

I nästa procedur tilldelar du testgruppen en klientdator. En testdator är en dator med programvara och maskinvara motsvarande majoriteten av klientdatorerna i nätverket, men som inte fyller någon viktig funktion. När testerna har slutförts med lyckat resultat kan du godkänna uppdateringarna för datorer i de grupper som du väljer.

**Så tilldelar du testgruppen en dator**
1.  Klicka på **Datorer** i administrationskonsolen för WSUS.

2.  Klicka på gruppen för den dator som du vill att testgruppen ska tilldelas.

3.  I listan över datorer markerar du den eller de datorer som du vill att testgruppen ska tilldelas.

4.  Högerklicka på **Ändra medlemskap**.

5.  Markera den testgrupp som du skapade tidigare i dialogrutan **Ange datorgruppsmedlemskap** och klicka sedan på **OK**.

Upprepa de här två procedurerna, d.v.s. skapa en grupp och sedan tilldela den datorer, för att skapa så många ytterligare datorgrupper som behövs för att hantera uppdateringar i organisationen.

Nästa steg
----------

[Steg 7: Godkänna och distribuera WSUS-uppdateringar](https://technet.microsoft.com/c4e58e17-d5e3-4194-8f26-b459e0c03b86).

Ytterligare resurser
--------------------

[Steg-för-steg-guide för Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)
