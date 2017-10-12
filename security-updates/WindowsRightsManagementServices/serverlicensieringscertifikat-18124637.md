---
TOCTitle: Serverlicensieringscertifikat
Title: Serverlicensieringscertifikat
ms:assetid: '0b35fbcd-25a9-4587-898d-9a30fd1d3c5b'
ms:contentKeyID: 18124637
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720184(v=WS.10)'
---

Serverlicensieringscertifikat
=============================

Ett serverlicensieringscertifikat ger en RMS-server rättigheten att utfärda certifikat och licenser. När den första rotcertifikatservern har etablerats i RMS-distributionen får den ett serverlicensieringscertifikat från Microsofts registreringstjänst. Den processen kallas registrering. Detta certifikat innehåller rotcertifikatserverns offentliga nyckel och det signeras av registreringstjänstens privata nyckel. Andra servrar som läggs till i rotcertifieringsklustret delar på detta certifikat.

Vid etablering får den första licensieringsservern i ett kluster ett serverlicensieringscertifikat från RMS-rotcertifikatservern eller RMS-klustret genom en process som kallas underregistrering. Detta certifikat innehåller licensieringsserverns offentliga nyckel och det signeras av den privata nyckeln för rotcertifikatservern eller -klustret. Andra servrar som läggs till i licensieringsklustret delar på detta certifikat.

Följande tabell är en sammanställning av de rättigheter som servrar beviljas genom serverlicensieringscertifikat.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Beviljar rättighet att utfärda</th>
<th style="border:1px solid black;" >Serverlicensieringscertifikat som utfärdas till en rotcertifikatserver</th>
<th style="border:1px solid black;" >Serverlicensieringscertifikat som utfärdas till en licensieringsserver</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Rättighetskontocertifikat</td>
<td style="border:1px solid black;">Ja</td>
<td style="border:1px solid black;">Nej</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Publiceringslicenser</td>
<td style="border:1px solid black;">Ja</td>
<td style="border:1px solid black;">Ja</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Användarlicenser</td>
<td style="border:1px solid black;">Ja</td>
<td style="border:1px solid black;">Ja</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Licensieringscertifikat för underordnade servrar</td>
<td style="border:1px solid black;">Ja</td>
<td style="border:1px solid black;">Nej</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Klientlicensieringscertifikat</td>
<td style="border:1px solid black;">Ja</td>
<td style="border:1px solid black;">Ja</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc720184.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| I RMS krävs inte separata licensieringsservrar eller -kluster, men sådana kan underlätta för att avlasta mängden licensieringsbegäran från rotcertifikatklustret. Det kan också vara av intresse för administratörer att installera licensieringsservrar som uppfyller behov hos interna avdelningar som behöver direkt kontroll över publiceringen av skyddat innehåll. Det kan t.ex. inträffa att de allmänna principerna inom ett företag, som implementeras via rotcertifikatservern och principmallarna för rättigheter, inte ger vissa av de rättigheter som krävs på en viss avdelning. I så fall kan avdelningen använda en separat licensieringsserver eller ett separat licensieringskluster där avdelningens principmallar för rättigheter lagras och avdelningens licensieringsbegäran hanteras. |
