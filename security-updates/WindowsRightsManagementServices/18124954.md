---
TOCTitle: Planera klusterkrav för RMS
Title: Planera klusterkrav för RMS
ms:assetid: 'ec4023eb-4d39-4551-9789-c8a2d973a55b'
ms:contentKeyID: 18124954
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747792(v=WS.10)'
---

Planera klusterkrav för RMS
===========================

Om du använder RMS i en klustermiljö bör du tänka igenom hur följande situationer, som kan förekomma i organisationen, ska hanteras.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Situation</th>
<th style="border:1px solid black;" >Rekommenderas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Ett stort antal datorer använder RMS.</td>
<td style="border:1px solid black;">Du kan använda Windows Update, ett skript eller en metod för programvarudistribution, t.ex. Systems Management Server (SMS) eller grupprinciper till att installera och aktivera klientprogramvaran Microsoft Windows Rights Management Services.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Ett stort antal klientbegäran.</td>
<td style="border:1px solid black;">Använd en server som belastningsutjämnare, tjänsten Utjämning av nätverksbelastning eller en maskinvarubaserad belastningsutjämning till att distribuera begäran i klustret.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Två nätverksadaptrar som använder virtuell IP-adressering för hantering av både extranät- och intranätbegäran.</td>
<td style="border:1px solid black;">Kontrollera att eventuell DNS-registrering som visar de virtuella IP-adresserna för extranätet också visar adressen för intranätet.
Interna användarlicensbegäran kommer att misslyckas om inte DNS-registrering utförs för intranätet. Om det inte går att ändra DNS-resursposterna kan du ändra värdtabellen för varje server som ingår i klustret så att kluster-URL:en mappas till klustrets virtuella IP-adress. DNS-registreringen måste göras innan du etablerar RMS. Om du redan har Windows RMS måste du avinstallera det och sedan upprepa etableringsprocessen.</td>
</tr>
</tbody>
</table>
