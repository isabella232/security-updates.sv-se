---
TOCTitle: Precertifieringstjänsten i RMS
Title: Precertifieringstjänsten i RMS
ms:assetid: '09957294-167f-4f98-88e9-ae90fbeb26c1'
ms:contentKeyID: 18124653
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720191(v=WS.10)'
---

Precertifieringstjänsten i RMS
==============================

Precertifieringstjänsten körs endast på RMS-rotklustret. Med den här tjänsten kan en server begära rättighetskontocertifikat åt en användare. Den kan också användas till att utveckla anpassade program. Exempel på servrar som använder den här tjänsten är Microsoft Exchange Server 2007 och Microsoft Office SharePoint Server 2007.

Programfilen för precertifieringstjänsten, Precertification.asmx, ligger i den virtuella katalogen Certification i IIS.

Mer information om hur du utvecklar anpassade program finns i den tekniska dokumentationen till Windows Rights Management Services i MSDN Library på [http://go.microsoft.com/fwlink/?LinkId=32972](http://go.microsoft.com/fwlink/?linkid=32972).

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
