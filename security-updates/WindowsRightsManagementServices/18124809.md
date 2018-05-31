---
TOCTitle: Krav och checklistor för RMS
Title: Krav och checklistor för RMS
ms:assetid: '836d96ef-d0fd-4935-b595-e8dec19cbb2b'
ms:contentKeyID: 18124809
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747582(v=WS.10)'
---

Krav och checklistor för RMS
============================

Innan du börjar installera RMS ska du läsa igenom teknikkraven för användning av RMS. Varje teknik som listas är mycket viktig för RMS och det är viktigt att ha grundläggande kunskaper om teknikerna för att kunna tillämpa RMS på rätt sätt. Använd gärna följande checklistor till att skapa en egen plan för distribution och administration av RMS:

-   [Tekniska förberedelser](#bkmk_9)
-   [Checklistor för RMS-distribution](#bkmk_10)
-   [Checklistor för RMS-administration](#bkmk_14)

<span id="BKMK_9"></span>
Tekniska förberedelser
----------------------

Den här dokumentationen innehåller information som hjälper dig att förstå hur Windows RMS fungerar, hur du planerar och utför distributionen i organisationen och hur du sköter den dagliga administrationen av systemet. Du bör ha kunskaper inom följande områden:

-   Distribution och administration av Windows Server 2003.
-   Distribution och administration av Active Directory.
-   Distribution och administration av Microsoft® IIS 6.0 (Internet Information Services).
-   Administration av Microsoft® SQL Server™ 2000
-   Grunderna i PKI (Public Key Infrastructure).
-   Servernätverk och serversäkerhet

Mer information finns i ”Ytterligare resurser” i [Använda en RMS-server](http://go.microsoft.com/fwlink/?linkid=42495).

<span id="BKMK_10"></span>
Checklistor för RMS-distribution
--------------------------------

I det här avsnittet finns checklistor för följande distributionsåtgärder:

-   [Distribuera en enskild serverinstallation](#bkmk_11)
-   [Distribuera rotcertifikatkluster och licensieringskluster](#bkmk_12)
-   [Distribuera RMS mellan skogar](#bkmk_13)

Mer information om RMS-distribution finns i[Distribuera ett RMS-system](http://go.microsoft.com/fwlink/?linkid=42494).

<span id="BKMK_11"></span>
Distribuera en enskild serverinstallation
-----------------------------------------

Använd följande checklista när du distribuerar en enskild RMS-server.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Referens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Granska information om koncept och planering.</td>
<td style="border:1px solid black;">”Förbereda RMS-distributioner” i<a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Granska systemkrav och kontrollera att all nödvändig maskin- och programvara är tillgänglig.</td>
<td style="border:1px solid black;">”Infrastrukturella krav för RMS” i <a href="http://go.microsoft.com/fwlink/?linkid=37537">Planera en RMS-distribution</a>.
”Planera databasserver-infrastrukturen” i <a href="http://go.microsoft.com/fwlink/?linkid=37537">Planera en RMS-distribution</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Konfigurera infrastrukturen, exempelvis maskin- och programvarukrav, administrativa konton och funktioner för SMS eller grupprinciper, baserat på aktuella behov.</td>
<td style="border:1px solid black;">”Förbereda RMS-distributioner” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Installera och konfigurera RMS på servern.</td>
<td style="border:1px solid black;">”Konfigurera certifierings- och licensieringstjänsterna på den första servern” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Testa distributionen.</td>
<td style="border:1px solid black;">”Konfigurera en testmiljö” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Implementera RMS i produktionsmiljön.</td>
<td style="border:1px solid black;">”Definiera omfattningen av RMS-implementeringen” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
</tbody>
</table>
  
<span id="BKMK_12"></span>
Distribuera rotcertifikatkluster och licensieringskluster  
---------------------------------------------------------
  
Använd följande checklista när du distribuerar rotcertifikatkluster och licensieringskluster.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Referens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Granska information om koncept och planering.</td>
<td style="border:1px solid black;">”Förbereda RMS-distributioner” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Granska systemkrav och kontrollera att all nödvändig maskin- och programvara är tillgänglig.</td>
<td style="border:1px solid black;">”Infrastrukturella krav för RMS” i <a href="http://go.microsoft.com/fwlink/?linkid=37537">Planera en RMS-distribution</a>.
”Planera databasserver-infrastrukturen” i <a href="http://go.microsoft.com/fwlink/?linkid=37537">Planera en RMS-distribution</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Granska distributionsplanen så att du förstår den topologi och de komponenter som ska installeras.</td>
<td style="border:1px solid black;">”Bestämma RMS-topologin” i <a href="http://go.microsoft.com/fwlink/?linkid=37537">Planera en RMS-distribution</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Konfigurera infrastrukturen, exempelvis maskin- och programvarukrav, administrativa konton och funktioner för SMS eller grupprinciper, baserat på aktuella behov.</td>
<td style="border:1px solid black;">”Förbereda RMS-distributioner” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Installera och konfigurera RMS på servrarna i rotcertifikatklustret.</td>
<td style="border:1px solid black;">”Konfigurera certifierings- och licensieringstjänsterna på den första servern” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.
”Lägga till servrar för hantering av certifiering och licensiering” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Installera och konfigurera RMS på servrarna i licensieringsklustren.</td>
<td style="border:1px solid black;">”Konfigurera certifierings- och licensieringstjänsterna på den första servern” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.
”Lägga till servrar för hantering av certifiering och licensiering” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Konfigurera belastningsutjämning.</td>
<td style="border:1px solid black;">”Utöka den grundläggande infrastrukturen till att hantera kluster” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Testa distributionen.</td>
<td style="border:1px solid black;">”Konfigurera en testmiljö” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Implementera RMS i produktionsmiljön.</td>
<td style="border:1px solid black;">”Definiera omfattningen av RMS-implementeringen” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
</tbody>
</table>
  
<span id="BKMK_13"></span>
Distribuera RMS mellan skogar  
-----------------------------
  
Använd följande checklista när du distribuerar rot-RMS mellan skogar.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Referens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Granska information om koncept och planering.</td>
<td style="border:1px solid black;">”Förbereda RMS-distributioner” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Konfigurera nödvändiga behörigheter baserade på den aktuella förtroendemodellen.</td>
<td style="border:1px solid black;">”Distribuera RMS mellan skogar” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Ange aktuella Active Directory-attribut för skogarna.</td>
<td style="border:1px solid black;">”Distribuera RMS mellan skogar” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>.</td>
</tr>
</tbody>
</table>
  
<span id="BKMK_14"></span>
Checklistor för RMS-administration  
----------------------------------
  
I det här avsnittet finns checklistor för följande administrationsåtgärder:
  
-   [Implementera en principmall för rättigheter](#bkmk_15)  
-   [Distribuera en ny RMS-klient](#bkmk_16)  
-   [Lägga till en betrodd användardomän](#bkmk_17)  
-   [Lägga till en betrodd publiceringsdomän](#bkmk_18)
  
Mer information om hur du hanterar RMS finns i [Använda en RMS-server](http://go.microsoft.com/fwlink/?linkid=42495).
  
<span id="BKMK_15"></span>
Implementera en principmall för rättigheter  
-------------------------------------------
  
Använd följande checklista när du implementerar en principmall för rättigheter.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Referens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Granska relevanta koncept.</td>
<td style="border:1px solid black;">”Principmallar för rättigheter” i <a href="http://go.microsoft.com/fwlink/?linkid=42496">Tekniska referenser för RMS</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Ange platsen för principmallen för rättigheter.</td>
<td style="border:1px solid black;">”Så här anger du platsen för principmallen för rättigheter” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Skapa principmallen för rättigheter.</td>
<td style="border:1px solid black;">”Skapa och ändra principmallar för rättigheter” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.
”Så här lägger du till en principmall för rättigheter” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Distribuera principmallen för rättigheter.</td>
<td style="border:1px solid black;">”Distribuera principmallar för rättigheter” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
</tbody>
</table>
  
<span id="BKMK_16"></span>
Distribuera en ny RMS-klient  
----------------------------
  
Använd följande checklista när du distribuerar en ny version av RMS-klienten.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Referens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Granska relevanta koncept.</td>
<td style="border:1px solid black;">”Planera klientdistribution” i <a href="http://go.microsoft.com/fwlink/?linkid=42494">Distribuera ett RMS-system</a>
”Exkludera lockbox-versioner” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Exkludera tidigare lockbox-versioner om du vill tvinga alla klienter att uppgradera till den senaste klientversionen.</td>
<td style="border:1px solid black;">”Så här exkluderar du lockbox-versioner” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
</tbody>
</table>
  
<span id="BKMK_17"></span>
Lägga till en betrodd användardomän  
-----------------------------------
  
Använd följande checklista när du vill lägga till en betrodd användardomän.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Referens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Granska relevanta koncept.</td>
<td style="border:1px solid black;">”Betrodda användardomäner” i <a href="http://go.microsoft.com/fwlink/?linkid=42496">Tekniska referenser för RMS</a>.
”Lägga till och ta bort betrodda användardomäner” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Hämta serverlicensieringscertifikatet från den användardomän som du vill lägga till. (Detta får du av administratören för den installation som du vill skapa förtroende för.) Lägg sedan till användardomänen i installationen.</td>
<td style="border:1px solid black;">”Så här lägger du till en betrodd användardomän” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
</tbody>
</table>
  
<span id="BKMK_18"></span>
Lägga till en betrodd publiceringsdomän  
---------------------------------------
  
Använd följande checklista när du vill lägga till en betrodd publiceringsdomän.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Steg</th>
<th style="border:1px solid black;" >Referens</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Granska relevanta koncept.</td>
<td style="border:1px solid black;">”Betrodda publiceringsdomäner” i <a href="http://go.microsoft.com/fwlink/?linkid=42496">Tekniska referenser för RMS</a>.
”Lägga till och ta bort betrodda publiceringsdomäner” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Hämta det krypterade serverlicensieringscertifikatet och den privata nyckeln för den publiceringsdomän som du vill lägga till. Lägg sedan till publiceringsdomänen i installationen.</td>
<td style="border:1px solid black;">”Så här lägger du till en betrodd publiceringsdomän” i <a href="http://go.microsoft.com/fwlink/?linkid=42495">Använda en RMS-server</a>.</td>
</tr>
</tbody>
</table>
