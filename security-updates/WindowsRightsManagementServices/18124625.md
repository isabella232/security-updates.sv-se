---
TOCTitle: Konton och behörigheter som krävs för RMS
Title: Konton och behörigheter som krävs för RMS
ms:assetid: '07a51daa-6823-41e6-b453-92f1a0592361'
ms:contentKeyID: 18124625
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720178(v=WS.10)'
---

Konton och behörigheter som krävs för RMS
=========================================

I följande tabell beskrivs de användarrättigheter och -behörigheter som krävs för distribution och administration av RMS.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Aktivitet</th>
<th style="border:1px solid black;" >Användarkonton och behörigheter</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Installera RMS</td>
<td style="border:1px solid black;">Logga in med ett domänkonto som tillhör den lokala administratörsgruppen.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Etablera RMS</td>
<td style="border:1px solid black;">Logga in med ett domänkonto som tillhör den lokala administratörsgruppen. Dessutom måste kontot som används ha utfört en SQL-inloggning med rollen som systemadministratör på SQL Server-databasen så att databaserna kan konfigureras i RMS.
Under etableringen måste du ange RMS-tjänstkontot. Kontot måste ha skapats tidigare. Kontot ska vara ett vanligt domänanvändarkonto utan några ytterligare behörigheter. Kontot läggs till i RMS-tjänstgruppen och är det konto som används i RMS för rutinåtgärder.
Om en enskild server används där databasen finns på samma dator som rotcertifikatservern kan du använda det lokala systemkontot. Men av säkerhetsskäl bör du alltid ange RMS-tjänstkontot i stället för det lokala systemkontot. När databasen finns på en annan server måste du ange RMS-tjänstkontot.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Administrera RMS</td>
<td style="border:1px solid black;">Logga in med ett domänkonto som tillhör den lokala administratörsgruppen. Du kan anpassa säkerhetsinställningarna och hantera åtkomst till administrationssidorna.</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc720178.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                             |  
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Det konto som används till att logga in på RMS-servern behöver inte tillhöra några ytterligare domängrupper (t.ex. gruppen Domänadministratörer). Men för vissa administrativa åtgärder, t.ex. registrering av tjänstens anslutningspunkt och ändring av säkerhetsprinciper, krävs att kontot har ytterligare åtkomsträttigheter. |
