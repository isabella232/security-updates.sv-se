---
TOCTitle: Webbtjänster för RMS
Title: Webbtjänster för RMS
ms:assetid: 'ed8dbb2e-0590-4502-afc4-54f66b96d515'
ms:contentKeyID: 18124974
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747728(v=WS.10)'
---

Webbtjänster för RMS
====================

RMS utgör serverkomponenten i ett RMS-system. Kärnfunktionerna implementeras i form av en uppsättning Microsoft® ASP.NET-webbtjänster som körs på Microsoft® Internet Information Services (IIS). RMS-webbtjänsterna distribueras via SOAP-gränssnittet eller via .NET-fjärrhantering.

Webbtjänsterna omfattar följande:

-   Underregistrering av servrar
-   Kontocertifiering av betrodda enheter
-   Licensiering av rättighetsskyddad information
-   RMS-administrationsfunktioner

RMS-webbtjänsterna beskrivs i följande tabell.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Tjänst</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Underregistrering</td>
<td style="border:1px solid black;">Används för att dela ut underordnade serverlicensieringscertifikat till servrar i licensklustret. Tack vare de här certifikaten kan licenskluster användas till att utfärda publiceringslicenser och användarlicenser.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Kontocertifiering</td>
<td style="border:1px solid black;">Används för att dela ut rättighetskontocertifikat till användare. De här certifikaten krävs för att användare ska kunna skaffa publiceringslicenser och användarlicenser för att skapa och använda rättighetsskyddat innehåll.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Aktiveringsproxy</td>
<td style="border:1px solid black;">Tjänsten finns kvar för att skapa kompatibilitet med RMS version 1-klienten. Den skickar begäran om datoraktivering till Microsofts aktiveringstjänst och förser RMS version 1-klienter med lockboxar och RMS-datorcertifikat. Tjänsten används inte av RMS-klienter med Service Pack 1 (SP1) eller senare.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Publicering</td>
<td style="border:1px solid black;">Används för att utfärda publiceringslicenser som gör att användare kan skapa och distribuera rättighetsskyddat innehåll. Används även för att utfärda klientlicensieringscertifikat som gör att användare kan publicera rättighetsskyddat innehåll utan att vara anslutna till det interna nätverk som innehåller RMS.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Licensiering</td>
<td style="border:1px solid black;">Används för att utfärda användarlicenser som gör att användare kan tillämpa rättighetsskyddat innehåll.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Administration</td>
<td style="border:1px solid black;">Används av administratören vid hantering av RMS.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DrmRemote</td>
<td style="border:1px solid black;">Tjänst som bidrar till att webbtjänsterna kan kommunicera med varandra och med andra komponenter i RMS-systemet genom att exponera .NET-fjärrhantering.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Inaktivering</td>
<td style="border:1px solid black;">Används för att göra skyddat innehåll oskyddat och skicka tillbaka det till klienten. Tjänsten installeras med RMS-installationsprogrammet men det finns ingen motsvarande virtuell rot i IIS förrän den aktiveras av administratören. När du aktiverar den här tjänsten avaktiveras alla andra tjänster.</td>
</tr>
</tbody>
</table>
  
Förutom webbtjänsterna installeras en lyssnartjänst för loggning. Loggade data skickas till meddelandekön från samtliga webbtjänster. Loggade data överförs sedan från meddelandekön till loggningsdatabasen.
  
Webbtjänstsprogrammen finns i virtuella IIS-kataloger. De här katalogerna installeras på RMS-servrarna under den webbplats som angavs vid etableringen.
  
Autentisering och åtkomst konfigureras separat för varje virtuell katalog. Åtkomst konfigureras dessutom separat för varje webbtjänst. Mer information om säkerhetsinställningar för virtuella kataloger och webbtjänstfiler finns i [Internet Information Services-funktioner för RMS](https://technet.microsoft.com/bd4dc69f-1e4e-4e95-9ae2-c925d8a14d4c) längre fram i det här avsnittet.
  
Mer information om de olika webbtjänsterna hittar du i [Programvarukomponenter i RMS](https://technet.microsoft.com/e38a840e-f390-48fd-8354-50108a64f5ca) längre fram i det här avsnittet.
