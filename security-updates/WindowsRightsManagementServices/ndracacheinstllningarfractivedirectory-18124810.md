---
TOCTitle: Ändra cacheinställningar för Active Directory
Title: Ändra cacheinställningar för Active Directory
ms:assetid: '8789a7a5-2065-4fae-9104-e0a70f1f2fb6'
ms:contentKeyID: 18124810
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747586(v=WS.10)'
---

Ändra cacheinställningar för Active Directory
=============================================

Inställningarna i registret anger hur många poster som ska lagras i Active Directory-cachen. Du kan ändra inställningarna om du vill förbättra svarstiden för klientbegäran. Mer information finns i ”Optimera prestanda för katalogtjänster” tidigare i avsnittet. Du kan också ange giltighetstid för den information som lagras i cachen.

På datorer som kör 32-bitarsversionen av Windows Server 2003 är följande registernyckel den fullständiga undernyckelsökvägen till cacheposterna:

**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\DRMS\\1.0\\DirectoryServices**

På datorer som kör 64-bitarsversionen av Windows Server 2003 är följande registernyckel den fullständiga undernyckelsökvägen till cacheposterna:

**HKEY\_LOCAL\_MACHINE\\SoftwareWOW6432Node\\Microsoft\\DRMS\\1.0\\DirectoryServices**

I följande tabell visas de poster som kontrollerar cacheminnets funktioner.

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
<th style="border:1px solid black;" >Typ</th>
<th style="border:1px solid black;" >Standardvärde</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">PrincipalCacheMax</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">1,000</td>
<td style="border:1px solid black;">Maximalt antal enheter (inklusive e-postadresser och säkerhetsidentifierare) som kan lagras i cacheminnet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">PrincipalCacheExpireMinutes</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">12</td>
<td style="border:1px solid black;">Giltighetstid för cachelagrad information för enheter.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">GroupIDCacheMax</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">1,000</td>
<td style="border:1px solid black;">Maximalt antal grupper (inklusive e-postadresser och säkerhetsidentifierare) som kan lagras i cacheminnet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">GroupIDCacheExpireMinutes</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">12</td>
<td style="border:1px solid black;">Giltighetstid för cachelagrad information för gruppmedlemskap.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">GroupMembershipCacheMax</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">1,000</td>
<td style="border:1px solid black;">Maximalt antal kontakter som är medlemmar i en grupp som kan lagras i cacheminnet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">GroupMembershipCacheExpireMinutes</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">12</td>
<td style="border:1px solid black;">Giltighetstid för cachelagrad information för kontakter som är medlemmar i en grupp.</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc747586.Caution(WS.10).gif)Varning!                                                                              |  
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om du ändrar registret på ett felaktigt sätt kan du skada systemet. Säkerhetskopiera alla viktiga data på datorn innan du ändrar registerinställningarna. |
  
| ![](images/Cc747586.note(WS.10).gif)Obs!                                                                                                                                                                                                                                        |  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Med registerposterna **PrincipalCacheExpireMinutes**, **GroupIDCacheExpireMinutes**, **GroupMembershipCacheExpireMinutes** och **ContactMembersofGroupCacheExpireMinutes** kontrolleras även cacheförfallotiden för den lokala Active Directory-cache som lagras i katalogtjänstdatabasen på databasservern. |
