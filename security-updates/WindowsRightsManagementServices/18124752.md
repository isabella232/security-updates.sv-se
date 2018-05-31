---
TOCTitle: Listor över återkallade certifikat i RMS
Title: Listor över återkallade certifikat i RMS
ms:assetid: '688d4dfa-c928-4b2f-8116-2f9e87d2b6f7'
ms:contentKeyID: 18124752
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720287(v=WS.10)'
---

Listor över återkallade certifikat i RMS
========================================

I listor över återkallade certifikat definieras innehåll, program, användare eller andra principer som har återkallats. Ett företag kan ange en enhet i en återkallelselista av en eller flera av följande anledningar:

-   En privat nyckel är osäker eller misstänks vara osäker.
-   En ägare begär återkallning av en nyckel som misstänks vara osäker.
-   En enhet är inte längre giltig (en anställd kan t.ex. ha slutat på företaget).
-   Det har uppstått en svag punkt i säkerhetskontrollen (t.ex. kan ett certifikat som utfärdats till en klientdator ha blivit osäkert).
-   Ny certifiering krävs på grund av förändringar av autentisering.
-   Det förekommer säkerhetsläckor i ett RMS-aktiverat program som gör det olämpligt att använda för särskilt känsligt innehåll eller med allt skyddat innehåll.
-   Ett innehåll som distribuerats tidigare är för gammalt eller är inte längre aktuellt.

I följande tabell beskrivs de enheter du kan ange i en återkallelselista och den information som används för att identifiera var och en av dem.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Enhet</th>
<th style="border:1px solid black;" >Identifierare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">En grupp av licenser eller certifikat</td>
<td style="border:1px solid black;">Utfärdarens ID eller offentliga nyckel</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">En grupp av programmanifest</td>
<td style="border:1px solid black;">Utfärdarens ID eller offentliga nyckel</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">En viss licens eller ett visst certifikat</td>
<td style="border:1px solid black;">Licensens ID eller hash</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Ett visst programmanifest</td>
<td style="border:1px solid black;">Licensens ID eller hash</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">En viss enhet</td>
<td style="border:1px solid black;">Enhetens ID eller offentliga nyckel</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Ett visst innehåll</td>
<td style="border:1px solid black;">Innehållets ID</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc720287.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |  
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Vid återkallning och exkludering är alla hash-algoritmer av typen SHA-1 \[NIS94c\], en revision av SHA-algoritmen (Secure Hash Algorithm) som specificeras i Secure Hash Standard (SHS, FIPS 180). SHA-1 beskrivs i standarden ANSI X9.30 (del 2). Om du vill utföra återkallningar med programmanifest måste du antingen extrahera utfärdarens ID eller offentliga nyckel, licens-ID:t eller licenshashvärdet ur programmanifestet. Dock är programmanifest bas-64-kodade så att den informationen inte är tillgänglig för visning. Med Rights Management Client SDK kan du utveckla ett program med metoderna **DRMConstructCertificateChain**, **DRMDeconstructCertificateChain** och **DRMDecode** så att programmanifestet kan avkodas. På så sätt får du tillgång till den information som behövs. Om du vill hindra vissa programs möjligheter att hantera RMS-skyddat innehåll ska du överväga att använda programexkludering till att hindra att användningslicenser tilldelas de programmen med RMS-servern. Begränsningen för exkludering är att det inte kan hindra någon med en giltig användningslicens från att dekryptera RMS-skyddat innehåll. Mer information om programexkludering finns i avsnittet Exkludera program, i ”Använda en RMS-server”. |
  
En återkallelselista är en XrML-fil där följande parametrar anges.
  
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
<td style="border:1px solid black;">ISSUEDTIME</td>
<td style="border:1px solid black;">Systemtidpunkten då XrML-filen skapades. Det här används av REFRESH-villkoret i en användarlicens till att avgöra åldern på listan över återkallade certifikat.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">ISSUER</td>
<td style="border:1px solid black;">Namnet på, samt ID-numret och adressen för utfärdaren av återkallelselistan.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">PUBLICKEY</td>
<td style="border:1px solid black;">Den offentliga nyckeln för utfärdaren av återkallelselistan.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">REVOCATIONLIST</td>
<td style="border:1px solid black;">Namnet och typen på, samt ID-numret för varje återkallad enhet.</td>
</tr>
</tbody>
</table>
