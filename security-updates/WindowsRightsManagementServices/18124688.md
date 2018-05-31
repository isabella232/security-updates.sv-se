---
TOCTitle: 'Uppdatera distributionen med RMS Service Pack 2 (SP2)'
Title: 'Uppdatera distributionen med RMS Service Pack 2 (SP2)'
ms:assetid: '27ee06a1-f467-4a6c-b662-45ddb5f8c13e'
ms:contentKeyID: 18124688
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720225(v=WS.10)'
---

Uppdatera distributionen med RMS Service Pack 2 (SP2)
=====================================================

I det här avsnittet finns information om hur du installerar Microsoft® Windows® Rights Management Services (RMS) med Service Pack 2 (SP2) i en organisation som redan tillämpar RMS-distribution. Det är endast organisationer som redan tillämpar RMS som behöver uppdatera till RMS med SP2. Organisationer som tillämpar RMS för första gången kan distribuera RMS med SP2 genom att följa instruktionerna för planering av RMS-distribution ([http://go.microsoft.com/fwlink/?LinkId=74999](http://go.microsoft.com/fwlink/?linkid=74999)) och distribution av RMS-system ([http://go.microsoft.com/fwlink/?LinkID=75000](http://go.microsoft.com/fwlink/?linkid=75000)) i den här dokumentsamlingen.

Du kan installera RMS med SP2 utan att först ta bort RMS med SP1. Installationsprogrammet för RMS med SP2 känner av att RMS med SP1 är installerat och lägger därefter till de funktioner och inställningar som krävs.

| ![](images/Cc720225.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Det går inte att upprätta en uppgraderingssökväg från en RMS-server utan Service Pack till RMS med SP2. Om du använder en RMS-server utan Service Pack måste du uppgradera till RMS med SP1 innan du kan uppgradera till RMS med SP2. RMS-klienten kan uppgraderas från vilken tidigare version av RMS-klienten som helst. |

**Inom samma ämne**

-   [Förbereda för uppdatering till RMS med SP2](#bkmk_preparingforsp2update)
-   [Uppdatera till RMS med SP2](#bkmk_performingsp2update)
-   [Uppdatera kluster](#bkmk_updateclusters)
-   [Uppdatera RMS-klienter](#bkmk_updateclients)
-   [Samverkan med RMS version 1.0](#bkmk_interop)
-   [Ta bort RMS med SP2](#bkmk_removingrms)

<span id="bkmk_PreparingForSP2Update"></span>
Förbereda för uppdatering till RMS med SP2
------------------------------------------

Uppdateringen till RMS med SP2 är till för att du ska kunna fortsätta tillämpa RMS utan avbrott. Innan du uppgraderar ett RMS-kluster bör du dock göra följande:

-   Säkerhetskopiera konfigurationsdatabasen och den privata RMS-nyckeln. Mer information finns i avsnittet om säkerhetskopiering av RMS-system ([http://go.microsoft.com/fwlink/?LinkId=75001](http://go.microsoft.com/fwlink/?linkid=75001)) i den här dokumentsamlingen.
-   Om du använder en programbaserad privat nyckel bör du ha lösenordet till den privata RMS-nyckeln till hands.
-   Säkerhetskopiera loggningsdatabasen om du vill behålla statistik som loggats tidigare.
-   Kontrollera att du har installerat de senaste kritiska uppdateringarna och säkerhetsuppdateringarna för operativsystemet på klientdatorer och servrar. Det kontrollerar du genom att klicka på **Start**, klicka på **Windows Update** och sedan följa instruktionerna på skärmen.

<span id="bkmk_PerformingSP2Update"></span>
Uppdatera till RMS med SP2
--------------------------

När installationsguiden för Windows Rights Management Services med Service Pack 2 känner av RMS-installationen kontrolleras den existerande installationen av RMS med SP1. Nya filer läggs sedan till och filer som behöver ersättas byts ut vid installation av RMS med SP2. Om du redan använder RMS utan problem behöver du inte etablera om eller utföra någon extra konfiguration för att kunna fortsätta använda RMS efter att du har installerat RMS med SP2.

<span id="bkmk_UpdateClusters"></span>
Uppdatera kluster
-----------------

Om du har installerat RMS i en klusterkonfiguration bör du planera uppdateringen av klustren för att på så sätt minska effekten av uppdateringen. Tänk på följande när du bestämmer hur du vill implementera RMS med SP2 i organisationen:

-   Det bästa är att installera RMS med SP2 på en del av klustret i taget. På så sätt har du större kontroll över klusteruppgraderingen och risken för degradering minskar.
-   Om du har flera RMS-kluster bör du uppgradera rotcertifikatklustren först och sedan uppgradera underregistrerade licensieringskluster.
-   Om du tillämpar gruppexpandering mellan skogar kan du uppgradera klustren i skogarna oberoende av varandra utan att det påverkar RMS-serverns förmåga att expandera gruppmedlemskap mellan skogar.
-   Servrar med RMS med SP2, RMS med SP1 och RMS version 1.0 kan endast samexistera och samverka om de fins i olika Active Directory-skogar. Du bör inte ha olika versioner av RMS-servrar i ett och samma kluster.
-   Installationspaketet för RMS med SP2 kan även användas för att installera en ny version av RMS med SP2 på en server. RMS med SP1 behöver inte vara installerat.

<span id="bkmk_UpdateClients"></span>
Uppdatera RMS-klienter
----------------------

Du kan hämta en ny RMS-klient med SP2 antingen från Windows Update eller på Microsoft Download Center. Klientinstallationspaketet för RMS med SP2 kan även användas för att installera en ny version av RMS SP2-klienten på en dator. För detta krävs inte att en klient med RMS version 1.0 är installerad. Klienter med RMS med SP2 är bakåtkompatibla så att de kan användas med RMS-aktiverade program som kräver RMS version 1.0.

Mer information om hur du uppdaterar och installerar RMS-klienten finns i avsnittet om distribution av RMS-klienten ([http://go.microsoft.com/fwlink/?LinkId=75070](http://go.microsoft.com/fwlink/?linkid=75070)).

<span id="bkmk_InterOp"></span>
Samverkan med RMS version 1.0
-----------------------------

Eftersom RMS med SP2 innehåller flera prestandaförbättringar bör du installera det vid nästa uppgraderingscykel. Trots att RMS-servrar och RMS-klienter som körs med RMS med SP2 är helt kompatibla med servrar och klienter som inte kör RMS med SP2 bör du vara medveten om följande skillnader i hur de fungerar i en blandad miljö:

-   Offlineregistrering kan endast tillämpas med servrar som körs med RMS med SP1 eller senare.
-   Det är endast klienter som körs med RMS med SP1 eller senare som är självaktiverande.
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
<th style="border:1px solid black;" >Funktioner som kan användas med version 1-klienter</th>
<th style="border:1px solid black;" >Funktioner som kan användas med SP2-klienter</th>
<th style="border:1px solid black;" >Funktioner som kan användas i blandade klientmiljöer</th>
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
SP2-klienter är självaktiverande.
Version 1-klienter måste aktiveras via Internet.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">SP2</td>
<td style="border:1px solid black;">Alla tidigare funktioner.
Offlineregistrering av server.
Inga självaktiverande klienter.</td>
<td style="border:1px solid black;">Samtliga SP1-funktioner.
Offlineregistrering av server.
Självaktiverande klienter.
Server-lockbox.
Microsoft SQL Server™ 2005 kan börja användas direkt.</td>
<td style="border:1px solid black;">Alla tidigare funktioner samt SP2-funktioner.
Offlineregistrering av server.
SP2-klienter är självaktiverande.
Version 1-klienter måste aktiveras via Internet.</td>
</tr>
</tbody>
</table>
 

<span id="bkmk_RemovingRMS"></span>
Ta bort RMS med SP2
-------------------

Om du vill återställa RMS-serverns gamla konfiguration efter att du har installerat RMS med SP2 kan du ta bort RMS med SP2 via **Lägg till eller ta bort program** på **Kontrollpanelen**.
