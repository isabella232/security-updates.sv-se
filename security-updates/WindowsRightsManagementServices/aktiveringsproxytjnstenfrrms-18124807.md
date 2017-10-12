---
TOCTitle: Aktiveringsproxytjänsten för RMS
Title: Aktiveringsproxytjänsten för RMS
ms:assetid: '6b9d33ef-466b-405b-a768-54e5615d6770'
ms:contentKeyID: 18124807
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747608(v=WS.10)'
---

Aktiveringsproxytjänsten för RMS
================================

Alla begäran om datoraktivering i RMS version 1.0 går via aktiveringsproxytjänsten, som endast körs på RMS-rotklustret. Du måste aktivera en klientdator för att den ska kunna användas med RMS till att publicera och använda rättighetsskyddat innehåll. RMS-klienter med Service Pack 1 är "självaktiverande" och behöver inte använda aktiveringsproxyservern eller Microsofts aktiveringstjänst för att lockbox och datorcertifikat ska skapas.

Aktiveringsproxytjänsten vidarebefordrar aktiveringsbegäran från RMS version 1.0-klienter till Microsofts aktiveringstjänst, som skapar och returnerar en anpassad lockbox och ett motsvarande RMS-datorcertifikat som är unika för den aktuella användaren och datorn. Aktiveringsproxytjänsten skickar därefter tillbaka dem till klienten som gjort begäran.

Programfilen för aktiveringsproxytjänsten, Activation.asmx, ligger i den virtuella katalogen Certification i IIS. DACL-listan (discretionary access control list) för den här tjänsten visas i följande tabell:

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
<td style="border:1px solid black;">Gäster</td>
<td style="border:1px solid black;">Läs och kör</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">RMS-tjänstgrupp</td>
<td style="border:1px solid black;">Läs och kör</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">SYSTEM</td>
<td style="border:1px solid black;">Fullständig kontroll</td>
</tr>
</tbody>
</table>
