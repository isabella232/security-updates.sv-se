---
TOCTitle: Ta bort principmallar för rättigheter
Title: Ta bort principmallar för rättigheter
ms:assetid: '32bf98c7-edda-4507-a4b8-4c11bddd6e60'
ms:contentKeyID: 18124697
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720239(v=WS.10)'
---

Ta bort principmallar för rättigheter
=====================================

Ta bort en principmall för rättigheter från datorn om du inte vill använda den längre. Den här proceduren beskrivs i ”[Så här tar du bort en principmall för rättigheter](https://technet.microsoft.com/9c9a1496-cf55-4c65-a4c6-9fe245edce00)” senare i det här avsnittet. Normalt bör du dock inte ta bort principmallar för rättigheter. Om du trots allt vill ta bort en principmall för rättigheter bör du också ta bort kopior av den från användarnas datorer. Det bör du göra eftersom en begäran skickas till RMS-servern när en författare publicerar innehåll med en principmall för rättigheter. RMS använder en kopia av principmallen för rättigheter som lagras i databasen till att svara på begäran. Om principmallen för rättigheter inte finns i databasen misslyckas begäran.

| ![](images/Cc720239.note(WS.10).gif)Obs!                                                                                           |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ett sätt att hantera borttagning av principmallar för rättigheter är att skapa ett skript som tar bort principmallen för rättigheter från alla användardatorer. |
