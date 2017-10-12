---
TOCTitle: 'RMS-servertjänsten'
Title: 'RMS-servertjänsten'
ms:assetid: '772d0a89-c9fb-4430-9434-38cd5add1e86'
ms:contentKeyID: 18124793
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747566(v=WS.10)'
---

RMS-servertjänsten
==================

Servertjänsten körs endast på RMS-rotklustret. Servertjänsten förmedlar en begäran, som görs av en klient vid onlinepublicering om att hämta ett serverlicensieringscertifikat.

Programfilen för servertjänsten, Server.asmx, ligger i den virtuella katalogen Certification i IIS.

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
