---
TOCTitle: Principmallar för rättigheter
Title: Principmallar för rättigheter
ms:assetid: 'eee931c8-7c98-48e9-9e2c-d0b7bd4f2b96'
ms:contentKeyID: 18124976
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747732(v=WS.10)'
---

Principmallar för rättigheter
=============================

I en principmall för rättigheter beskrivs en standarduppsättning med användare, rättigheter och villkor som kan tillämpas på RMS-skyddat innehåll. När en användare tillämpar en principmall för rättigheter på innehåll blir de rättigheter som anges i mallen en del av publiceringslicensen.

På webbplatsen Administration av RMS kan du skapa principmallar för rättigheter samt ta bort eller ändra befintliga mallar. Principmallar för rättigheter kan innehålla olika villkor, t.ex. särskilda mottagare eller Active Directory-grupper, hur länge en användarlicens för innehållet ska vara giltig, hur länge efter publiceringen innehållet kan användas samt särskilda villkor som har betydelse för ett visst RMS-aktiverat program. En lista över återkallade certifikat kan krävas för en mall. I mallen anges listfilens URL och antalet dagar som listan är giltig. När en mottagare begär en användarlicens som baseras på mallen kontrolleras listan över återkallade certifikat innan användaren kan använda det RMS-skyddade innehållet. Mer information finns i ”[Återkalla RMS](https://technet.microsoft.com/72689f90-f3c5-4b61-94ea-d825f3199b3b)” senare i det här avsnittet.

Nedan följer några exempel på rättigheter som kan fastställas i principmallar:

-   Vem som helst får läsa innehållet men endast den användare som skapat innehållet får ändra det.
-   Vem som helst inom företaget får läsa innehållet men endast i en månad efter publiceringen.
-   Vem som helst inom företaget får läsa innehållet men inga externa medarbetare eller kunder får läsa det.
-   Endast angivna mottagare får läsa innehållet.
-   Endast en angiven mottagare får läsa eller ändra innehållet.

Mallar kan innehålla olika villkor, t.ex:

-   Särskilda mottagare eller Active Directory-grupper som har rättigheter att använda innehållet.
-   Hur länge en användarlicens för innehållet ska vara giltig.
-   Hur länge efter publiceringen innehållet kan användas.
-   Om användarlicensen kräver en lista över återkallade certifikat och hur ofta listan behöver uppdateras.
-   Särskilda villkor som har betydelse för ett visst RMS-aktiverat program.

Principmallar för rättigheter sparas både i konfigurationsdatabasen och i en delad mapp. RMS-administratören ansvarar för att distribuera principmallar för rättigheter från den delade mappen till klientdatorerna så att användarna kan använda dem. Mer information finns i ”Distribuera principmallar för rättigheter” i ”Använda en RMS-server”.

I ett RMS-aktiverat program kan en användare välja en principmall att tillämpa på det innehåll han eller hon skapat. Normalt anger mallen en grupp vars medlemmar får använda innehållet. När en mottagare begär en användarlicens tillämpas den principmall för rättigheter som finns i databasen med servern. På så sätt säkerställs att villkoren i en användarlicens alltid speglar den senaste versionen av mallen.
