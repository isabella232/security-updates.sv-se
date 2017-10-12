---
TOCTitle: 'Steg 4: Konfigurera uppdateringar och synkronisering'
Title: 'Steg 4: Konfigurera uppdateringar och synkronisering'
ms:assetid: 'deeaa7e1-9b50-45cb-9537-d75f70de3405'
ms:contentKeyID: 21799683
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939924(v=WS.10)'
---

Steg 4: Konfigurera uppdateringar och synkronisering
====================================================

I det här avsnittet beskrivs hur du konfigurerar en uppsättning uppdateringar som du vill hämta med hjälp av Windows Server Update Services 3.0 Service Pack 2 (WSUS 3.0 SP2).

Steg 4 Procedurer
-----------------

Du kan utföra de här procedurerna med hjälp av antingen konfigurationsguiden för WSUS eller administrationskonsolen för WSUS.

1.  Sparar och hämtar information om den överordnade servern och proxyservern.
2.  Välj språk för uppdateringarna.
3.  Markera för vilka produkter som du vill ta emot uppdateringar.
4.  Välj klassificeringar för uppdateringarna.
5.  Anger synkroniseringsschema för servern.

När du har konfigurerat nätverksanslutningen kan du hämta uppdateringar genom att synkronisera WSUS-servern. Synkroniseringen påbörjas när WSUS-servern kontaktar Microsoft Update. När kontakten är etablerad kontrollerar WSUS om det har kommit några nya uppdateringar sedan den senaste synkroniseringen genomfördes. När du synkroniserar WSUS-servern för första gången är alla uppdateringar tillgängliga och kan godkännas för installation. Den första synkroniseringen kan ta lång tid.

I procedurerna i det här avsnittet beskrivs synkronisering med standardinställningar. WSUS 3.0 SP2 innehåller också alternativ för att minimera bandbreddsanvändningen under synkronisering.

Om du använder konfigurationsguiden i Windows Server Update Services
--------------------------------------------------------------------

I procedurerna i steg 3 slutförde du konfigureringen av den överordnade servern och proxyservern. Följande uppsättning procedurer börjar på sidan **Anslut till överordnad server** i den konfigurationsguiden.

**Så här sparar du och hämtar information om den överordnade servern och proxyservern**
1.  Klicka på knappen **Starta anslutning** på sidan Anslut till överordnad server i konfigurationsguiden. Då både sparas och överförs inställningarna och information om tillgängliga uppdateringar samlas in.

2.  Medan anslutningen upprättas kan knappen **Avsluta anslutning** användas. Om det uppstår problem med anslutningen klickar du på **Avsluta anslutning**, korrigerar problemen och startar om anslutningen.

3.  Klicka på **Nästa** när hämtningen har slutförts.

**Så här väljer du uppdateringsspråk**
1.  På sidan Välj språk kan du välja att ta emot uppdateringar för alla språk eller för en begränsad uppsättning språk. Du kan spara diskutrymme genom att markera en begränsad uppsättning språk, men det är viktigt att du väljer alla språk som behövs på alla klienter för den här WSUS-servern.

    Om du väljer att endast hämta uppdateringar för vissa språk markerar du **Hämta endast uppdateringar på följande språk** och markerar sedan de språk som du vill ha uppdateringar för.

2.  Klicka på **Nästa**.

**Så här väljer du uppdateringsprodukter**
1.  På sidan Välj produkter kan du ange vilka produkter som du vill ha uppdateringar för. Markera produktkategorier, till exempel Windows, eller vissa produkter, till exempel Windows Server 2008. När du markerar en produktkategori markeras alla produkter i den kategorin.

2.  Klicka på **Nästa**.

**Så här väljer du uppdateringsklassificeringar**
1.  På sidan Välj klassificeringar kan du välja de uppdateringsklassificeringar som du vill hämta. Du kan välja alla klassificeringar eller en begränsad uppsättning av dem.

2.  Klicka på **Nästa**.

**Så här konfigurerar du synkroniseringsschemat**
1.  På sidan Ange synkroniseringsschema väljer du huruvida du vill utföra synkronisering manuellt eller automatiskt.

    Om du väljer **Synkronisera manuellt** måste du starta synkroniseringsprocessen från administrationskonsolen för WSUS.

    Om du väljer **Synkronisera automatiskt** synkroniseras WSUS-servern vid angivna intervall. Ange tiden för **Första synkroniseringen** och ange det antal **Synkroniseringar per dag** som du vill att servern ska utföra. Om du till exempel anger att fyra synkroniseringar per dag ska utföras, med början klockan 03:00, utförs synkroniseringar vid 03:00, 09:00, 15:00 och 21:00.

