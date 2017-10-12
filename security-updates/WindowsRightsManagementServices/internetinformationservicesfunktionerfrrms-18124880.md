---
TOCTitle: 'Internet Information Services-funktioner för RMS'
Title: 'Internet Information Services-funktioner för RMS'
ms:assetid: 'bd4dc69f-1e4e-4e95-9ae2-c925d8a14d4c'
ms:contentKeyID: 18124880
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747649(v=WS.10)'
---

Internet Information Services-funktioner för RMS
================================================

De grundläggande tjänsterna i RMS utgörs av en uppsättning ASP .NET-webbtjänster. Dessa webbtjänster körs på Microsoft® Internet Information Services (IIS). Vid serveretableringen skapas virtuella kataloger för RMS i IIS. Programfilerna för webbtjänsterna installeras i de virtuella katalogerna.

Vid serveretableringen kan du välja den webbplats där du vill att de virtuella katalogerna ska skapas genom att markera ett alternativ i en lista över webbplatser på servern. Innan du etablerar en server kan det vara lämpligt att skapa en särskild webbplats för RMS. Om du gör det kan du konfigurera autentiserings- och åtkomstrestriktioner som är specifika för din RMS-distribution.

Som standard skyddas programfilerna för webbtjänsterna och de virtuella katalogerna av DACL-listor (discretionary access control lists) för att förhindra obehörig åtkomst av deras funktioner. ACE-posterna (access control entries), d.v.s. posterna för åtkomstkontroll, i de här listorna är följande:

-   Administratörsgruppen har full kontroll
-   Det lokala systemet har full kontroll
-   RMS-tjänstgruppen har läs- och körrättigheter
-   Gäster och användare har läs- och körrättigheter samt rättighet att visa innehåll i mappar
-   Anonym åtkomst är inte tillåten

Av följande tabell framgår vilka virtuella kataloger som skapas i IIS och vilka tjänster som installeras i dem.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Virtuell katalog</th>
<th style="border:1px solid black;" >Tjänst</th>
<th style="border:1px solid black;" >Webbtjänstfil</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">_wmcs</td>
<td style="border:1px solid black;">Detta är den virtuella katalogen för administration av RMS-klustret</td>
<td style="border:1px solid black;">Ej tillämpligt</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Certifiering</td>
<td style="border:1px solid black;">Denna virtuella katalog innehåller de tjänster som stödjer RMS-certifiering</td>
<td style="border:1px solid black;">Ej tillämpligt</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Aktiveringsproxy</td>
<td style="border:1px solid black;">Activation.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Kontocertifiering</td>
<td style="border:1px solid black;">Certification.asmx</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Precertifiering</td>
<td style="border:1px solid black;">Precertification.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Tjänstidentifiering</td>
<td style="border:1px solid black;">ServiceLocator.asmx</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Server</td>
<td style="border:1px solid black;">Server.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Servercertifiering</td>
<td style="border:1px solid black;">ServerCertification.asmx</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Certifiering av mobila enheter</td>
<td style="border:1px solid black;">MobileDeviceCertfication.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Registrering</td>
<td style="border:1px solid black;">SubEnrollService.asmx</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Licensiering</td>
<td style="border:1px solid black;">Denna virtuella katalog innehåller de tjänster som har funktioner för RMS-licensiering</td>
<td style="border:1px solid black;">Ej tillämpligt</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Licensiering</td>
<td style="border:1px solid black;">License.asmx</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Publicering</td>
<td style="border:1px solid black;">Publish.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Server</td>
<td style="border:1px solid black;">Server.asmx</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Tjänstidentifiering</td>
<td style="border:1px solid black;">ServiceLocator.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Admin</td>
<td style="border:1px solid black;">Denna virtuella katalog innehåller tjänster med RMS-administrationsfunktioner</td>
<td style="border:1px solid black;">Ej tillämpligt</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Administration</td>
<td style="border:1px solid black;">AdminSvc.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">DrmRemote</td>
<td style="border:1px solid black;">Gränssnitt för .NET Remoting</td>
<td style="border:1px solid black;">Ej tillämpligt</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DirectoryServices</td>
<td style="border:1px solid black;">Det här är en underkatalog till DrmRemote</td>
<td style="border:1px solid black;">Ej tillämpligt</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc747649.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Administrationstjänsten har strängare restriktioner än de andra webbtjänsterna eftersom de gränssnitt tjänsten tillhandahåller gör det möjligt att konfigurera RMS. Av denna anledning har inte medlemmar i användargruppen tillgång till administrationstjänsten. Dessutom är IP-filtrering aktiverad, vilket gör att användare endast får tillgång till den lokala datorn. Gästanvändare beviljas inte tillgång till den virtuella katalogen DirectoryServices. Tjänstlokaliseringstjänsten ger också full kontroll till Network Service-kontot. För att kunna etablera en licensieringsserver måste du ändra standardinställningarna så att RMS-administratören får åtkomsträttigheter. |
