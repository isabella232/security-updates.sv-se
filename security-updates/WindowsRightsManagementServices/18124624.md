---
TOCTitle: 'Granska RMS-designer'
Title: 'Granska RMS-designer'
ms:assetid: '0ed1dd67-8e07-47c9-9e2e-0104438bd19f'
ms:contentKeyID: 18124624
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720185(v=WS.10)'
---

Granska RMS-designer
====================

Innan du påbörjar en distribution bör du kontrollera att du gått igenom följande punkter i din RMS-plan:

-   Du har valt ett RMS-aktiverat klientprogram och har en färdig plan för implementeringen.
-   Du har valt metod för distribution av RMS-klienten.
-   Det finns en installerad och tillgänglig databasserver.
-   Du har valt RMS-topologi, antingen grundläggande eller distribuerad.
-   Active Directory är installerat på domänkontrollanter med Windows 2000 med Service Pack 3 (SP3) eller senare, och alla användare har kontaktobjekt med konfigurerade e-postattribut. Windows Server 2003 är installerat med de senaste uppdateringarna. Message Queuing, Internet Information Services och ASP.NET version 1.1 är aktiverade.

| ![](images/Cc720185.note(WS.10).gif)Obs!                                                                                                                                         |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du ska installera RMS på en 64-bitarsdator bör du läsa avsnittet ”Programvarukrav för RMS” i ”Planera en RMS-distribution” i den här dokumentationen. Där finns särskilda instruktioner för konfiguration. |

-   Metoder för belastningsutjämning och växling vid serverfel har definierats.
-   DNS-registreringen är konfigurerad för RMS-servrarna.
-   Planer för säkerhetskopiering och återställning finns.
-   Du har gjort de säkerhetsöverväganden som krävs för din organisation.
