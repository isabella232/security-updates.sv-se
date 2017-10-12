---
TOCTitle: Katalogtjänstdatabasen i RMS
Title: Katalogtjänstdatabasen i RMS
ms:assetid: '6f6b8586-5d17-4a40-94a3-4dc738195301'
ms:contentKeyID: 18124773
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747617(v=WS.10)'
---

Katalogtjänstdatabasen i RMS
============================

Katalogtjänstdatabasen, som innehåller information om användare, identifierare (t.ex. e-postadresser), säkerhets-ID (SID), gruppmedlemskap och alternativ identifierare, ligger på databasservern. Informationen hämtas via LDAP-frågor som ställs till den globala katalogen i Active Directory av licensieringstjänsten i RMS. Mer information om processen och dess syfte finns i ”[Cacheminnet för Active Directory i RMS](https://technet.microsoft.com/c721a2eb-2fe9-4346-b426-3cc169b97265)” senare i det här avsnittet.

RMS-tjänstgruppen har körrättigheter för katalogtjänstdatabasens sparade procedurer.

I följande tabell beskrivs de attribut i Active Directory som sparas i katalogtjänstdatabasens tabeller.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Tabell</th>
<th style="border:1px solid black;" >Attribut</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">GroupAliases</td>
<td style="border:1px solid black;"><ul>
<li>GroupName: Gruppens alias<br />
<br />
</li>
<li>GroupID: Det unika ID-numret för denna grupp<br />
<br />
</li>
</ul></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">GroupIdentifiers</td>
<td style="border:1px solid black;"><ul>
<li>GroupDN: Det särskilda namnet i Active Directory för denna grupp<br />
<br />
</li>
<li>GroupID: Det unika ID-numret för denna grupp<br />
<br />
</li>
<li>Expiration: Det datum och klockslag då den sparade informationen om denna grupp förfaller<br />
<br />
</li>
</ul></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">GroupMembership</td>
<td style="border:1px solid black;"><ul>
<li>GroupID: Det unika ID-numret för denna grupp<br />
<br />
</li>
<li>ParentID: Det unika ID-numret för den grupp som denna grupp är medlem av<br />
<br />
</li>
</ul></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">PrincipalAliases</td>
<td style="border:1px solid black;"><ul>
<li>PrincipalName: Ett alias för enheten<br />
<br />
</li>
<li>PrincipalID: Det unika ID-numret för denna enhet<br />
<br />
</li>
</ul></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">PrincipalIdentifiers</td>
<td style="border:1px solid black;"><ul>
<li>PrincipalID: Det unika ID-numret för denna enhet<br />
<br />
</li>
<li>Expiration: Det datum och klockslag då den sparade informationen om denna enhet förfaller<br />
<br />
</li>
</ul></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">PrincipalMembership</td>
<td style="border:1px solid black;">Varje rad i denna tabell innehåller det unika ID-numret för en enhet och det unika ID-numret för en grupp som är medlem av den.
<ul>
<li>PrincipalID: Det unika ID-numret för denna enhet<br />
<br />
</li>
<li>ParentID: Det unika ID-numret för den grupp som denna enhet är medlem av<br />
<br />
</li>
</ul></td>
</tr>
</tbody>
</table>
