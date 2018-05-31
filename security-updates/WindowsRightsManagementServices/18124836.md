---
TOCTitle: Säkerhet vid etablering
Title: Säkerhet vid etablering
ms:assetid: '9f1282c5-5642-4870-a9a4-c3a485f8ff76'
ms:contentKeyID: 18124836
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747616(v=WS.10)'
---

Säkerhet vid etablering
=======================

Du kan använda webbplatsen Administration av RMS till att etablera RMS-resurser på en befintlig webbsida. Under etableringen skapas virtuella kataloger och programpooler under webbplatsen samtidigt som RMS-databaserna skapas och konfigureras på en databasserver. Servern kan också registreras via Microsofts registreringstjänst under etableringen, förutsatt att servern är ansluten till Internet.

Vid RMS-etableringen används de konton som beskrivs i följande tabell.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Konto</th>
<th style="border:1px solid black;" >Syfte</th>
<th style="border:1px solid black;" >Rättigheter</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Den inloggade användarens konto</td>
<td style="border:1px solid black;">Skapar virtuella kataloger och programpooler. I IIS krävs Windows-autentisering. RMS använder den inloggade användarens identitet, och användaren måste vara inloggad lokalt.</td>
<td style="border:1px solid black;">Fullständig kontroll (den inloggade användaren måste vara en lokal administratör).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Systemkonto</td>
<td style="border:1px solid black;">Bygger den temporära sammanställningsfilen för serieomvandling.</td>
<td style="border:1px solid black;">Läs- och skrivrättigheter för den temporära Windows-mappen C:\Windows\Temp.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">ASPNET-konto</td>
<td style="border:1px solid black;">Skapar den temporära sammanställningsfilen med *.aspx-filer.</td>
<td style="border:1px solid black;">Åtkomst av det temporära cacheminnet C:\Windows\Microsoft.NET\Framework\v1.1.4322\Temporary ASP.NET Files.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Network Services account</td>
<td style="border:1px solid black;">Registrerar tjänstens anslutningspunkt i Active Directory.</td>
<td style="border:1px solid black;"><ul>
<li>Läsrättigheter för webbplatsen för etablering (normalt C:\Inetpub\Wwwroot\Provisioning).<br />
<br />
</li>
<li>Läs- och skrivbehörighet för registernyckeln <strong>DRMS</strong>. Rättigheterna beviljas av RMS-installationsprogrammet som också skapar följande registernyckel.<br />
<br />
På datorer där 32-bitarsversionen av Windows Server 2003 körs:<br />
<br />
<code>HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\1.0</code><br />
<br />
På datorer där 64-bitarsversionen av Windows Server 2003 körs:<br />
<br />
<code>HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\DRMS\1.0</code><br />
<br />
</li>
</ul></td>
</tr>
</tbody>
</table>
 

Vid etableringen utförs följande åtgärder i RMS:

-   På databasservern:
    -   Skapar konfigurations-, katalogtjänst- och loggningsdatabaser.
    -   Beviljar inloggningsrättigheter för RMS-tjänstgruppen.
    -   Installerar lagrade procedurer i databaserna och beviljar körrättigheter för RMS-tjänstgruppen.
    -   Kör frågor på huvuddatabasen.
-   Lägger till RMS-tjänstgruppen i gruppen IIS\_WPG.
-   Skapar en struktur av virtuella kataloger, filer, programpooler för webbtjänsterna och webbplatsen Administration av RMS i C:\\Inetpub\\Wwwroot\\\_wmcs.
-   Anger DACL-listor er för de virtuella katalogerna, filerna och programpoolerna.
-   Beviljar RMS-tjänstgruppen åtkomsträttigheter för den temporära mappen.
-   Krypterar den privata nyckeln för serverlicensiering och sparar den i databasen när du anger skydd av en nyckel. RMS begär ett lösenord under etableringen och får tillgång till DPAPI på datornivå.
-   Installerar loggningslyssnartjänsten.
-   Skapar en kö för loggningsmeddelanden.
-   Ställer in tjänstanslutningspunkten i Active Directory vid etablering av rotcertifikatservern.
