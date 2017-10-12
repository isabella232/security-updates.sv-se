---
TOCTitle: 'Certifikattabeller för RMS-konfigurationsdatabaser'
Title: 'Certifikattabeller för RMS-konfigurationsdatabaser'
ms:assetid: 'd392663a-1a46-42f6-a71d-f0f2c1843566'
ms:contentKeyID: 18124921
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747760(v=WS.10)'
---

Certifikattabeller för RMS-konfigurationsdatabaser
==================================================

I det här avsnittet beskrivs de certifikattabeller som finns i RMS-konfigurationsdatabasen. Tabellerna innehåller information om de rättighetskontocertifikat som har utfärdats för användare med den aktuella installationen.

UD\_Machines
------------

I följande tabell visas information om maskinvaru-ID:n för alla datorer.

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
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Datatyp</th>
<th style="border:1px solid black;" >Null-värden</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">i_MachineId</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">IDENTITY (1,1) Inte NULL</td>
<td style="border:1px solid black;">Internt index</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">b_PubKeyHash</td>
<td style="border:1px solid black;">binary(20)</td>
<td style="border:1px solid black;">(20) Inte NULL</td>
<td style="border:1px solid black;">Hash-värde för maskinvaru-ID</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">dt_CreateDate</td>
<td style="border:1px solid black;">datetime</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Datum och tid då posten lades till i tabellen</td>
</tr>
</tbody>
</table>
  
UD\_PassportAuthIdentities  
--------------------------
  
I följande tabell visas information om Microsoft® .NET Passport-informationen för användare.
  
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
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Datatyp</th>
<th style="border:1px solid black;" >Null-värden</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">i_UserId</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Internt index</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">i64_Puid</td>
<td style="border:1px solid black;">bigint</td>
<td style="border:1px solid black;">(50) NULL</td>
<td style="border:1px solid black;">Användar-ID för .NET Passport</td>
</tr>
</tbody>
</table>
  
UD\_UserMachine  
---------------
  
I följande tabell länkas certifierade användare till information om motsvarande dator.
  
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
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Datatyp</th>
<th style="border:1px solid black;" >Null-värden</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">i_MachineId</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Internt index</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">i_UserId</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Internt index</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">dt_CreateDate</td>
<td style="border:1px solid black;">datetime</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Datum och tid då posten lades till i tabellen</td>
</tr>
</tbody>
</table>
  
UD\_Users  
---------
  
I följande tabell visas information om användardata.
  
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
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Datatyp</th>
<th style="border:1px solid black;" >Null-värden</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">i_UserId</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">IDENTITY (1,1) Inte NULL</td>
<td style="border:1px solid black;">Internt index</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">b_KeyData</td>
<td style="border:1px solid black;">varbinary(2000)</td>
<td style="border:1px solid black;">(2000) Inte NULL</td>
<td style="border:1px solid black;">Användarens krypterade privata/offentliga nyckel</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">i_KeyDataLength</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Den icke-krypterade privata/offentliga nyckelns längd</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">b_PublicKey</td>
<td style="border:1px solid black;">PublicKey</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Användarens offentliga nyckel</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">i_EncryptionDbId</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Index för det licensieringscertifikat som används för kryptering av det privata/offentliga nyckelparet</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">s_Certificate</td>
<td style="border:1px solid black;">ntext</td>
<td style="border:1px solid black;">Inte angivet</td>
<td style="border:1px solid black;">Används inte</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">dt_Expiration</td>
<td style="border:1px solid black;">datetime</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Användarnyckelns förfallodatum</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">dt_TemporaryExpiration</td>
<td style="border:1px solid black;">datetime</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Förfallodatum och tidpunkt för temporär användning av nyckeln</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">f_Modified</td>
<td style="border:1px solid black;">bit</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Används inte</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">i_Quota</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Aktuell kvotnivå för användaren</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">i_WaitDays</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Antal dagar innan ytterligare kvotbegäran kan lyckas</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">dt_LastConsumption</td>
<td style="border:1px solid black;">datetime</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Datum och tid för sista återstående användarcertifiering</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">dt_CreateDate</td>
<td style="border:1px solid black;">datetime</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Datum och tid då posten lades till i tabellen</td>
</tr>
</tbody>
</table>
  
UD\_Windows AuthIdentities  
--------------------------
  
I följande tabell visas ID:n för alla Windows-autentiserade och Windows-certifierade användare.
  
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
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Datatyp</th>
<th style="border:1px solid black;" >Null-värden</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">i_UserId</td>
<td style="border:1px solid black;">int</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Internt index</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">s_Sid</td>
<td style="border:1px solid black;">Sid</td>
<td style="border:1px solid black;">Inte NULL</td>
<td style="border:1px solid black;">Användarens säkerhets-ID</td>
</tr>
</tbody>
</table>
