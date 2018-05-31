---
TOCTitle: Hantera serverlicensieringscertifikat
Title: Hantera serverlicensieringscertifikat
ms:assetid: '549979ad-13ee-4abc-8281-3e002a5a9561'
ms:contentKeyID: 18124718
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720272(v=WS.10)'
---

Hantera serverlicensieringscertifikat
=====================================

Serverlicensieringscertifikat upphör att gälla efter en viss tid, normalt efter ett år. Du måste vara inloggad som lokal administratör för att kunna förnya ett serverlicensieringscertifikat. När du förnyar rotcertifikatklustrets serverlicensieringscertifikat skickas en begäran från RMS om förnyelse av serverlicensieringscertifikatet till Microsofts registreringstjänst. När du förnyar certifikatet för en licensieringsserver skickas förnyelsebegäran till den rotcertifikatserver som utfärdade det aktuella certifikatet.

Det finns tre olika händelser som skickas till systemets händelselogg och som du bör övervaka. Händelserna ger dig information antingen om när det datum då serverlicensieringscertifikatet upphör att gälla närmar sig, eller när det har upphört att gälla. I följande tabell visas ID och namn för de här händelserna.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Händelse-ID</th>
<th style="border:1px solid black;" >Händelsenamn</th>
<th style="border:1px solid black;" >Händelsetyp</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">16</td>
<td style="border:1px solid black;">LicensorCertExpiresInOneMonthEvent</td>
<td style="border:1px solid black;">Varning. Tjänsten fortsätter att fungera normalt.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">17</td>
<td style="border:1px solid black;">LicensorCertExpiresInOneWeekEvent</td>
<td style="border:1px solid black;">Varning. Tjänsten fortsätter att fungera normalt.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">18</td>
<td style="border:1px solid black;">LicensorCertExpiredEvent</td>
<td style="border:1px solid black;">Fel. Tjänsten avaktiveras.</td>
</tr>
</tbody>
</table>
