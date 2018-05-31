---
TOCTitle: Visa loggfiler
Title: Visa loggfiler
ms:assetid: '2dc9ed54-76d8-4721-ba93-194845de726a'
ms:contentKeyID: 18124655
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720228(v=WS.10)'
---

Visa loggfiler
==============

Beroende på hur du har distribuerat RMS lagras loggfiler antingen i en databasserver av typen SQL Server eller i Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) Release A. Du kan skriva filter som minskar mängden information som lagras i loggfilerna. Instruktioner om det finns i hjälpen till SQL Server Enterprise Manager.

Storleken på en typisk loggpost är cirka 300 byte. I följande tabell beskrivs de fält som loggas.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Fält</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">HostMachineName</td>
<td style="border:1px solid black;">Den dator där begäran hanterades.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">HostMachineRequestId</td>
<td style="border:1px solid black;">Unik identifierare för aktuell begäran på datorn. Kombinationen av HostMachineName och HostMachineRequestId är en unik identifierare för begäran i klustret.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">RequestTime</td>
<td style="border:1px solid black;">Tid då begäran togs emot, anges i GMT-tid (Greenwich Mean Time).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">RequestPath</td>
<td style="border:1px solid black;">Relativ URL till ASMX-filen, t.ex.: /_wmcs/licensing/Licens.asmx.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">RequestType</td>
<td style="border:1px solid black;">Namnet på den webbmetod som startades, t.ex.: AcquireLicense.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">RequestUserAddress</td>
<td style="border:1px solid black;">Käll-IP-adress för begäran.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">RequestUserAgent</td>
<td style="border:1px solid black;">Användaragentvärde för HTTP-huvud.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">AuthenticatedState</td>
<td style="border:1px solid black;">Här anges om HTTP-anslutningen autentiserades eller inte (True/False).</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">SecureConnectionState</td>
<td style="border:1px solid black;">Här anges om det är en SSL-anslutning eller inte (True/False).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">AuthenticatedId</td>
<td style="border:1px solid black;">Inloggningsnamn för autentiserade begäran. Tomt om AuthenticatedState=False.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">ReceivedXrMLDocument</td>
<td style="border:1px solid black;">Det XrML-dokument som kommer från den som skickade begäran.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">ReceivedXrMLDocumentIssuerChain</td>
<td style="border:1px solid black;">Utfärdarkedjan för det XrML-dokument som anlände.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">IssuedXrMLDocument</td>
<td style="border:1px solid black;">Det XrML-dokument som skickas tillbaka till den som skickade begäran.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">IssuedXrMLDocumentIssuerChain</td>
<td style="border:1px solid black;">Utfärdarkedjan för det utfärdade XrML-dokumentet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">SuccessOrFailure</td>
<td style="border:1px solid black;">Här anges om begäran lyckades eller inte (Succeeded/Failed).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Metadata</td>
<td style="border:1px solid black;">Metadata-fält.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">ErrorInformation</td>
<td style="border:1px solid black;">Beskrivande felmeddelande om något fel inträffat.</td>
</tr>
</tbody>
</table>
