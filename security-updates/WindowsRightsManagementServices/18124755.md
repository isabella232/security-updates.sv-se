---
TOCTitle: 'Översikt av RMS-certifikat och -licenser'
Title: 'Översikt av RMS-certifikat och -licenser'
ms:assetid: '637ccfca-318e-4346-85b5-0945b058fb9c'
ms:contentKeyID: 18124755
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747595(v=WS.10)'
---

Översikt av RMS-certifikat och -licenser
========================================

I följande tabell ges en översikt över de certifikat och licenser som förekommer i RMS. De beskrivs i detalj längre fram i avsnittet.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Certifikat eller licens</th>
<th style="border:1px solid black;" >Syfte</th>
<th style="border:1px solid black;" >Innehåll</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Serverlicensieringscertifikat</td>
<td style="border:1px solid black;">Det serverlicensieringscertifikat som utfärdas till licensieringsservrar ger rättighet att utfärda:
<ul>
<li>Publiceringslicenser<br />
<br />
</li>
<li>Användarlicenser<br />
<br />
</li>
<li>Klientlicensieringscertifikat<br />
<br />
</li>
<li>Principmallar för rättigheter<br />
<br />
</li>
</ul>
Det serverlicensieringscertifikat som utfärdas till rotcertifieringsklustret ger dessutom rättighet att utfärda:
<ul>
<li>Rättighetskontocertifikat till klienter<br />
<br />
</li>
<li>Serverlicensieringscertifikat till licensieringsservrar<br />
<br />
</li>
</ul></td>
<td style="border:1px solid black;">Det serverlicensieringscertifikat som utfärdas till en licensieringsserver innehåller licensieringsserverns offentliga nyckel.
Det serverlicensieringscertifikat som utfärdas till rotcertifikatservern innehåller rotcertifikatserverns offentliga nyckel.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Klientlicensieringscertifikat</td>
<td style="border:1px solid black;">Certifikat som ger användare rättighet att publicera RMS-skyddat innehåll utan att vara ansluten till företagets nätverk.</td>
<td style="border:1px solid black;">Innehåller certifikatets offentliga nyckel och den privata nyckeln för det certifikat som krypterats med den offentliga nyckeln för den användare som begärt certifikatet. Innehåller också den offentliga nyckeln för den server som har utfärdat certifikatet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">RMS-datorcertifikat</td>
<td style="border:1px solid black;">Certifikat som identifierar en dator eller enhet som är betrodd av RMS-systemet.</td>
<td style="border:1px solid black;">Innehåller den aktiverade datorns offentliga nyckel. Motsvarande privata nyckel finns i datorns lockbox.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rättighetskontocertifikat</td>
<td style="border:1px solid black;">Identifierar en användare av en viss dator eller enhet.</td>
<td style="border:1px solid black;">Innehåller användarens offentliga nyckel och användarens privata nyckel, som krypteras med den aktiverade datorns offentliga nyckel.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Publiceringslicenser</td>
<td style="border:1px solid black;">Anger de rättigheter som gäller för det RMS-skyddade innehållet.</td>
<td style="border:1px solid black;">Innehåller den symmetriska innehållsnyckeln för dekryptering av innehållet, som krypteras med den offentliga nyckeln för den server som utfärdat licensen.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Användarlicenser</td>
<td style="border:1px solid black;">Anger de rättigheter en viss autentiserad användare har att använda det RMS-skyddade innehållet.</td>
<td style="border:1px solid black;">Innehåller den symmetriska innehållsnyckeln för dekryptering av innehållet, som krypteras med användarens offentliga nyckel.</td>
</tr>
</tbody>
</table>
