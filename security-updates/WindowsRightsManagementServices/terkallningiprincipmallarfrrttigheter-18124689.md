---
TOCTitle: Återkallning i principmallar för rättigheter
Title: Återkallning i principmallar för rättigheter
ms:assetid: '287c5b92-fcb5-4295-9c2b-4e37e643beb2'
ms:contentKeyID: 18124689
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720226(v=WS.10)'
---

Återkallning i principmallar för rättigheter
============================================

Återkallningsvillkor anges i principmallar för rättigheter. De återkallningsvillkor du anger i en principmall för rättigheter läggs i en XrML REFRESH-tagg i den publiceringslicens som utfärdas mot mallen. Den resulterande användarlicensen som utfärdas av servern innehåller också REFRESH-taggen.

I följande tabell beskrivs de parametrar som förekommer i REFRESH-taggen.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Parameter</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">ID</td>
<td style="border:1px solid black;">ID-numret för återkallelselistan.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">ADDRESS</td>
<td style="border:1px solid black;">URL- eller UNC-sökvägen till återkallelselistan.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">PUBLICKEY</td>
<td style="border:1px solid black;">Den offentliga nyckeln för utfärdaren av återkallelselistan. Denna offentliga nyckel motsvarar den privata nyckel som använts för att signera återkallelselistan.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">INTERVALTIME</td>
<td style="border:1px solid black;">Återkallelselistans maximala ålder i dagar. Om listan över återkallade certifikat i cacheminnet är äldre än INTERVALTIME medger hämtas den nyaste återkallelselistan från den URL som anges i ADDRESS med RMS-klienten. På detta sätt säkerställs att en aktuell återkallelselista används.</td>
</tr>
</tbody>
</table>
  
Mer information om hur du skapar principmallar för rättigheter finns i ”Skapa och ändra principmallar för rättigheter” i ”Använda en RMS-server”.
