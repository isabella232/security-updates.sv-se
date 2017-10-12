---
TOCTitle: 'Distribuera RMS-klienten'
Title: 'Distribuera RMS-klienten'
ms:assetid: '4b8dd930-4105-4e73-918c-12d2b05d5fb5'
ms:contentKeyID: 18124710
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720266(v=WS.10)'
---

Distribuera RMS-klienten
========================

RMS-klienten är inbyggd i operativsystemet Windows Vista®, vilket betyder att RMS-klienten inte längre är en separat installation. Operativsystem före Windows Vista kräver att du installerar RMS-klientprogramvaran och sedan aktiverar den.

I aktiveringsprocessen etableras en lockbox och ett datorcertifikat för den användare som är inloggad för tillfället. Aktiveringen är en lokal process som inte kräver nätverksanslutning. När aktiveringen har genomförts medför den första begäran om en användarlicens från ett RMS-aktiverat program att användaren får ett användarcertifikat. RMS-klienten kan installeras på varje klientdator i organisationen med hjälp av grupprinciper, Windows Update eller ett administrativt skript.

| ![](images/Cc720266.note(WS.10).gif)Obs!                                                                                                                                                                                                                            |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oavsett vilken metod för klientdistribution som används så använder RMS-klienten en port, som standard antingen port 80 eller port 443, för kommunikation med RMS-servern. Du bör se till att klientdatorn kan skicka utgående begäran till RMS-rotservern och licenskluster på de här portarna. |

**Använda grupprinciper**

Om din organisation distribuerar programvara med hjälp av grupprinciper kan metoden användas till att distribuera RMS-klienten med förhöjda privilegier. Om RMS-klienten distribueras på det sättet behöver användaren inte ha administratörsprivilegier, utan kan installera RMS-klienten antingen med **Lägg till eller ta bort program** på **Kontrollpanelen** eller genom att öppna skyddat innehåll med ett RMS-aktiverat program.

**Använda Windows Update**

Det enklaste sättet att installera RMS-klienten på en dator är att använda Windows Update. Den här metoden har fördelen att en mekanism som är välbekant för användarna används, men den kräver att användaren som installerar RMS-klienten har lokala administratörsprivilegier för datorn.

**Installera via skript**

Största möjliga kontroll över klientinstallationsprocessen får du genom att hämta programvaran och sedan validera integriteten i varje steg av installationsprocessen genom att köra ett skript. Skriptet kan skrivas och läggas till i ett grupprincipobjekt (GPO) som ett startskript. Med den här metoden behöver användaren inte vara lokal administratör för datorn och RMS-klienten installeras automatiskt vid omstart.

        ```
Grundläggande information om hur du distribuerar RMS-klienten med hjälp av grupprinciper finns i "[Konfigurera SMS eller grupprinciper för klientdistribution](https://technet.microsoft.com/9e37c27b-8cc1-40c6-adb7-0937aa64c8db)" längre fram i avsnittet.

Instruktioner om RMS-klientdistribution finns i "[Så här distribuerar du RMS-klienten](https://technet.microsoft.com/c84f1724-cf71-4385-9003-ff68bc23c927)" längre fram i avsnittet.
