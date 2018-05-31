---
TOCTitle: Ändra registerinställningar för anslutningspool
Title: Ändra registerinställningar för anslutningspool
ms:assetid: 'c61d91db-a1ad-4ca5-a492-015da629afbc'
ms:contentKeyID: 18124885
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747660(v=WS.10)'
---

Ändra registerinställningar för anslutningspool
===============================================

Med hjälp av registernycklar som anger egenskaperna för den Active Directory LDAP-anslutningspool (Lightweight Directory Access Protocol) som används i RMS kan du förbättra datorns prestanda.

På datorer där 32-bitarsversionen av Windows Server 2003 körs är följande registernyckel den fullständiga undernyckelsökvägen till registerposterna för anslutningspoolen:

**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\DRMS\\1.0**

På datorer där 64-bitarsversionen av Windows Server 2003 körs är följande registernyckel den fullständiga undernyckelsökvägen till registerposterna för anslutningspoolen:

**HKEY\_LOCAL\_MACHINE\\SoftwareWOW6432Node\\Microsoft\\DRMS\\1.0**

I följande tabell visas de poster som du kan lägga till för att åsidosätta standardinställningarna för Active Directory-anslutningspoolen. Värdena som visas är standardvärden. Mer information om hur frågelistor konstrueras och inställningarna används finns i ”Optimera inställningarna för Active Directory-anslutningspoolen” tidigare i avsnittet.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Typ</th>
<th style="border:1px solid black;" >Standardvärde</th>
<th style="border:1px solid black;" >Beskrivning</th>
<th style="border:1px solid black;" >Obs!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">GC</td>
<td style="border:1px solid black;">Sträng</td>
<td style="border:1px solid black;">name-1, ..., name-n</td>
<td style="border:1px solid black;">Kommaseparerad lista över globala kataloger (med DNS-namn). Med den här nyckeln begränsas RMS till att bara använda angivna globala kataloger.</td>
<td style="border:1px solid black;">Ange de globala kataloger som ska användas med den här inställningen, om du inte vill att RMS ska skapa en frågelista.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">MinGC</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">1</td>
<td style="border:1px solid black;">Minsta antal globala kataloger som måste vara tillgängliga innan RMS kan startas.</td>
<td style="border:1px solid black;"></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">MaxGC</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">15</td>
<td style="border:1px solid black;">Maximalt antal globala kataloger som läggs till i frågelistan med algoritmen för topologiidentifiering.</td>
<td style="border:1px solid black;"></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">ThreshHoldAlive</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">1</td>
<td style="border:1px solid black;">Minsta antal anslutningar som måste vara aktiva innan sökning påbörjas med DiscoveryServices efter globala kataloger att lägga till i frågelistan, så att begäran kan tas emot i RMS.</td>
<td style="border:1px solid black;"></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">RetryDown</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">5</td>
<td style="border:1px solid black;">Antal sändningsförsök innan en anslutning anses som inaktiv.</td>
<td style="border:1px solid black;"></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">TimeRetryDown</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">300</td>
<td style="border:1px solid black;">Antal sekunder att vänta innan ett nytt uppkopplingsförsök görs.</td>
<td style="border:1px solid black;">Denna standardinställning behöver normalt inte ändras.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">TimeRetrySlow</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">30</td>
<td style="border:1px solid black;">Antal sekunder att vänta innan ett nytt försök görs att använda en långsam anslutning.</td>
<td style="border:1px solid black;">Denna standardinställning behöver normalt inte ändras.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">WtRoundRobin</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">1</td>
<td style="border:1px solid black;">Resursallokeringens vikt vid belastningsutjämning.</td>
<td style="border:1px solid black;">Den relativa vikten av resursallokering vid belastningsutjämning. Värdet 1 är det lägsta värdet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">WtThreadCount</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">100</td>
<td style="border:1px solid black;">Vikt för räkning av trådar per anslutning vid belastningsutjämning.</td>
<td style="border:1px solid black;">Den relativa vikten av ett lågt värde vid räkning av trådar.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">WtSlow</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">1,000</td>
<td style="border:1px solid black;">Vikt för långsamma anslutningar vid belastningsutjämning.</td>
<td style="border:1px solid black;">Den relativa vikten av att anslutningen inte är långsam.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">TimeOutForGC</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">5</td>
<td style="border:1px solid black;">Antal sekunder att vänta innan en begäran att lägga till en global katalog i frågelistan gör timeout.</td>
<td style="border:1px solid black;"></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">LdapTimeOut</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">5</td>
<td style="border:1px solid black;">Antal sekunder att vänta innan LDAP API:er gör timeout.</td>
<td style="border:1px solid black;"></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">TopDownExpansionLDAPTimeOut</td>
<td style="border:1px solid black;">DWORD</td>
<td style="border:1px solid black;">40</td>
<td style="border:1px solid black;">Antal sekunder att vänta innan LDAP-expanderingsfrågor uppifrån och ned gör timeout.</td>
<td style="border:1px solid black;"></td>
</tr>
</tbody>
</table>
  
| ![](images/Cc747660.Caution(WS.10).gif)Varning!                                                                              |  
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om du ändrar registret på ett felaktigt sätt kan du skada systemet. Säkerhetskopiera alla viktiga data på datorn innan du ändrar registerinställningarna. |