2.  Klicka på **Nästa**.

3.  Du kan starta administrationskonsolen för WSUS på sidan Slutfört genom låta kryssrutan **Starta administrationskonsolen för Windows Server Update Services** vara markerad och du kan starta den första synkroniseringen genom att låta kryssrutan **Påbörja inledande synkronisering** vara markerad.

4.  Klicka på **Slutför**.

 
    <table style="border:1px solid black;">
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th style="border:1px solid black;" ><img src="images/Dd939924.Important(WS.10).gif" />Viktigt</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td style="border:1px solid black;">Du kan inte spara konfigurationsändringarna som görs medan servern synkroniseras. Vänta tills synkroniseringen har slutförs och utför sedan ändringarna.
    </td>
    </tr>
    </tbody>
    </table>
 

Om du använder administrationskonsolen för WSUS
-----------------------------------------------

I följande procedurer förklaras hur du utför konfigurationsstegen med hjälp av administrationskonsolen för WSUS.

**Så här väljer du produkter och uppdateringsklassificeringar**
1.  Klicka på **Produkter och klassificeringar** på panelen **Alternativ**. En dialogruta med flikarna **Produkter** och **Klassificeringar** visas.

2.  Markera produktkategorin eller de specifika produkter som du vill att servern ska hämta uppdateringar för på fliken **Produkter**. Du kan också markera **Alla produkter**.

3.  På fliken **Klassificeringar** ska du välja önskade uppdateringsklassificeringar, eller annars välja **Alla klassificeringar**.

4.  Spara valen med **OK**.

**Så här väljer du uppdateringsfiler och uppdateringsspråk**
1.  Klicka på **Uppdateringsfiler och -språk** på panelen **Alternativ**. En dialogruta med flikarna **Uppdateringsfiler** och **Uppdateringsspråk** visas.

2.  På fliken **Uppdateringsfiler** kan du markera **Lagra uppdateringar på den här servern** eller ange att alla klientdatorer ska installera från Microsoft Update. Om du väljer att lagra uppdateringsfilerna på den här servern, kan du också välja huruvida du vill hämta endast de uppdateringar som är godkända eller hämta expressinstallationsfiler.

3.  Om du lagrar uppdateringsfiler lokalt kan du på fliken **Uppdateringsspråk** markera **Hämta uppdateringar på alla språk** (standardinställning) eller **Hämta endast uppdateringar på följande språk**. Om den här WSUS-servern har underordnade servrar tar de endast emot uppdateringar på de språk som anges av den överordnade servern.

4.  Spara inställningarna genom att klicka på **OK**.

**Så här synkroniserar du WSUS-servern**
1.  Klicka på **Synkroniseringsschema** på panelen **Alternativ**.

2.  På fliken **Synkroniseringsschema** väljer du huruvida du vill utföra synkronisering manuellt eller automatiskt.

    Om du väljer **Synkronisera manuellt** måste du starta synkroniseringsprocessen från administrationskonsolen för WSUS.

    Om du väljer **Synkronisera automatiskt** synkroniseras WSUS-servern vid angivna intervall. Ange tiden för **Första synkroniseringen** och ange det antal **Synkroniseringar per dag** som du vill att servern ska utföra. Om du till exempel anger att fyra synkroniseringar per dag ska utföras, med början klockan 03:00, utförs synkroniseringar vid 03:00, 09:00, 15:00 och 21:00.

3.  Spara valen med **OK**.

4.  Markera **Synkroniseringar** i navigeringsfönstret i administrationskonsolen för WSUS.

5.  Högerklicka eller gå till fönstret **Åtgärder** till höger och klicka sedan på **Synkronisera nu**.

    Om fönstret **Åtgärder** inte visas till höger om konsolen klickar du på **Visa** i konsolens verktygsfält, klickar på **Anpassa** och markerar sedan kryssrutan **Åtgärdsfönster**.

6.  När synkroniseringen har slutförts klickar du på **Uppdateringar** på den vänstra panelen för att visa listan över uppdateringar.

Nästa steg
----------

[Steg 5: Konfigurera klientuppdateringar](https://technet.microsoft.com/5ae60ead-3e94-456c-a692-c0f193ea5d5a).

Ytterligare resurser
--------------------

[Steg-för-steg-guide för Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)
