---
TOCTitle: Konfigurera en domänkontrollant och databasserver
Title: Konfigurera en domänkontrollant och databasserver
ms:assetid: 'd20f8305-9f9e-4760-bfbf-82824db60d1f'
ms:contentKeyID: 18124950
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747681(v=WS.10)'
---

Konfigurera en domänkontrollant och databasserver
=================================================

Innan du installerar en rotcertifikatserver eller licensieringsserver bör du kontrollera att du har implementerat domän- och databasfunktioner med Active Directory och en databasserver, t.ex. SQL Server 2000 med Service Pack 3 (SP3) eller Microsoft® SQL Server 2000 Desktop Engine (MSDE 2000) version A. Även om produktionsmiljön redan har de komponenter som krävs bör du inte använda den vid testning.

Med följande processer konfigurerar du både en domänkontrollant och en databasserver på en enskild dator i ett isolerat nätverk som ska användas för testning av serversidan.

| ![](images/Cc747681.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| I det här exemplet körs databasservern på domänkontrollanten. I en produktionsmiljö bör du inte installera några andra komponenter på en domänkontrollant. Dessutom är Active Directory och databasservern installerade på samma dator i exemplet för att möjliggöra en installation av hela infrastrukturen på minsta möjliga antal datorer. |

Om du väljer att använda MSDE 2000 som databasserver bör du vara medveten om att den inte har funktioner för nätverksgränssnitt och att det står i användarvillkoren för MSDE 2000 att du inte får använda klientverktyg i SQL Server till att ändra en MSDE-databas. Den här begränsningen gör att det inte går att visa loggningsinformation eller att ändra data som lagras i konfigurationsdatabasen. Därför bör du bara använda MSDE 2000 för RMS-databaser i testmiljö.

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
<th style="border:1px solid black;" >Stegvisa instruktioner för hur du konfigurerar en domänkontrollant och databasserver</th>
<th style="border:1px solid black;" >Kommentarer till distribution i produktionsmiljö</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Operativsystem</td>
<td style="border:1px solid black;">Installera Windows 2000 Server med SP3 eller senare, eller Windows Server 2003 på en dator som uppfyller maskinvarukraven för RMS men inte är ansluten till ett nätverk. Använd filsystemet NTFS på partitionen.</td>
<td style="border:1px solid black;">Du bör alltid installera den senaste Service Pack-versionen och de senaste uppdateringarna. Använd NTFS-formaterade partitioner.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Nätverksanslutning</td>
<td style="border:1px solid black;">Upprätta en anslutning till ett nätverk med Internetanslutning som är isolerat från produktionsmiljön.</td>
<td style="border:1px solid black;">Internetanslutningen ska vara utrustad med en lämplig brandvägg.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">IP-adress</td>
<td style="border:1px solid black;">Tilldela datorn en statisk IP-adress.</td>
<td style="border:1px solid black;">Använd alltid statiska IP-adresser för servrar.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Active Directory</td>
<td style="border:1px solid black;">Logga in som en lokal administratör.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Klicka på <strong>Start</strong>, klicka på <strong>Kör</strong>, skriv in <code>dcpromo</code> i rutan <strong>Öppna</strong> och klicka sedan på <strong>OK</strong>.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Slutför installationsguiden för Active Directory när den startas och skapa en ny domän i en ny skog. Acceptera alla standardalternativ utom följande:
Ange domännamnet, t.ex. konto.se.
Låt guiden konfigurera DNS på datorn.
Välj <strong>Behörigheter som endast är kompatibla med Windows 2000-servrar</strong> om alla domänkontrollanter kör Windows 2000 eller senare.
Ange ett starkt lösenord för det lokala administratörskontot.</td>
<td style="border:1px solid black;">Konfigurera nya domäner i Active Directory om RMS-implementeringen kräver det.
Använd alltid starka lösenord för alla konton.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Starta om datorn när du ombeds att göra det.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Kontrollera funktionsnivån genom att öppna snapin-modulen <strong>Active Directory – användare och datorer</strong>, högerklicka på domännamnet, klicka på <strong>Egenskaper</strong> och sedan bekräfta inställningarna i rutan <strong>Domänläge</strong>. Klicka på <strong>Byt läge</strong> om du vill att domänen ska köras i <strong>Ursprungligt läge</strong> och det inte finns några äldre domänkontrollanter än Windows 2000-domänkontrollanter.
Obs! I Windows Server 2003 har inställningen <strong>Domänläge</strong> ersatts med <strong>Domänens funktionalitet</strong>.</td>
<td style="border:1px solid black;">Du bör inte använda blandade funktionsnivåer för RMS-stöd i Windows 2000 med tanke på säkerheten och hanterbarheten.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Användarkonton</td>
<td style="border:1px solid black;">Skapa ett domänanvändarkonto som används som RMS-tjänstkonto för RMS, t.ex. KontoRMS@konto.se. Ange ett starkt lösenord. Var noga med att ange en e-postadress för användaren. Om e-postadressen inte anges i Active Directory kan användaren inte ta emot licenser och certifikat från RMS.
Obs! RMS-tjänstkontot kan inte vara samma domänkonto som användes vid installationen av RMS.</td>
<td style="border:1px solid black;">Skapa ett separat konto i Active Directory som används av RMS-tjänstkontot. Inkludera en e-postadress. Tilldela inte kontot några specifika behörigheter.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">SQL Server 2000</td>
<td style="border:1px solid black;">Logga in på den server som du ska installera databasen på. Om det är samma server som domänkontrollanten måste du logga in som domänadministratör.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Följ instruktionerna i databasprogramvaran när du installerar databasserverprogrammet.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Följ praxis när du installerar databasservern, till exempel:
<ul>
<li>Ange ett namn för databassystemets administratörskonto och ett organisationsnamn, t.ex. Konto.<br />
<br />
</li>
<li>Ange ett starkt systemadministratörslösenord.<br />
<br />
</li>
<li>Använd integrerade metoder för Windows-autentisering.<br />
<br />
</li>
</ul></td>
<td style="border:1px solid black;">Du bör använda ett integrerat Windows-autentiseringsläge. Om det inte går att köra servern i det läget kontaktar du domänadministratören och databasserver-administratören och kontrollerar vilka ändringar som kan krävas i RMS-installationen.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Kontrollera att databastjänsten inte körs.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Installera programvaruuppdateringar på databasservern. Använd samma lösenord som du angav under installationen när du uppmanas att ange ett lösenord.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Starta om datorn. Kontrollera att databastjänsten startas.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Kontrollera att alla användarkonton har giltiga e-postadressattribut i Active Directory.</td>
<td style="border:1px solid black;"> </td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Kontrollera att den domänanvändare som kommer att administrera RMS (och etablera rotcertifikat- och licensieringsservrarna) har nödvändiga databasserver-behörigheter. Om du använder SQL Server som databasserver kan du lägga till en inloggningsidentifierare för den användare som använder snapin-modulen <strong>SQL Server Enterprise Manager</strong>. Expandera servern och servergruppen i snapin-modulen och expandera sedan objektet <strong>Security</strong>. Klicka på <strong>Logins item</strong>, lägg till en inloggning för användarens domänkonto, klicka på fliken <strong>Server Roles</strong> och markera kryssrutan <strong>Server Administrators</strong>.</td>
<td style="border:1px solid black;">Viktigt! Alla användare och grupper som hämtar licenser och publicerar innehåll med RMS måste ha en konfigurerad e-postadress för sitt konto på fliken <strong>Allmänt</strong> i användarens <strong>Egenskaper</strong>, i MMC-snapin-modulen Active Directory - användare och datorer.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Internetanslutning
(valfritt)</td>
<td style="border:1px solid black;">Kontrollera att webbläsaren och servern (inklusive alla nödvändiga proxyserverkonfigurationer), TCP/IP och LMHOSTS/HOSTS är korrekt konfigurerade för att komma åt Internet. Testa genom att gå till http://uddi.microsoft.com. Om du kan öppna den sidan kan RMS anslutas till Microsofts registreringstjänst.</td>
<td style="border:1px solid black;">Besök http://uddi.microsoft.com och bekräfta att du kommer åt Internet.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Programuppdateringar</td>
<td style="border:1px solid black;">Hämta och installera de senaste uppdateringarna för den programvara som är installerad på datorn (inklusive de senaste Windows-uppdateringarna från www.microsoft.com).</td>
<td style="border:1px solid black;">Hämta och installera alltid de senaste uppdateringarna.</td>
</tr>
</tbody>
</table>
  
När du har utfört alla steg ovan är du redo att påbörja installationen (inklusive installationen av nödvändig programvara) på de datorer där RMS ska köras.
