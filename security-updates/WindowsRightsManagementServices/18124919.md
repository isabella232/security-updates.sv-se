---
TOCTitle: Underhålla loggningsdatabasen
Title: Underhålla loggningsdatabasen
ms:assetid: 'de55058b-0d1a-4997-8a45-e14678ddd13f'
ms:contentKeyID: 18124919
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747691(v=WS.10)'
---

Underhålla loggningsdatabasen
=============================

En loggpost innehåller kopior av de licenser som utfärdats för olika RMS-åtgärder, t.ex. att registrera användare och tilldela användarlicenser. I sämsta tänkbara fall, när varje loggningspost består av en genomförd användarregistrering eller ett lyckat försök att hämta en användarlicens, lägger varje loggpost 200 kB till storleken på loggningsdatabasen.

Anta till exempel att ett RMS-skyddat e-postmeddelande skickas till alla anställda i ett företag med 50 000 användare och alla öppnar det. Om alla anställda öppnar e-postmeddelandet under en och samma dag växer loggningsdatabasen med 10 GB. Du kan konfigurera lyssnartjänsten så att själva XrML-informationen inte loggas, vilket minskar storleken på den information som sparas.

Du kan skapa skript som arkiverar gammal information i loggningsdatabasen i en andra databas. Exempel på loggningsskript finns i RMS Toolkit som du kan hämta gratis på [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=26724) (http://go.microsoft.com/fwlink/?LinkId=26724).

Variabler som påverkar loggningsdatabasens tillväxt
---------------------------------------------------

Storleken på loggningsdatabasen är beroende av miljön. Ett par startposter i loggen kan förutses, bland annat:

-   Registrering av RMS Server
-   Användarregistrering (en unik begäran för varje dator som varje användare använder)
-   Automatiska användarbegäran för certifikat som används vid offlinepublicering

Den mängd poster som finns i loggningsdatabasen efter den första starten står i relation till det antal användarlicenser för skyddat innehåll som utfärdats. Ett antal faktorer påverkar databasens tillväxt:

-   En ny licens krävs varje gång en användare får åtkomst till skyddat innehåll. Det här är inte standardmetoden för skyddade dokument, utan en valfri inställning. Om du väljer att använda det här kravet kommer databasen att växa snabbare.
-   Förväntat antal skyddade e-postmeddelanden som skickas till varje person varje dag.
-   Förväntat antal unika användare som kommer att läsa de här skyddade e-postmeddelandena.
-   Förväntat antal skyddade Microsoft Office 2003-dokument (Word, PowerPoint och Excel) som produceras av varje användare varje dag.
-   Förväntade mottagare av de skyddade dokumenten.

Den ursprungliga storleken på loggningsdatabasen är cirka 1,7 MB. Då ingår även RMS-serverns begäran om certifikat. När en ny användare registreras får han/hon ett rättighetskontocertifikat och ett klientlicensieringscertifikat. De två händelserna loggas, och tillsammans gör de att databasen växer med 0,06 MB. Varje gång en användare får en licens för skyddat innehåll växer databasen med 0,19 MB.

För att förklara hur siffran beräknas kan vi ta en organisation med 5 000 användare som exempel där RMS distribueras till alla. Varje användare har en dator och det finns två RMS-servrar i organisationen. När distributionen är genomförd skapar varje användare i genomsnitt ett RMS-skyddat e-postmeddelande om dagen och skickar det till fem andra användare. Varje användare skapar också ett RMS-skyddat dokument per dag, som tre andra användare vill få åtkomst till. I följande tabell visas ungefär hur mycket de här aktiviteterna ökar storleken på loggningsdatabasen.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Åtgärd</th>
<th style="border:1px solid black;" >Loggtillväxt</th>
<th style="border:1px solid black;" >Ackumulerad loggstorlek</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">RMS-servern etableras utan fel</td>
<td style="border:1px solid black;">1,7 MB</td>
<td style="border:1px solid black;">1,7 MB</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">5 000 anställda registrerar sig (5000*0,06)</td>
<td style="border:1px solid black;">300 MB</td>
<td style="border:1px solid black;">301,7 MB</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Skyddade e-postmeddelanden läses (25 000*0,19)</td>
<td style="border:1px solid black;">4 750 MB</td>
<td style="border:1px solid black;">5 051,7 MB</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Skyddade dokument används (15 000*0,19)</td>
<td style="border:1px solid black;">2 850 MB</td>
<td style="border:1px solid black;">7 901,7 MB</td>
</tr>
</tbody>
</table>
  
Efter registreringen har loggningsdatabasen alltså en statisk storlek som uppgår till 300 MB. Men den dagliga tillväxten enligt det här exemplet är 7,6 GB – nära begränsningen 8 GB i standardinstallationen av Message Queuing. Om loggningsdatabasen inte är tillgänglig under en dag eller mer börjar du förlora loggposter.
  
Kontrollera storleken på loggningsdatabasen  
-------------------------------------------
  
I din distributionsplan behöver du inkludera en metod för hantering av loggningsdatabasen. Följande hör till de vanligaste metoderna.
  
-   **Rensa och arkivera**  
    Med den här metoden använder du SQL Server-skript till att arkivera valda delar av informationen från loggningsdatabasen i en andra databas när loggposterna når en viss ålder. Här ingår också filtrering av irrelevant information i databaserna så att du inte slösar med utrymmet i den.  
-   **Begränsa informationen som loggas**  
    Loggningsdatabasen består av tre huvudsakliga tabeller. En av dem är **DRMS\_Log\_Filter**, som identifierar vilket fält i huvudtabellen som ska loggas när loggfiltreringen är aktiverad.  
    Posterna i tabellen aktiverad/inaktiverad bestämmer vilka fält i huvudtabellen som loggas med loggningslyssnartjänsten på RMS-servern. Två av fälten (hör ihop med XrML) har redan ställts in på 0 för att avaktivera loggningen, eftersom de två fälten står för cirka 99 % av utrymmet på varje rad med licensbegäran.  
    En annan tabell under databasen **DRMS\_Config\_ServerName\_Port** med namnet **DRMS\_ClusterPolicies** innehåller ett **PolicyName** (principnamn) för **LoggingFiltering** (loggningsfiltrering). **LoggingFiltering** är inte aktiverat som standard. Om du ändrar värdet för **LoggingFiltering** till 1 och startar om loggningslyssnartjänsten minskar tillväxten i databasen i det tidigare exemplet från 7,6 GB per dag till omkring 160 MB per dag.  
-   **Flytta loggningsdatabasen**  
    Ett annat alternativ för att hantera en växande loggningsdatabas är att flytta den till en server med mer diskutrymme. Loggningsdatabasen kan ligga på en annan server än konfigurationsdatabasen. Om du vill flytta databasen till en annan server gör du enligt följande:  
    1.  Avsluta loggningslyssnartjänsten på samtliga RMS-servrar.  
    2.  Kopiera databasen (eller skapa en ny) på en annan server.  
    3.  Redigera RMS-databasen **DRMS\_Config\_ServerName\_Port** genom att välja tabellen **DRMS\_ClusterPolicies** och redigera värdena för **LoggingDatabaseName** (namnet på databasservern) och **LoggingDatabaseServer** (namnet på databasen).  
    4.  Starta om IIS genom att köra IISRESET.exe från kommandoraden.
