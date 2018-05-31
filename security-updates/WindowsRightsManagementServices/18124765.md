---
TOCTitle: 'Ta bort webbtjänsten (Inaktivera RMS)'
Title: 'Ta bort webbtjänsten (Inaktivera RMS)'
ms:assetid: '68b4e2b0-b1b7-4b0a-8c1a-82ac27c1f12e'
ms:contentKeyID: 18124765
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747602(v=WS.10)'
---

Ta bort webbtjänsten (Inaktivera RMS)
=====================================

När RMS-servern har inaktiverats och allt RMS-skydd har tagits bort kan du ta bort webbtjänsten genom följande steg:

-   Klicka på **Ta bort RMS från den här webbplatsen** på sidan **Global administration**.

Nästa steg beror på vilken typ av server som ska tas bort, även om RMS alltid tas bort från IIS.

-   Om servern är en del av ett kluster (och inte är den sista servern i klustret) behöver du inte utföra något ytterligare steg.
-   Om servern är en licensieringsserver ska du ta bort katalogtjänstdatabasen men behålla konfigurationen och loggningsdatabasen (de som används av den certifikatserver som fortfarande är i drift).
-   Om servern är den sista RMS-servern i organisationen ska du behålla konfigurationen och loggningsdatabasen, men ta bort anslutningspunkten i Active Directory.
