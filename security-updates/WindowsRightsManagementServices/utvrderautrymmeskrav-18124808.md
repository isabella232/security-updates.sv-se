---
TOCTitle: Utvärdera utrymmeskrav
Title: Utvärdera utrymmeskrav
ms:assetid: '89f0138c-946d-47d7-a286-041d4d9606a8'
ms:contentKeyID: 18124808
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747663(v=WS.10)'
---

Utvärdera utrymmeskrav
======================

När du ska avgöra om du ska använda en server eller flera utvärderar du hur många användare som ska använda RMS-distributionen och hur många filer som ska skyddas.

Då får du fram de genomsnittliga användningskraven. Fundera sedan på vilka krav som ställs vid hög belastning, vilket normalt rör sig om cirka tre gånger den genomsnittliga belastningen.

Ta också med företagets feltolerans och krav på tillgänglighet för tjänsten i beräkningen.

RMS har testats med en 2,4 GHz Pentium 4-server med dubbla processorer och 1 GB RAM-minne, vilket kan användas som riktmärke. I den konfigurationen levererade RMS-servern cirka 50 licenser per sekund.

Du kan använda följande värden vid kapacitetsplaneringen, som en uppskattning av åtkomstkraven för ett RMS system.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Transaktion</th>
<th style="border:1px solid black;" >Förekomster</th>
<th style="border:1px solid black;" >Använd klient till server-bandbredd (kB)</th>
<th style="border:1px solid black;" >Använd server till klient-bandbredd (kB)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Licensbegäran</td>
<td style="border:1px solid black;">Upprepade för varje användare och för varje innehåll</td>
<td style="border:1px solid black;">64</td>
<td style="border:1px solid black;">18</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rättighetskontocertifikat</td>
<td style="border:1px solid black;">Endast RMS-initieringstrafik</td>
<td style="border:1px solid black;">12</td>
<td style="border:1px solid black;">16</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Klientregistrering</td>
<td style="border:1px solid black;">Endast RMS-initieringstrafik</td>
<td style="border:1px solid black;">17</td>
<td style="border:1px solid black;">16</td>
</tr>
</tbody>
</table>
  
Dessutom kan antalet Active Directory-frågor påverka dataflödet i nätverket. Normalt är det inte någon avgörande faktor om du distribuerar RMS-servrarna i närheten av de globala katalogerna. Det enda undantaget är om ett fel i alla de globala katalogservrarna på en plats orsakar en växling vid fel (failover) till en annan plats, via en anslutning med lägre kapacitet.
  
I följande tabell visas riktlinjer för vilken bandbredd som krävs för RMS-transaktioner. Använd informationen till att beräkna hur Active Directory-frågor påverkar organisationens nätverk.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Transaktion</th>
<th style="border:1px solid black;" >RMS till global katalog-bandbredd (byte)</th>
<th style="border:1px solid black;" >Global katalog till RMS-bandbredd (byte)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Etablering av RMS-anslutning (ldap_bind)</td>
<td style="border:1px solid black;">1600</td>
<td style="border:1px solid black;">200</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Utvärdering av RMS-gruppmedlemskap (ldap_search)</td>
<td style="border:1px solid black;">200</td>
<td style="border:1px solid black;">100</td>
</tr>
</tbody>
</table>
  
Kontrollera att du använder de siffror som gäller för din distribution när du använder de här referenstabellerna. Om en användare t.ex. tillhör 15 grupper krävs 200 byte för sökbegäran från RMS, medan 1 500 byte (100 byte × 15) krävs för svaret från den globala katalogen.
  
Kapacitetsplaneringen bör baseras på det förväntade antalet begäran om innehållslicenser eftersom de utgör majoriteten av de åtgärder som utförs i RMS. Hastigheten för indata/utdata och diskenhetens dataflöde är inte några avgörande faktorer för RMS eftersom licensbegäran inte omfattar stora datamängder och helt kan hanteras med information som cache-lagrats.
  
