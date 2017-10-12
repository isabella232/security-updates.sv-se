---
TOCTitle: RMS publiceringstjänst
Title: RMS publiceringstjänst
ms:assetid: '4c0c8fe3-695c-4b2c-a2d3-cab9b52bbb25'
ms:contentKeyID: 18124711
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720267(v=WS.10)'
---

RMS publiceringstjänst
======================

Publiceringstjänsten, som utfärdar publiceringslicenser, körs på RMS-rotklustret samt på eventuella licensieringskluster. Publiceringslicenser definierar principer för hur användarlicenser ska levereras.

Programfilen för publiceringstjänsten, Publish.asmx, ligger i den virtuella katalogen Licensing i IIS.

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
<td style="border:1px solid black;">Läs och Kör</td>
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
