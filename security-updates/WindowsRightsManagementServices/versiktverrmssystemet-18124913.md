---
TOCTitle: 'Översikt över RMS-systemet'
Title: 'Översikt över RMS-systemet'
ms:assetid: 'cbd14635-e17e-42b8-9fd8-6fdce42ffe07'
ms:contentKeyID: 18124913
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747671(v=WS.10)'
---

Översikt över RMS-systemet
==========================

Det här avsnittet innehåller information om hur webbtjänsterna och klientteknikerna fungerar tillsammans i RMS-systemet.

I följande tabell beskrivs de servertyper som ingår i ett RMS-system och vilka funktioner de har. Detaljerad information om distribution finns i ”Distribuera ett RMS-system”.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Server eller kluster</th>
<th style="border:1px solid black;" >Funktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Rotcertifiering</td>
<td style="border:1px solid black;">Hanterar följande RMS-tjänster:
<ul>
<li><strong>Underregistrering</strong>. Hanterar underregistrering av licensieringsservrar.<br />
<br />
</li>
<li><strong>Aktiveringsproxy</strong>. Fungerar som Internetproxy för klientbegäran om lockboxar och RMS-datorcertifikat.<br />
<br />
</li>
<li><strong>Certifiering</strong>. Utfärdar rättighetskontocertifikat.<br />
<br />
</li>
<li><strong>Publicering</strong>. Utfärdar publiceringslicenser.<br />
<br />
</li>
<li><strong>Licensiering</strong>. Utfärdar användarlicenser.<br />
<br />
</li>
</ul>
Varje RMS-system måste innehålla minst en rotcertifikatserver eller ett rotcertifieringskluster. Det kan bara finnas ett rotcertifieringskluster i varje Active Directory-skog.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Licensiering (valfritt)</td>
<td style="border:1px solid black;">Hanterar följande RMS-tjänster:
<ul>
<li><strong>Publicering</strong>. Utfärdar publiceringslicenser.<br />
<br />
</li>
<li><strong>Licensiering</strong>. Utfärdar användarlicenser.<br />
<br />
</li>
</ul>
Licensieringsservrar ingår ofta i ett RMS-system som stöd för enskilda avdelningar eller för att avlasta rotcertifieringsklustret vid licensieringsbegäran. Licensieringsservrar är inte nödvändiga i ett RMS-system.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Databasserver, t.ex. SQL Server</td>
<td style="border:1px solid black;"><ul>
<li>Hanterar databaser för konfiguration, loggning och katalogtjänster för RMS.<br />
<br />
</li>
<li>Sparar rättighetskontocertifikat i konfigurationsdatabasen på rotcertifieringsklustret.<br />
<br />
</li>
</ul></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Domänkontrollant och global katalog</td>
<td style="border:1px solid black;"><ul>
<li>Tillhandahåller tjänster för autentisering av användare samt katalogtjänster.<br />
<br />
</li>
<li>Sparar tjänstidentifierings-URL:en för rotcertifieringsklustret.<br />
<br />
</li>
</ul></td>
</tr>
</tbody>
</table>
 

RMS använder Microsofts registrerings- och aktiveringstjänster för att tillhandahålla en gemensam förtroenderot för systemet. Mer information finns i ”[Förtroendehierarkin i RMS](https://technet.microsoft.com/2d44182f-a653-4383-aba1-dade53f7cf9a)” senare i det här avsnittet.

I följande figur beskrivs de olika komponenterna i ett RMS-system och vilken funktion de har i systemet. Pilarna representerar begäran och svar som skickas mellan de olika komponenterna.

![](images/Cc747671.29138741-d45c-459b-8ead-b9bc3f708dd5(WS.10).gif)

Mer information om varje komponent finns i ”[Programvarukomponenter i RMS](https://technet.microsoft.com/e38a840e-f390-48fd-8354-50108a64f5ca)” senare i det här avsnittet.
