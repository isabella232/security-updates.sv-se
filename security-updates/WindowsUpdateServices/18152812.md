---
TOCTitle: 'Steg 4: Konfigurera uppdateringar och synkronisering'
Title: 'Steg 4: Konfigurera uppdateringar och synkronisering'
ms:assetid: '734cc2ed-98be-4772-a42c-8fd38b39d864'
ms:contentKeyID: 18152812
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708447(v=WS.10)'
---

Steg 4: Konfigurera uppdateringar och synkronisering
====================================================

Innan du hämtar uppdateringarna måste du ange vilka som ska hämtas. I det här avsnittet beskrivs hur du anger vilka uppdateringar som ska hämtas.

Här beskrivs hur du:

-   Sparar och hämtar information om den överordnade servern och proxyservern.
-   Väljer språk för uppdateringar.
-   Väljer vilka produkter som du vill ha uppdateringar för.
-   Väljer klassificeringar för uppdateringar.
-   Anger synkroniseringsschema för servern.

I de nästa fem procedurerna beskrivs hur du konfigurerar uppdateringarna med hjälp av konfigurationsguiden. I senare procedurer beskrivs hur du utför den här konfigurationen från WSUS-administratörskonsolen genom att välja vissa alternativ.

**Spara och hämta information om den överordnade servern och proxyservern**
1.  Du ska ha utfört konfigurationen av den överordnade servern och proxyservern i konfigurationsguiden och sidan **Anslut till överordnad server** bör nu visas.

2.  Klicka på **Starta anslutning** som sparar och överför dina inställningar och hämtar information om tillgängliga uppdateringar.

3.  Medan anslutningen upprättas kan knappen **Avsluta anslutning** användas. Om det uppstår problem med anslutningen klickar du på **Avsluta anslutning**, korrigerar problemen och startar om anslutningen.

4.  När hämtningen är klar klickar du på **Nästa** för att komma till sidan **Välj språk** eller väljer någon annan sida i den vänstra fönsterrutan.

**Välja uppdateringsspråk**
1.  På sidan **Välj språk** kan du hämta uppdateringar från alla språk eller från en delmängd språk. Det går att spara diskutrymme genom att markera en delmängd av språk, men det är viktigt att du väljer alla språk som behövs på alla klienter som använder den här WSUS-servern.

2.  Om du väljer att hämta uppdateringar för bara ett fåtal språk ska du välja **Hämta endast uppdateringar på följande språk** och sedan välja de språk som du vill ha uppdateringar för. Klicka på **Nästa** för att gå till sidan **Välj produkter**, eller välj en annan sida i den vänstra fönsterrutan.

**Välja uppdateringsprodukter**
1.  På sidan **Välj produkter** kan du ange vilka produkter som du vill ha uppdateringar för.

2.  Du kan markera produktkategorier, till exempel Windows, eller vissa produkter, till exempel Windows Server 2003. När du markerar en produktkategori markeras alla produkter som finns under den. Klicka på **Nästa** för att gå till sidan **Välj klassificeringar**, eller välj en annan sida i den vänstra fönsterrutan.

**Välja uppdateringsklassificeringar**
1.  På sidan **Välj klassificeringar** kan du välja de uppdateringsklassificeringar som du vill ha. Du kan välja alla klassificeringar eller en delmängd av dem.

2.  Klicka på **Nästa** för att gå till sidan **Konfigurera synkroniseringsschema**, eller välj en annan sida i den vänstra fönsterrutan.

**Konfigurera synkroniseringsschemat**
1.  Sidan **Ange synkroniseringsschema** visas, där du kan välja om du vill utföra synkroniseringen manuellt eller automatiskt.

2.  Om du väljer att synkronisera manuellt på den här servern måste du initiera synkroniseringen från WSUS-administratörskonsolen.

3.  Om du väljer att synkronisera automatiskt synkroniseras WSUS-servern vid angivna intervall. Ange tiden för den första synkroniseringen och sedan antalet synkroniseringar per dag som servern ska utföra. Om du till exempel anger att det ska vara fyra synkroniseringar en dag, med början klockan 03:00, utförs synkroniseringar vid 03:00, 09:00, 15:00 och 21:00.

