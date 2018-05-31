---
TOCTitle: Tjänsten Administration av RMS
Title: Tjänsten Administration av RMS
ms:assetid: '4bd3e142-f0f6-40e9-a160-deab28ce5b88'
ms:contentKeyID: 18124728
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747560(v=WS.10)'
---

Tjänsten Administration av RMS
==============================

Administrationstjänsten körs på RMS-rotklustret, samt på alla eventuella licensieringskluster. Till administrationstjänsten hör administrationswebbplatsen, med vars hjälp du kan hantera RMS.

Programfilen för administrationsfilen, Default.aspx, finns i den virtuella katalogen Admin *RMS-plats*\\\_wmcs\\Admin. Byt ut *RMS-plats* mot namnet på den webbplats där du har etablerat RMS.

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
</tbody>
</table>
