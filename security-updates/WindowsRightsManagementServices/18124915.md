---
TOCTitle: Utvärdera överflyttningskrav
Title: Utvärdera överflyttningskrav
ms:assetid: 'cec07f45-dc52-4004-860b-5cc33e5fc209'
ms:contentKeyID: 18124915
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747759(v=WS.10)'
---

Utvärdera överflyttningskrav
============================

Organisationer som distribuerar RMS behöver utarbeta en överflyttningsplan där den tid som servern är ur drift minimeras, så att serverunderhåll och uppgraderingar kan genomföras samtidigt som det RMS-skyddade innehållet fortfarande är tillgängligt för användarna. Eftersom tidigare konfigurationer och loggningsdatabaser kan användas med RMS bör en överflyttning av RMS från en server till en annan inte orsaka några problem i en organisation om rätt metoder används. I överflyttningsscenariot förutsätts det att du vill använda befintliga databaser. I annat fall gör du en ny installation av RMS.

Om en HMS (Hardware Security Module), t.ex. nCipher, används i den RMS-server som du ersätter måste du överföra HSM-konfigurationen till den nya servern innan du installerar och etablerar RMS på servern. Instruktioner om hur du gör det finns i dokumentationen som medföljde HSM:en.

Gör följande innan du gör överflyttningen:

-   Kontrollera att databaserna är tillgängliga.
-   Bestäm vilka datorer som ska användas i den nya installationen.

Följ instruktionerna nedan när du flyttar över RMS-installationen:

1.  Säkerhetskopiera alla komponenter innan du startar överflyttningen. Det här omfattar såväl databaser som privata nycklar och systemtillståndet.
2.  Kontrollera att databaserna för den tidigare RMS-installationen finns på den databasserver som kommer att användas för den nya distributionen.
3.  Installera och etablera RMS på de aktuella servrarna och ange var databaserna finns.

En vanlig orsak till migration av en RMS-server är att en RMS-pilotdistribution flyttas till produktionsmiljö. Mer information om det här scenariot finns i ”Migrera en RMS-pilotdistribution till en produktionsdistribution” i ”Distribuera RMS”.
