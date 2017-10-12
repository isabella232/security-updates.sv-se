---
TOCTitle: 'RMS-tjänstlokaliseringstjänsten'
Title: 'RMS-tjänstlokaliseringstjänsten'
ms:assetid: '6f410cc9-5d5b-4df3-bf4f-7b13811eb52f'
ms:contentKeyID: 18124769
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747548(v=WS.10)'
---

RMS-tjänstlokaliseringstjänsten
===============================

Tjänstlokaliseringstjänsten körs både på RMS-roten och licensieringskluster. Tjänsten tillhandahåller anslutnings-URL-adressen till klustret till Active Directory så att RMS-aktiverade klienter kan använda den vid identifiering av tjänster.

Programfilen för tjänsten, ServiceLocator.asmx, ligger i de virtuella katalogerna Certification och Licensing i IIS.

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
