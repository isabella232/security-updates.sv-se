---
TOCTitle: 'Migrera en RMS-pilotdistribution till en produktionsdistribution'
Title: 'Migrera en RMS-pilotdistribution till en produktionsdistribution'
ms:assetid: 'ea151946-22fb-4cba-a3ef-fd7a4bf0d292'
ms:contentKeyID: 18124940
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747789(v=WS.10)'
---

Migrera en RMS-pilotdistribution till en produktionsdistribution
================================================================

Många organisationer väljer att distribuera RMS i en pilotdistribution innan tekniken implementeras i hela organisationen. Pilotprogrammet har vanligen ett begränsat antal användare och servern underhålls lokalt av en särskild administratör, i stället för att vara en del av ett datacenter som underhålls av en IT-grupp. När piloten är klar och RMS implementeras i organisationens datacenter för alla klienter, sätts nya RMS-servrar in för att klara ett större antal möjliga användare.

Men det RMS-skyddade innehållet är fortfarande knutet till den RMS-server som användes till att skapa det. Om en server tas bort eller byts ut måste därför flera steg genomföras så att det innehåll som krypterades med RMS-pilotservern kan dekrypteras och licensieras med RMS-produktionsservrarna.

Om du har distribuerat RMS som ett pilotprogram och vill migrera RMS-servern till produktionsmiljön i din organisation, samtidigt som du behåller integriteten för innehållet som skyddats med RMS-pilotservern, ska du skapa en migreringsplan för att övergången ska gå smidigt och för att du ska ha möjlighet att återgå till pilotprogrammet och återställa data om det blir nödvändigt.

Följande steg är exempel på vad migreringsplanen bör innehålla, men din egen plan kan innehålla ytterligare åtgärder.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Server</th>
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Obs!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Pilot</td>
<td style="border:1px solid black;">Säkerhetskopiera RMS-konfigurationsdatabasen.</td>
<td style="border:1px solid black;">Då kan du återställa pilotservern om det skulle bli nödvändigt.
I konfigurationsdatabasen finns den privata RMS-nyckeln.
Kontrollera att du känner till lösenordet till den privata nyckeln.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Pilot</td>
<td style="border:1px solid black;">Om du har använt en HSM (Hardware Security Module) till att skydda den privata RMS-nyckeln ska du säkerhetskopiera HSM-konfigurationen enligt tillverkarens instruktioner.</td>
<td style="border:1px solid black;">Du återställer sedan HSM:en på den nya servern.
Se till att du har alla komponenter som krävs vid installation och konfiguration av HSM tillgängliga.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Pilot</td>
<td style="border:1px solid black;">Exportera den betrodda publiceringsdomänfilen.</td>
<td style="border:1px solid black;">På så sätt går det att dekryptera publiceringslicenser som skapats av den här servern även på andra RMS-servrar och utfärda användarlicenser för skyddat innehåll.
Den betrodda publiceringsdomänen innehåller serverlicensieringscertifikatet, den privata RMS-nyckeln och alla principmallar för rättigheter som upprättats med servern.
Den betrodda publiceringsdomänfilen är en XML-fil som krypteras med ett starkt lösenord som du anger när du skapar filen. Du måste också ha det här lösenordet för att kunna importera den betrodda publiceringsdomänfilen.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Pilot</td>
<td style="border:1px solid black;">Exportera den betrodda användardomänen.</td>
<td style="border:1px solid black;">På så sätt kan användarlicenser beviljas från en annan RMS-server för användare vars rättighetskontocertifikat (RAC) beviljats på RMS-pilotservern.
Den betrodda användardomänen etableras när du importerar den här serverns serverlicensieringscertifikat till den andra RMS-servern.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Förbered den nya servern för att fungera som rotcertifikatserver.</td>
<td style="border:1px solid black;">Kontrollera att den har åtkomst till databasservern och att IIS och Message Queuing finns installerat.
Om det är möjligt bör du använda samma servernamn för den här servern.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Om du använder HSM installerar du HSM:en och återställer konfigurationen från säkerhetskopian som du skapade på pilotservern.</td>
<td style="border:1px solid black;">De referenser som behövs vid dekryptering av den privata RMS-nyckeln etableras.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Installera RMS.</td>
<td style="border:1px solid black;">I RMS verifieras att alla tjänster som krävs är installerade och korrekt konfigurerade.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Etablera RMS med en ny privat nyckel. Om du använder onlineregistrering registreras servern under etableringsprocessen genom att du ansluter till Microsofts registreringstjänst via en Internetuppkoppling. Om det inte finns någon Internetuppkoppling på servern måste du använda offlineregistrering.</td>
<td style="border:1px solid black;">Om servern har ett annat namn än pilotservern kan du ändra URL-inställningen för klustret så att den får samma URL som pilotservern.
Om du inte gör det måste du konfigurera en omdirigering från det tidigare klustrets URL till den nya kluster-URL:en, så att användare med befintligt innehåll kan erhålla användarlicenser.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Om du använder offlineregistrering ska du slutföra den manuella registreringsprocessen för den nya RMS-servern. Mer information finns i ”Så här registrerar du en rotcertifikatserver manuellt” i ”Använda en RMS-server” i dokumentationen.</td>
<td style="border:1px solid black;">RMS-servern kan inte användas innan den har registrerats.
Dessutom kan du inte nå RMS-administrationssidorna innan servern har registrerats.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Importera den betrodda publiceringsdomänfilen som du exporterade i steg 3.</td>
<td style="border:1px solid black;">RMS-tjänstkontot måste ha läsrättigheter för den plats som filen lagrats på om filen ska kunna importeras.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Omsignera alla mallar som importerats med den betrodda publiceringsdomänfilen.</td>
<td style="border:1px solid black;">Mallarna signeras med den privata servernnyckeln. Eftersom servern har en ny privat nyckel måste mallarna signeras om för att vara giltiga. Mer information finns i ”Så här omsignerar du en principmall för rättigheter” i ”Använda en RMS-server” i dokumentationen.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Distribuera mallarna till de klientdatorer som ingick i pilotuppsättningen.</td>
<td style="border:1px solid black;">Gamla mallar måste tas bort och bytas ut mot mallar som signerats på den här servern.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Produktion</td>
<td style="border:1px solid black;">Importera den betrodda användardomänfilen som du exporterade i steg 4.</td>
<td style="border:1px solid black;">Det här medför att gamla klientlicensieringscertifikat och rättighetskontocertifikat kan användas.
Om användarkonton flyttas mellan skogar under migreringen bör du observera att kontona måste ha motsvarande SMTP-proxy.</td>
</tr>
</tbody>
</table>
 

När du är klar med installationen av produktionsservern bör du kontrollera att pilotanvändarna fortfarande kan skapa och läsa tidigare skyddad e-post. Sedan kan du lägga till så många RMS-servrar till klustret som du behöver för de användare som finns i organisationen.
