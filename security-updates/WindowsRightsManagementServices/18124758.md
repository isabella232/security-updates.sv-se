---
TOCTitle: Underregistreringstjänsten i RMS
Title: Underregistreringstjänsten i RMS
ms:assetid: '6b05e71c-5e7d-467c-9e13-35ac14d3718a'
ms:contentKeyID: 18124758
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720289(v=WS.10)'
---

Underregistreringstjänsten i RMS
================================

Underregistreringstjänsten körs endast på RMS-rotklustret. Tjänsten svarar på begäran om serverlicensieringscertifikat som skickas från servrar med kluster för enbart licensiering under etableringen.

Programfilen för underregistreringstjänsten, SubEnrollService.asmx, ligger i den virtuella katalogen Certification *RMS-plats*\\\_wmcs\\Certification\\, där *RMS\_Web\_Site* byts ut mot namnet på den webbplats där du har etablerat RMS.

Som standard har endast det lokala systemkontot tillgång till den tjänsten. För att kunna etablera och registrera en underordnad server i ett kluster för enbart licensiering måste administratören för licensieringsservern läggas till i SubEnrollService.asmx i DACL-listan (discretionary access control list) i SubEnrollService.asmx med fullständiga kontrollrättigheter.

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
<td style="border:1px solid black;">SYSTEM</td>
<td style="border:1px solid black;">Fullständig kontroll</td>
</tr>
</tbody>
</table>
