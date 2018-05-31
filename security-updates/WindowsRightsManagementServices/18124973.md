---
TOCTitle: Förbereda installationen av rotcertifikatservern
Title: Förbereda installationen av rotcertifikatservern
ms:assetid: 'ed51605e-8b17-4155-8d83-f6777f499b7b'
ms:contentKeyID: 18124973
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747726(v=WS.10)'
---

Förbereda installationen av rotcertifikatservern
================================================

I testinstallationsexemplet förekommer bara en rotcertifikatserver. Om du vill kan du konfigurera flera servrar, antingen som den del av ett rotcertifikatkluster eller som ett separat licensieringsserverkluster. Konfigurationen av infrastrukturen för alla sådana servrar är identisk så du måste utföra processen som beskrivs i det här avsnittet på var och en av dessa servrar.

När du har installerat domänkontrollanten och konfigurerat databasservrarna (enligt instruktionerna i det förra avsnittet) samt utfört de steg som beskrivs i följande tabell är du redo att installera RMS.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Komponent i infrastrukturen</th>
<th style="border:1px solid black;" >Så här förbereder du servern för RMS-installationen</th>
<th style="border:1px solid black;" >Kommentarer till distribution i produktionsmiljö</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Operativsystem</td>
<td style="border:1px solid black;">Installera operativsystemet Windows Server 2003 på en dator som uppfyller maskinvarukraven för RMS och som ännu inte är ansluten till något nätverk. Använd filsystemet NTFS på partitionen.</td>
<td style="border:1px solid black;">Du bör alltid installera de senaste Service Pack-versionen och de senaste korrigeringarna. Använd NTFS-formaterade partitioner.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Internetanslutning
(valfritt)</td>
<td style="border:1px solid black;">Upprätta en Ethernetanslutning till ett nätverk med Internetanslutning och som är isolerat från produktionsmiljön. Om du ska använda onlineregistrering för att registrera RMS-servern i etableringsprocessen måste servern ha en Internetanslutning.</td>
<td style="border:1px solid black;">Om du använder onlineregistrering bör du se till att Internetanslutningen har en fungerande brandvägg.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">IP-adress</td>
<td style="border:1px solid black;">Tilldela datorn en statisk IP-adress.</td>
<td style="border:1px solid black;">Använd alltid statiska IP-adresser för servrar.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Anslut datorn till domänen</td>
<td style="border:1px solid black;">Logga in på datorn som lokal administratör. Klicka på <strong>Start</strong>, högerklicka på <strong>Den här datorn</strong>, klicka på <strong>Egenskaper</strong>, klicka på fliken <strong>Datornamn</strong> och klicka sedan på <strong>Ändra</strong>.</td>
<td style="border:1px solid black;">Använd samma domän för alla servrar.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Acceptera det föreslagna datornamnet, klicka på <strong>Domän</strong> och skriv sedan in domänens namn, t.ex. Konto.se, och klicka sedan på <strong>OK</strong>. Ange en användaridentifiering som är behörig att ansluta till domänen, klicka på <strong>OK</strong> och starta sedan om datorn när du uppmanas att göra det. När datorn startas om och du ombeds ange inloggningsinformation anger du aktuell domän, användarnamn och lösenord.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Användare och inloggning</td>
<td style="border:1px solid black;">Högerklicka på <strong>Den här datorn</strong>, klicka på <strong>Hantera</strong>, expandera <strong>Lokala användare och grupper</strong>, klicka på <strong>Grupper</strong> och dubbelklicka sedan på <strong>Administratörer</strong>.
Klicka på <strong>Lägg till</strong>, ange namnet på det användarkonto som ska läggas till (t.ex. Mikael@konto.se) och klicka sedan på <strong>OK</strong>. Tilldela användarkontot administratörsbehörigheter. Ange den aktuella användarinformationen när du ombeds att göra det, t.ex. Konto\Administratör.
Logga in på datorn med ett domänanvändarkonto som även har administratörsbehörigheter på den lokala datorn.</td>
<td style="border:1px solid black;">Administratörsbehörigheter krävs om du ska lägga till komponenter i den aktuella datorn. Vissa steg i installationen går inte att utföra med det lokala administratörskontot. Det måste finnas minst en domänanvändare på servern som är en administratör. Dessutom kräver SQL Server systemadministrationsbehörighet för att skapa nya databaser.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Internetanslutning
(valfritt)</td>
<td style="border:1px solid black;">Använd en webbläsare och gå till http://uddi.microsoft.com/ för att kontrollera åtkomsten till Internet. På datorer där Windows Server 2003 körs kan LMHOSTS- och HOSTS-filerna behöva ändras så att domänkontrollanten inkluderas.</td>
<td style="border:1px solid black;">Besök http://uddi.microsoft.com och bekräfta att du kommer åt Internet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Windows-aktivering</td>
<td style="border:1px solid black;">Du kan använda Aktiveringsguiden och aktivera Windows hos Microsoft med en Internetanslutning. Du kan också kontakta Windowsaktiveringen per telefon. Mer information om produktaktiveringen av Windows Server 2003 finns i hjälpen och supportcentret i Windows Server 2003.</td>
<td style="border:1px solid black;">Windows Server 2003 måste aktiveras inom fjorton dagar efter installationen.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Programuppdateringar</td>
<td style="border:1px solid black;">Se till att installera de senaste uppdateringarna för den programvara som är installerad på datorn</td>
<td style="border:1px solid black;">Installera de senaste programvaruuppdateringarna.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Konfigurera Internet Explorer</td>
<td style="border:1px solid black;">I RMS används ett webbadministrationsgränssnitt. Vissa säkerhetsstandardinställningar kan göra att sidor inte visas korrekt. Vissa sidor på webbplatsen Administration av Windows RMS använder popup-fönster för vissa konfigureringsalternativ.</td>
<td style="border:1px solid black;"> </td>
</tr>
</tbody>
</table>
  
När du har utfört alla steg ovan på båda servrarna är du redo att installera och etablera RMS på servrarna.