CPU-belastningen är den viktigaste faktorn när det gäller att bestämma serverns dataflöde. Välj därför processorer med omsorg. Minnesbehovet i RMS-servrarna ökar när belastningen på servrarna ökar. Om belastningen överstiger serverns maximala dataflöde ställer IIS (Internet Information Services) inkommande begäran i kö i minnet tills de kan bearbetas på servern. När den kögräns som du konfigurerar i IIS uppnås upphör IIS att placera inkommande begäran i kö och nekar i stället nya begäran.
  
Minnesbehovet för RMS (under arbete) för ett belastningsmönster ska rymmas helt inom gränserna för storleken på det fysiska minnet. Den totala minnesstorleken bestäms mer av cachebehovet för gruppexpandering än av något annat. Minst 1 GB RAM-minne rekommenderas för varje RMS-server.
  
På varje RMS-server går det att hantera ett givet antal klientbegäran under en viss tid (ungefär 30 till 50 licenser per sekund). Ett klusters förmåga att utfärda licenser ökar därmed linjärt i förhållande till hur många servrar som används, samtidigt som fler servrar ger ökad pålitlighet. Därför är skalbarhet inte bara något som påverkas av de enskilda servrarna utan också något som påverkas av hur många servrar som distribueras. I de följande konfigurationsexemplen kan du se hur du kan använda uppskattade siffror till att räkna ut kraven på utrymme i RMS-distributionen.
  
-   Konfiguration för låg belastning  
    Vissa organisationer har relativt låga krav när det gäller åtkomstbehov för RMS. En organisation som har ungefär 5 000 användare, där tio procent av användarna samtidigt använder RMS till att skydda e-postinnehåll, kan t.ex. räkna med att en genomsnittlig användare skyddar tre e-postmeddelanden i timmen. Med utgångspunkt i de kraven behöver RMS-servrarna tillhandahålla 1 500 licenser i timmen, vilket motsvarar 0,42 licenser per sekund. Detta är alltså det genomsnittliga åtkomstbehovet. Om du multiplicerar siffran med tre erhåller du det beräknade värdet vid hög belastning – 1,25 licenser per sekund.  
    Med utgångspunkt i den här beräkningen är belastningen relativt låg. Därför räcker det troligen med en RMS-server för den aktuella organisationen.  
-   Konfiguration för normal belastning  
    Många organisationer har relativt stora användargrupper med normala åtkomstkrav. En organisation som har ungefär 40 000 användare, där 50 procent av användarna använder RMS till att skydda innehåll regelbundet, kan t.ex. räkna med att en genomsnittlig användare skyddar sju e-postmeddelanden och ett dokument (eller annan fil) i timmen. Med utgångspunkt i de kraven får vi fram att RMS-servrarna behöver tillhandahålla 160 000 licenser i timmen, vilket motsvarar 44,4 licenser per sekund. Detta är alltså det genomsnittliga åtkomstbehovet. Om du multiplicerar siffran med tre erhåller du det beräknade värdet vid hög belastning – 133,3 licenser per sekund.  
    Med utgångspunkt i den här beräkningen är belastningen relativt hög och tre RMS-servrar kan vara lämpligt för att klara av det aktuella behovet. Vill organisationen ha ett visst utrymme för expansion kan sex RMS-servrar vara lämpligt.  
-   Konfiguration för hög belastning  
    Större organisationer har ofta mycket stora användargrupper med höga åtkomstkrav. En organisation som har ungefär 150 000 användare, där 70 procent av användarna använder Windows RMS till att skydda innehåll regelbundet, kan t.ex. räkna med att en genomsnittlig användare skyddar femton e-postmeddelanden och tre dokument (eller andra filer) i timmen. Med utgångspunkt i de kraven behöver RMS-servrarna tillhandahålla 1 890 000 licenser i timmen, vilket motsvarar 525 licenser per sekund. Detta är alltså det genomsnittliga åtkomstbehovet. Om du multiplicerar siffran med tre erhåller du det beräknade värdet vid hög belastning – 1575 licenser per sekund.  
    Med utgångspunkt i den här beräkningen är belastningen relativt hög och 32 RMS-servrar kan vara lämpligt för att klara av det aktuella behovet. Vill organisationen ha ett visst utrymme för expansion kan 51 RMS-servrar vara lämpligt.
  
När din beräkning visar att cirka 30 till 50 licenser måste tillhandahållas per sekund behöver du ytterligare en RMS-server.
