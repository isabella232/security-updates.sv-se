---
TOCTitle: 'RMS-inaktiveringstjänsten'
Title: 'RMS-inaktiveringstjänsten'
ms:assetid: '97677e3b-bc83-47ec-b6db-d326cd94566c'
ms:contentKeyID: 18124843
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747695(v=WS.10)'
---

RMS-inaktiveringstjänsten
=========================

Inaktiveringstjänsten är en särskild webbtjänst som installeras med RMS-installationsprogrammet. Den körs både på rotklustret och på licensieringskluster. När du aktiverar denna tjänst inaktiveras alla andra RMS-webbtjänster på servern.

Tjänsten används till att dekryptera den innehållsnyckel som finns i publiceringslicensen för rättighetsskyddat innehåll och tillhandahålla nyckeln åt klienten efter en begäran om licensiering. Det här medför att innehållet kan sparas utan RMS-skydd. I inaktiveringstjänsten loggas alla begäran från klienter och skickas till loggningslyssnartjänsten genom vilken de registreras i loggningsdatabasen.

Du kan aktivera inaktiveringstjänsten via webbsidan **Säkerhetsinställningar** på webbplatsen Administration. När du har aktiverat tjänsten kan du inte återställa servern till en standardkonfiguration för Windows RMS.

När du har aktiverat tjänsten bör du ändra DACL-listan i filen decommission.asmx så att de användare i företaget som har använt den aktuella servern till att licensiera sitt innehåll får åtkomsträttigheter. Lägg också till RMS-tjänstgruppen i DACL-listan och ge gruppen läs- och körbehörighet om du vill att RMS ska kunna hantera driften. När allt innehåll som publiceras av servern har blivit oskyddat bör du säkerhetskopiera information som rör den privata nyckeln och sedan ta bort RMS från servern.

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
