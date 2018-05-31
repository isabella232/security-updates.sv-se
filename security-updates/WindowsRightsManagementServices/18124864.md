---
TOCTitle: 'RMS-nyckeldefinitioner'
Title: 'RMS-nyckeldefinitioner'
ms:assetid: 'b052305c-1db7-434a-bad9-26d704156776'
ms:contentKeyID: 18124864
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747729(v=WS.10)'
---

RMS-nyckeldefinitioner
======================

I följande tabell visas de nycklar som används i RMS-systemet.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Nyckel</th>
<th style="border:1px solid black;" >Användningsområde</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Servernycklar</td>
<td style="border:1px solid black;"><strong>Offentlig nyckel</strong>
Krypterar innehållsnyckeln i en publiceringslicens så att bara RMS-servern kan hämta innehållsnyckeln. Utfärdar användarlicenser mot denna publiceringslicens.
<strong>Privat nyckel</strong>
Signerar alla certifikat och licenser som utfärdas av servern.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Datornycklar</td>
<td style="border:1px solid black;"><strong>Offentlig nyckel</strong>
Krypterar rättighetskontocertifikatets privata nyckel.
<strong>Privat nyckel</strong>
Dekrypterar rättighetskontocertifikatet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Klientlicensieringsnycklar</td>
<td style="border:1px solid black;"><strong>Offentlig nyckel</strong>
Krypterar den symmetriska innehållsnyckeln i de publiceringslicenser den utfärdar.
<strong>Privat nyckel</strong>
Signerar publiceringslicenser som utfärdas lokalt när användaren inte är ansluten till nätverket.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Användarnycklar</td>
<td style="border:1px solid black;"><strong>Offentlig nyckel</strong>
Krypterar innehållsnyckeln i en användarlicens så att bara en viss användare kan använda det RMS-skyddade innehållet med hjälp av den licensen.
<strong>Privat nyckel</strong>
Ger en användare rättighet att använda RMS-skyddat material.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Innehållsnycklar</td>
<td style="border:1px solid black;">Krypterar RMS-skyddat innehåll när den användare som skapat innehållet publicerar det.</td>
</tr>
</tbody>
</table>
