---
TOCTitle: 'Uppdatera distributionen med RMS Service Pack 1 (SP1)'
Title: 'Uppdatera distributionen med RMS Service Pack 1 (SP1)'
ms:assetid: 'a562c4b0-15df-46db-9d61-24db74871cfa'
ms:contentKeyID: 18124856
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747714(v=WS.10)'
---

Uppdatera distributionen med RMS Service Pack 1 (SP1)
=====================================================

I det här avsnittet finns information om hur du installerar Microsoft® Windows® Rights Management Services (RMS) Service Pack 1 (SP1) i en organisation som redan tillämpar RMS-distribution. Det är endast organisationer som redan tillämpar RMS som behöver uppdatera till RMS SP1. Organisationer som tillämpar RMS för första gången kan distribuera RMS med SP1 genom att följa instruktionerna för planering av RMS-distribution och distribution av RMS-system i den här dokumentsamlingen.

Du kan installera RMS SP1 utan att först ta bort den nuvarande RMS-installationen. Installationsprogrammet för RMS SP1 känner av att RMS är installerat och lägger därefter till de funktioner och inställningar som krävs.

**Inom samma ämne**

-   [Förbereda för uppdatering till RMS SP1](#bkmk_1)
-   [Uppdatera till RMS SP1](#bkmk_2)
-   [Uppdatera kluster](#bkmk_3)
-   [Uppdatera RMS-klienter](#bkmk_4)
-   [Samverkan med RMS version 1.0](#bkmk_5)
-   [Ta bort RMS med SP1](#bkmk_6)

<span id="BKMK_1"></span>
Förbereda för uppdatering till RMS SP1
--------------------------------------

Uppdateringen till RMS SP1 är till för att du ska kunna fortsätta tillämpa RMS utan avbrott. Innan du uppgraderar ett RMS-servrar bör du dock göra följande:

-   Säkerhetskopiera konfigurationsdatabasen och den privata RMS-nyckeln. Mer information finns i avsnittet om säkerhetskopiering av RMS-system i instruktionerna för planering av RMS-distribution i den här dokumentsamlingen.
-   Se till att ha lösenordet till den privata RMS-nyckeln till hands.
-   Säkerhetskopiera loggningsdatabasen om du vill behålla statistik som loggats tidigare.
-   Kontrollera att du har installerat de senaste kritiska uppdateringarna och säkerhetsuppdateringarna för operativsystemet på klientdatorer och servrar. Det kontrollerar du genom att klicka på **Start**, klicka på **Windows Update** och sedan följa instruktionerna på skärmen.

<span id="BKMK_2"></span>
Uppdatera till RMS SP1
----------------------

Installationsguiden för RMS SP1 kontrollerar den befintliga RMS-installationen och sedan är det endast nya filer som läggs till och filer som behöver ersättas byts ut vid installation av RMS SP1. Om du redan använder RMS utan problem behöver du inte etablera om eller utföra någon extra konfiguration för att kunna fortsätta använda RMS efter att du har installerat RMS SP1 .

<span id="BKMK_3"></span>
Uppdatera kluster
-----------------

Om du har installerat RMS i en klusterkonfiguration bör du planera uppdateringen av klustren för att på så sätt minska effekten av uppdateringen. Tänk på följande när du bestämmer hur du vill implementera RMS SP1 i organisationen:

-   Det bästa är att installera RMS SP1 på en del av klustret i taget. På så sätt har du större kontroll över klusteruppgraderingen och risken för degradering minskar.
-   Om du har flera RMS-kluster bör du uppgradera rotcertifikatklustren först och sedan uppgradera underregistrerade licensieringskluster.
-   Om du tillämpar gruppexpandering mellan skogar kan du uppgradera klustren i skogarna oberoende av varandra utan att det påverkar RMS-serverns förmåga att expandera gruppmedlemskap mellan skogar.
-   RMS SP1 kan samexistera och samverka med RMS version 1.0.
-   Installationspaketet för RMS SP1 kan även användas för att installera en ny version av RMS SP1 på en server. RMS version 1.0 behöver inte vara installerat.

<span id="BKMK_4"></span>
Uppdatera RMS-klienter
----------------------

En ny RMS-klient medföljer RMS med SP1. Klientinstallationspaketet för RMS SP1 kan även användas för att installera en ny version av RMS SP1-klienten på en dator. För detta krävs inte att en klient med RMS version 1.0 är installerad. Klienter med RMS SP1 är bakåtkompatibla så att de kan användas med RMS-aktiverade program som kräver RMS version 1.0.

Den nya RMS-klienten omfattar följande funktioner:

-   Du behöver inte ansluta klienten till Microsoft via Internet och hämta en lockbox.
-   Om du installerar RMS-klienten med hjälp av SMS eller en grupprincip krävs inga administratörsrättigheter.
-   RMS SP1-klienten innehåller en ny server-lockbox (en typ av säkerhetsprocessor för server) som kan användas till att RMS-aktivera webbtjänster eller program på serversidan, som Windows SharePoint® Services och Exchange Server 2003, så att du kan använda och omdistribuera RMS-skyddat innehåll via tjänsten. Denna lockbox har höga prestanda och är skalbar vid användning i betrodda serverprogram
-   RMS-klienten använder FIPS 140-2-certifierade kryptografiska algoritmer. Det innebär att klienten kan distribueras i FIPS-kompatibla organisationer.

<span id="BKMK_5"></span>
Samverkan med RMS version 1.0
-----------------------------

Eftersom RMS SP1 innehåller flera prestandaförbättringar bör du installera det när du är klar med testningen. Trots att RMS-servrar och RMS-klienter som körs med RMS SP1 är helt kompatibla med servrar och klienter som inte kör RMS SP1 bör du vara medveten om följande skillnader i hur de fungerar i en blandad miljö:

-   Offlineregistrering kan endast tillämpas med servrar som körs med RMS SP1.
-   Det är endast klienter som körs med RMS SP1 som är självaktiverande.
-   I följande tabell anges vilka funktioner som kan användas i blandade miljöer:

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
<th style="border:1px solid black;" >RMS-serverversion</th>
<th style="border:1px solid black;" >Funktioner som kan användas med v1-klienter</th>
<th style="border:1px solid black;" >Funktioner som kan användas med SP1-klienter</th>
<th style="border:1px solid black;" >Funktioner som kan användas i blandade klientmiljöer (v1 och SP1)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">1.0</td>
<td style="border:1px solid black;">Alla tidigare funktioner.
Ingen offlineregistrering av server. Servern måste registreras via Internet.
Inga självaktiverande klienter.</td>
<td style="border:1px solid black;">Alla tidigare funktioner.
Ingen offlineregistrering av server.
Självaktiverande klienter.</td>
<td style="border:1px solid black;">Alla tidigare funktioner.
SP1-klienter är självaktiverande.
Version 1-klienter måste aktiveras via Internet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">SP1</td>
<td style="border:1px solid black;">Alla tidigare funktioner.
Offlineregistrering av server.
Inga självaktiverande klienter.</td>
<td style="border:1px solid black;">Samtliga SP1-funktioner.
Offlineregistrering av server.
Självaktiverande klienter.
Server-lockbox.</td>
<td style="border:1px solid black;">Alla tidigare funktioner samt SP1-funktioner.
Offlineregistrering av server.
SP1-klienter är självaktiverande.
Version 1-klienter måste aktiveras via Internet.</td>
</tr>
</tbody>
</table>
 

<span id="BKMK_6"></span>
Ta bort RMS med SP1
-------------------

Om du vill återställa RMS-serverns gamla konfiguration efter att du har installerat RMS SP1 kan du ta bort RMS SP1 via **Lägg till eller ta bort program** på **Kontrollpanelen**.

**Obs!**   Om du säkerhetskopierade konfigurationsdatabasen innan du installerade RMS SP1 kan du använda säkerhetskopian för att helt ta bort alla ändringar som infördes med RMS SP1. Om du inte säkerhetskopierade konfigurationsdatabasen kan du eventuellt använda konfigurationsdatabasen från RMS SP1-installationen med den återställda RMS-versionen. I det återställda RMS-versionen ignoreras de extrafält som infogades i konfigurationsdatabasen vid installationen av RMS SP1, eftersom de inte används.
