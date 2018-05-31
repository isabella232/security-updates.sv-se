---
TOCTitle: Konfigurera SMS eller grupprinciper för klientdistribution
Title: Konfigurera SMS eller grupprinciper för klientdistribution
ms:assetid: '9e37c27b-8cc1-40c6-adb7-0937aa64c8db'
ms:contentKeyID: 18124848
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747703(v=WS.10)'
---

Konfigurera SMS eller grupprinciper för klientdistribution
==========================================================

När du distribuerar RMS måste en RMS-aktiverad programvara installeras på användarnas datorer för att användare ska kunna skydda innehåll och använda RMS-skyddat innehåll.

Om ett program ska kunna RMS-aktiveras måste det integrera RMS-klienten. Före Windows Vista® fanns RMS-klienten som separat Windows-komponent och går att hämta på Microsoft Download Center. Men om du vill hämta klienten separat till varje klientdator i företaget kan du använda Microsoft SMS (Systems Management Server), grupprinciper eller skript för att automatisera leveransen av RMS-klienter till klientdatorerna.

| ![](images/Cc747703.Important(WS.10).gif)Viktigt!                 |
|------------------------------------------------------------------------------------------------|
| RMS-klienten är integrerad i Windows Vista. Därför behövs inte längre en separat installation. |

Gör så här när du distribuerar RMS-klienten med hjälp av SMS:

-   Skapa en ny PDF (Package Definition File).
-   Extrahera Windows Installer-filerna från filen WindowsRightsManagementServicesSP2-KB917275-Client-ENU.exe. Spara först filen WindowsRightsManagementServicesSP2-KB917275-Client-ENU.exe. Installera den inte. I det här exemplet kan vi anta att filen sparats i c:\\mappnamn. Öppna kommandotolken och skriv följande kommando:
    `c:\folder_name\WindowsRightsManagementServicesSP2-KB917275-Client-ENU.exe /x/t:c:\folder_name`
    Då extraheras filerna MSDrmClient.msi och RMClientBackCompat.msi från .exe-filen till mappen *c:\\mappnamn*.
-   Använd Windows Installer-filerna till paketdefinition och källa.
-   Meddela nätverksanvändarna var paketen finns.

| ![](images/Cc747703.note(WS.10).gif)Obs!                                                                                                     |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Administratörsrättigheter krävs för att installera programvara. Organisationens säkerhetsprincip kan kräva att en systemadministratör installerar RMS-klientprogramvaran. |

Mer information om att använda SMS till att distribuera programvara finns i Systems Management Server 2003 Concepts, Planning, and Deployment Guide ([http://go.microsoft.com/fwlink/?LinkID=17401](http://go.microsoft.com/fwlink/?linkid=17401)).

Mer information om distribution av klientprogramvara med hjälp av grupprinciper finns i avsnitten om gruppolicybaserad distribution av program ([http://go.microsoft.com/fwlink/?LinkID=38997](http://go.microsoft.com/fwlink/?linkid=38997)).
