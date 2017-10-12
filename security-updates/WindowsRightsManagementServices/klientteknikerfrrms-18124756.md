---
TOCTitle: Klienttekniker för RMS
Title: Klienttekniker för RMS
ms:assetid: '6980468a-fc8c-489b-966f-2921ec268e74'
ms:contentKeyID: 18124756
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720288(v=WS.10)'
---

Klienttekniker för RMS
======================

I klientdatorer som ingår i en RMS-distribution används följande tekniska funktioner för att tillåta användare att skapa, publicera och använda RMS-skyddat innehåll.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Teknik</th>
<th style="border:1px solid black;" >Beskrivning</th>
<th style="border:1px solid black;" >Utges av</th>
<th style="border:1px solid black;" >Mer information finns i</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">RMS-aktiverade program</td>
<td style="border:1px solid black;">Krävs för att skapa och publicera RMS-skyddat innehåll. Programmen kan vara utvecklade särskilt för RMS, och befintliga program kan skrivas om så att de fungerar ihop med RMS.</td>
<td style="border:1px solid black;">Andra utvecklingsföretag än Microsoft.</td>
<td style="border:1px solid black;">RMS-aktiverade program</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">RMS-datorcertifikat</td>
<td style="border:1px solid black;">Används till att identifiera en viss dator som betrodd i RMS.</td>
<td style="border:1px solid black;">Aktiveringstjänst för RMS version 1.0. Det krävs ingen särskild tjänst för att hämta ett datorcertifikat med RMS SP1.</td>
<td style="border:1px solid black;">RMS-datorcertifikat</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Lockboxar</td>
<td style="border:1px solid black;">Datorns privata nyckel och ett motsvarande certifikat som innehåller datorns offentliga nyckel.</td>
<td style="border:1px solid black;">Aktiveringstjänst för RMS version 1.0. Det krävs ingen särskild tjänst för att hämta en lockbox med RMS SP1. Lockboxen innehåller datorns privata nyckel och utgör den centrala säkerhetsenheten för kryptering och dekryptering.</td>
<td style="border:1px solid black;">Lockboxar</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rättighetskontocertifikat</td>
<td style="border:1px solid black;">Identifiera en viss dator som betrodd i RMS.</td>
<td style="border:1px solid black;">Kontocertifieringstjänst</td>
<td style="border:1px solid black;">Rättighetskontocertifikat</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Klientlicensieringscertifikat</td>
<td style="border:1px solid black;">Tillåt en användare att publicera RMS-skyddat material utan att vara ansluten till nätverket.
(Valfritt)</td>
<td style="border:1px solid black;">RMS publiceringstjänst</td>
<td style="border:1px solid black;">Klientlicensieringscertifikat</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Publiceringslicenser</td>
<td style="border:1px solid black;">Definiera användarrättigheter för innehåll.</td>
<td style="border:1px solid black;">RMS publiceringstjänst. Vid offlinepublicering kan den här licensen utfärdas av klientlicensieringscertifikatet.</td>
<td style="border:1px solid black;">Publiceringslicenser</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Användarlicenser</td>
<td style="border:1px solid black;">Tillåt en användare att använda RMS-skyddat material.</td>
<td style="border:1px solid black;">RMS licensieringstjänst.</td>
<td style="border:1px solid black;">Användarlicenser</td>
</tr>
</tbody>
</table>
