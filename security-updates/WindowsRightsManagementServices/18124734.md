---
TOCTitle: RMS licensieringstjänst
Title: RMS licensieringstjänst
ms:assetid: '5cad1baf-0304-4e82-b62d-83a4aac2140b'
ms:contentKeyID: 18124734
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720278(v=WS.10)'
---

RMS licensieringstjänst
=======================

Licensieringstjänsten, som utfärdar användarlicenser, körs på RMS-rotklustret samt på eventuella licensieringskluster. Användarlicenser ger användare möjlighet att använda rättighetsskyddat material.

Programfilen för licensieringstjänsten, License.asmx, ligger i den virtuella katalogen Licensing i IIS.

| ![](images/Cc720278.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                            |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du kan etablera ett separat licensieringskluster för att avlasta licensieringsbegäran från rotcertifikatservern eller rotklustret. Du kan också etablera en separat licensieringsserver eller ett separat licensieringskluster för en avdelning, t.ex. för att ge avdelningen möjlighet att upprätta egna rättighetsprinciper. Mer information om vad du bör tänka på finns i "Identifiera kärnkomponenter" i ”RMS: Planering och arkitektur" i den här dokumentationssamlingen. |

DACL-listan (discretionary access control list) för den här tjänsten visas i följande tabell:

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Användare eller grupp</th>
<th style="border:1px solid black;" >Standardbehörighet</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Administratörer</td>
<td style="border:1px solid black;">Fullständig kontroll</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">RMS-tjänstgrupp</td>
<td style="border:1px solid black;">Läs och kör</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">SYSTEM</td>
<td style="border:1px solid black;">Fullständig kontroll</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Användare</td>
<td style="border:1px solid black;">Läs och kör</td>
</tr>
</tbody>
</table>
