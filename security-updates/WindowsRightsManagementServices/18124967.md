---
TOCTitle: Kontocertifieringstjänsten i RMS
Title: Kontocertifieringstjänsten i RMS
ms:assetid: 'fb294969-850e-44b4-8f6a-ca5d5cec1bf1'
ms:contentKeyID: 18124967
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747802(v=WS.10)'
---

Kontocertifieringstjänsten i RMS
================================

Precertifieringstjänsten körs endast på rotklustret. Med den här tjänsten skapas rättighetskontocertifikat som knyter användarkonton till bestämda datorer. Med ett rättighetskontocertifikat kan en användare publicera och använda rättighetsskyddat innehåll med en specifik dator.

Programfilen för kontocertifieringstjänsten, Certification.asmx, ligger i den virtuella katalogen Certification i IIS.

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