När du har slutfört konfigurationsstegen ovan väljer du sidan **Slutförd** i konfigurationsguiden. Du kan starta WSUS-administratörskonsolen genom att markera kryssrutan **Starta snapin-modulen för administration av Windows Server Update Services**, och starta den första synkroniseringen genom att markera kryssrutan **Påbörja inledande synkronisering**.

| ![](images/Cc708447.note(WS.10).gif)Obs!                                                                            |
|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Du kan inte spara konfigurationsändringarna som görs medan servern synkroniseras. Vänta med att göra ändringarna tills synkroniseringen är klar. |

![](images/Cc708447.3f774fd1-af87-47d8-8f50-a5d585687d70(WS.10).gif)

I följande procedurer förklaras hur du utför konfigurationsstegen ovan på sidan **Alternativ** i WSUS-administratörskonsolen:

-   Välja produkter och klassificeringar
-   Uppdateringsfiler och -språk

**Välja produkter och klassificeringar**
1.  Starta WSUS-administratörskonsolen: Klicka på **Start** och peka på **Program**. Peka sedan på **Administrationsverktyg** och klicka därefter på **Microsoft Windows Server Update Services**.

2.  Välj **Alternativ** under WSUS-servern i vänster fönsterruta.

3.  Välj **Produkter och klassificeringar** i den mellersta fönsterrutan.

4.  En dialogruta med två flikar visas: **Produkter** och **Klassificeringar**.

5.  På fliken **Produkter** ska du markera produktkategorin eller en viss produkt som du vill att servern ska hämta uppdateringar för, annars väljer du **Alla produkter**.

6.  På fliken **Klassificeringar** ska du välja önskade uppdateringsklassificeringar, eller annars välja **Alla klassificeringar**.

7.  Spara valen med **OK**.

**Uppdateringsfiler och -språk**
1.  Välj **Uppdateringsfiler och -språk** på sidan **Alternativ**.

2.  En dialogruta med två flikar visas: **Uppdateringsfiler** och **Uppdateringsspråk**.

3.  På fliken **Uppdateringsfiler** kan du välja om du vill lagra uppdateringsfilerna lokalt eller låta alla klientdatorer installera från Microsoft Update. Om du väljer att lagra uppdateringsfilerna på den här servern, kan du välja om du vill hämta enbart de uppdateringar som är godkända eller hämta expressinstallationsfiler.

4.  På fliken **Uppdateringsspråk** kan du välja att hämta uppdateringar för alla språk (standardvärdet) eller hämta uppdateringar för enbart angivna språk. Om den här WSUS-servern har underordnade servrar får de uppdateringar bara på de språk som anges av den överordnade servern.

5.  Spara inställningarna genom att klicka på **OK**.

När du har konfigurerat nätverksanslutningen kan du hämta uppdateringar genom att synkronisera WSUS-servern.

Vid synkronisering kontaktar WSUS-servern Microsoft Update. När kontakten är etablerad kontrollerar WSUS om det har kommit några nya uppdateringar sedan den senaste synkroniseringen genomfördes. Eftersom det här är första gången du synkroniserar WSUS-servern är alla uppdateringar tillgängliga och kan godkännas för installation. Den första synkroniseringen kan ta ganska lång tid.

| ![](images/Cc708447.note(WS.10).gif)Obs!                                                                                                                  |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| I det här dokumentet beskrivs synkronisering med hjälp av standardinställningarna. I WSUS finns även alternativ som du kan använda om du vill minimera bandbredden vid synkronisering. |

**Så här synkroniserar du WSUS-servern**
1.  Välj **Synkroniseringar** i WSUS-administratörskonsolen.

2.  Högerklicka eller gå till fönstret **Åtgärder** till höger och klicka sedan på **Synkronisera nu**.

| ![](images/Cc708447.note(WS.10).gif)Obs!                                                                                                                |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om fönstret **Åtgärder** inte visas till höger om konsolen klickar du på **Visa** i konsolens verktygsfält, klickar på **Anpassa** och markerar sedan kryssrutan **Åtgärdsfönster**. |

När synkroniseringen har slutförts klickar du på **Uppdateringar** i den vänstra panelen så att listan med uppdateringar visas.
