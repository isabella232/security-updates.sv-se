---
TOCTitle: 'Åsidosätta identifiering av Active Directory-tjänster'
Title: 'Åsidosätta identifiering av Active Directory-tjänster'
ms:assetid: '9d97e7fb-5b05-4853-ad7b-6cc82b9729f0'
ms:contentKeyID: 18124835
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747614(v=WS.10)'
---

Åsidosätta identifiering av Active Directory-tjänster
=====================================================

RMS-tjänster och RMS-klienter hittar tjänster genom att först söka i det lokala registret. Om vissa nycklar i registret saknar värde söker RMS-tjänster och RMS-klienter efter anslutningspunkten i Active Directory. Det innebär att du kan åsidosätta standardinställningen för identifiering i Active Directory genom att ange vissa nycklar i serverregistret eller klientregistret.

| ![](images/Cc747614.note(WS.10).gif)Obs!                                                                                                        |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om RMS-rotklustret har konfigurerats så att anslutningspunkten inte publiceras i Active Directory kan du leda RMS-klienterna till rätt tjänst med hjälp av de här nycklarna. |

I det här avsnittet beskrivs registerposterna och hur du skapar dem.

Åsidosätta tjänstidentifiering för underregistrering av licenskluster
---------------------------------------------------------------------

Om du etablerar ett licenskluster och vill att det ska underregistreras med ett annat rotkluster än det som du har distribuerat i licensklustrets Active Directory-skog måste du åsidosätta identifieringen av såväl underregistreringstjänsten som kontocertifieringstjänsten.

#### Beskrivning av registerposter

Följande registerposter används för att åsidosätta underregistreringstjänsten och kontocertifieringstjänsten.

-   **SubEnrollmentURL**. Den här posten anger sökvägen till det rotkluster som licensieringsservern använder vid begäran om serverlicensieringscertifikat.
-   **GicURL**. Den här posten anger sökvägen till kontocertifieringstjänsten för licensklustret.

#### Information om posten

Här följer den fullständiga sökvägen till registerundernyckeln för tjänstidentifieringsposter vid underregistrering av licenskluster på datorer som kör en 32-bitarsversion av Windows Server 2003:

**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\DRMS\\1.0**

Här följer den fullständiga sökvägen till registerundernyckeln för tjänstidentifieringsposter vid underregistrering av licenskluster på datorer som kör en 64-bitarsversion av Windows Server 2003:

**HKEY\_LOCAL\_MACHINE\\SoftwareWOW6432Node\\Microsoft\\DRMS\\1.0**

I följande tabell listas de poster som du kan lägga till för att åsidosätta tjänstidentifiering.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Typ</th>
<th style="border:1px solid black;" >Värde</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">SubEnrollmentURL</td>
<td style="border:1px solid black;">Sträng</td>
<td style="border:1px solid black;">http(eller https)://<em>servernamn</em>/_wmcs/certification/subenrollservice.asmx</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">GicURL</td>
<td style="border:1px solid black;">Sträng</td>
<td style="border:1px solid black;">http(eller https)://<em>servernamn</em>/_wmcs/certification/certification.asmx</td>
</tr>
</tbody>
</table>
  
Åsidosätta tjänstidentifiering hos klienter för publicering  
-----------------------------------------------------------
  
Om användarna ska publicera innehåll från sina datorer kan det vara bra att åsidosätta servrar som används vid publicering, beroende på vilken topologi som används inom företaget. De servrar som används vid publicering hittar du vanligen med hjälp av Active Directory. Genom att lägga till lämpliga registernycklar på klientdatorerna kan du få klienterna att åsidosätta metoderna och i stället använda de URL:er som du har angett i registerpostens värde.
  
| ![](images/Cc747614.note(WS.10).gif)Obs!                                                                                                                 |  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| De klientåsidosättanden som beskrivs i det här avsnittet bör skapas som nycklar och inte som separata poster. Värdet för nycklarna bör skapas i standardposten för respektive nyckel. |
  
#### Beskrivning av registernycklar
  
Följande registernycklar kan användas för att åsidosätta automatisk identifiering av RMS-klustret.
  
-   **Activation**. Den här registernyckeln anger URL:en till datoraktiveringstjänsten. Den här registerposten används inte när du kör RMS-klienten med Service Pack 1 eller senare.  
-   **EnterprisePublishing**. Den här registernyckeln anger URL:en till den RMS-installation som du vill att klienten ska använda vid licensbegäran.  
-   **CloudPublishing**. Den här registernyckeln anger URL:en till den Microsoft-licensieringstjänst som kan användas om klienten inte har tillgång till någon RMS-installation men har tillgång till Internet.
  
#### Information om nycklar
  
Här följer den fullständiga sökvägen till registerundernyckeln för tjänstidentifieringsposter på klientsidan vid publicering:
  
**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\MSDRM\\ServiceLocation\\**
  
I följande tabell visas registernycklar som du kan lägga till i en RMS-klientdator för att åsidosätta tjänstidentifiering.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Namn</th>
<th style="border:1px solid black;" >Typ</th>
<th style="border:1px solid black;" >Värde</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Aktivering</td>
<td style="border:1px solid black;">Sträng</td>
<td style="border:1px solid black;">http(eller https)://<em>RMS_klusternamn</em>/_wmcs/Certification där <em>RMS_klusternamn</em> är namnet på RMS-klustret.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">EnterprisePublishing</td>
<td style="border:1px solid black;">Sträng</td>
<td style="border:1px solid black;">http(eller https)://<em>RMS_klusternamn</em>/_wmcs/Licensing där <em>RMS_klusternamn</em> är namnet på RMS-klustret.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">CloudPublishing</td>
<td style="border:1px solid black;">Sträng</td>
<td style="border:1px solid black;">http(eller https)://<em>FQDN_klusternamn</em>/_wmcs/Licensing där <em>FQDN_klusternamn</em> är det fullständigt kvalificerade domännamnet på RMS-klustret.</td>
</tr>
</tbody>
</table>
  
Du rekommenderas att implementera de här registernycklarna med hjälp av antingen Systems Management Server eller en grupprincip för att vara säker på att alla klienter inom företaget använder rätt publiceringsservrar.
  
| ![](images/Cc747614.Caution(WS.10).gif)Varning!                                                                        |  
|-----------------------------------------------------------------------------------------------------------------------------------------------------|  
| Om du redigerar registret på fel sätt kan systemet skadas. Du bör alltid säkerhetskopiera viktig information på datorn innan du ändrar i registret. |
  
En exempelregisterfil (.reg) kan användas för att importera rätt registernycklar på respektive server i RMS-klustret.
  
**Så här importerar du rätt registernycklar till respektive server i RMS-klustret**  
1.  Kopiera följande exempelregisterfil till Anteckningar.
  
    `Windows Registry Editor Version 5.00`
  
    `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation]`
  
    `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation]`
  
    `@="http://<RMS_cluster_name>/_wmcs/certification"`
  
    `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing]`
  
    `@="http://<RMS_cluster_name>/_wmcs/licensing"`
  
2.  Ersätt &lt;RMS\_klusternamn&gt; med namnet på ditt RMS-kluster.
  
3.  Spara filen med filnamnstillägget .reg.
  
4.  Dubbelklicka på filnamnet i Windows Explorer.
  
5.  Om dialogrutan **Användarkontokontroll** öppnas bekräftar du att du vill utföra den åtgärd som visas och klickar sedan på **Fortsätt**.. När du får frågan om du vill lägga till informationen i registret klickar du på **Ja**.
