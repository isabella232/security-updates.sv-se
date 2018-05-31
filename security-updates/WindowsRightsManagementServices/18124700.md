---
TOCTitle: Planera distribution mellan skogar
Title: Planera distribution mellan skogar
ms:assetid: '2dfb40b7-95b1-4362-b32e-72867544b705'
ms:contentKeyID: 18124700
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720233(v=WS.10)'
---

Planera distribution mellan skogar
==================================

Om du distribuerar RMS i en miljö med flera skogar måste du bestämma vilka funktioner som behövs för användare och grupper som inte tillhör den skog där RMS är distribuerat. Problemet är att användar- och gruppobjekt från andra skogar normalt inte innehåller objekt som är representativa i den skog där RMS är etablerat. Om du tänker begränsa behörigheter för användare och grupper i andra skogar med RMS måste du konfigurera skogen för det och tillåta gruppexpandering mellan skogar.

Det finns två sätt att implementera funktioner för gruppexpandering mellan skogar i RMS:

-   Distribuera RMS i den skog där grupperna definieras och där det ska användas för expandering av medlemskapen i de grupperna.
-   Synkronisera gruppdefinitioner mellan skogar och tillåt att den lokala RMS-installationen helt bestämmer gruppmedlemskap för alla användare. Om användaren som begär en användarlicens har ett Windows-konto i en annan skog måste det även finnas ett kontaktobjekt i den lokala skogen som representerar användarens gruppmedlemskap. Du kan använda metakataloger, t.ex. Microsoft® Identity Integration Server (MIIS) 2003 eller Identity Integration Feature Pack (IIFP) till att implementera komplett synkronisering av gruppobjekt mellan skogar.

Om du planerar att bara använda RMS i en skog kan du optimera processen att utfärda användarlicenser genom att modifiera klusterprincipen **MaxCrossForestCalls** i RMS-konfigurationsdatabasen. Den här principen anger hur många gånger ett gruppmedlemskap kan korsa skogsgränser. Standardvärdet är 10. Om du vill ändra det värdet till 0 använder du följande SQL-kommando:

`update DRMS_ClusterPolicies set PolicyData=0 där PolicyName='MaxCrossForestCalls'`
