---
TOCTitle: 'RMS-serverinstallation via kommandotolken'
Title: 'RMS-serverinstallation via kommandotolken'
ms:assetid: 'b55b1e2a-dd14-4168-a37f-9cdedbec660b'
ms:contentKeyID: 18124871
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747733(v=WS.10)'
---

RMS-serverinstallation via kommandotolken
=========================================

Du kan installera RMS med Service Pack 2 (SP2) från kommandotolken, vilket gör det möjligt att automatisera installationen. Installationen kan automatiseras på två sätt: Du kan göra en obevakad installation med hjälp av EXE-klienten som du hämtar eller med de extraherade MSI-filerna från EXE för att installera RMS-klienten. Om du installerar med hjälp av den hämtade EXE-filen använder du följande syntax:

**WindowsRightsManagementServicesSP2-KB917275-Client-ENU.exe -override 1 /I MsDrmClient.msi REBOOT=ReallySuppress /q -override 2 /I RmClientBackCompat.msi REBOOT=ReallySuppress /q**

Om du installerar med hjälp av Windows® Installer (.msi)-filerna måste du först extrahera msi-filerna från den körbara filen för RMS med SP 2. Följande kommando kan köras från kommandotolken för att extrahera filerna msdrmclient.msi och RmClientBackCompat.msi:

**WindowsRightsManagementServiceSP2-KB917275-Server-ENU.exe /X:C:\\***Install\_Location*

När du har extraherat .msi-filerna kan du använda följande kommando till att installera RMS:

**msiexec.exe /I MSDrmClient.msi /qn ALLUSERS=2 /m MSIDHOG /lei logfile.log DISPLYPAGE="NO" TARGETDIR=c:\\***Install\_Location*

**msiexec.exe /I RMClientBackCompat.msi /qn ALLUSERS=2 /m MSIDHOG /lei logfile.log DISPLYPAGE="NO" TARGETDIR=c:\\***Install\_Location*

I följande tabell beskrivs syntaxen för varje kommando.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Parameter</th>
<th style="border:1px solid black;" >Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;"><strong>/I MSDrmClient.msi</strong> eller <strong>/I RMClientBackCompat.msi</strong></td>
<td style="border:1px solid black;">Obligatorisk. Anger vilken produkt som ska installeras.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/qn</strong></td>
<td style="border:1px solid black;">Valfri. Anger en tyst installation utan interaktion från användaren.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/lei</strong> <em>logfile.log</em></td>
<td style="border:1px solid black;">Valfri. Anger i vilken fil fel och statusmeddelanden ska sparas.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>DISPLAYPAGE=”NO”</strong></td>
<td style="border:1px solid black;">Valfri. Anger att sidan <strong>Global administration</strong> inte ska visas efter installationen.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>TARGETDIR=c:\</strong><em>Install_Location</em></td>
<td style="border:1px solid black;">Valfri. Ange i vilken katalog RMS med Service Pack 2 installeras. Standardplatsen för installation används om du inte anger någon annan plats.</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc747733.note(WS.10).gif)Obs!                                                                                                                                                          |  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Vilken installationsmetod du än väljer att använda ska du se till att båda .msi-filerna installeras utan fel. Om ett fel uppstår som förhindrar installationen av MSDrmClient.msi ska RMClientBackCompat.msi inte installeras. |
