---
TOCTitle: Databasserverfunktioner för RMS
Title: Databasserverfunktioner för RMS
ms:assetid: 'c9844783-e6c4-49b4-8e7f-0f0377143b44'
ms:contentKeyID: 18124903
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747664(v=WS.10)'
---

Databasserverfunktioner för RMS
===============================

I RMS används en databasserver, t.ex. Microsoft® SQL Server eller Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) Release A, till att hantera RMS-konfigurationen, loggning och katalogtjänstdatabaserna. Du kan endast använda MSDE 2000 i distributioner med en enkel server. Som skydd mot växling vid fel kan du implementera ett databasserverkluster.

För att uppfylla behovet av loggning kan du också köra konfigurations- och loggningsdatabaserna på separata databasserverinstanser eller skapa en separat databasserverinstans eller ett separat databaskluster för rotcertifikatservern eller -klustret och licencieringsklustren. Mer information om de här alternativen finns i ”Distribuera ett RMS-system”.

Som standard har RMS-tjänstgruppen körbehörighet för de lagrade procedurerna i de här databaserna. Det användarkonto som loggats in vid etableringen har rättigheter som ägare av dessa databaser.

| ![](images/Cc747664.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Vi rekommenderar att Microsoft SQL Server Desktop Engine endast används tillsammans med RMS-databaser i testmiljö, eftersom Microsoft SQL Server Desktop Engine inte innehåller alla verktyg som behövs för att fungera med en databas i företagsskala. Eftersom MSDE inte har funktioner för fjärrnätverk måste du installera det på samma server som RMS och du kan då inte lägga till fler RMS-servrar i RMS-klustret. Dessutom anger villkoren för användning av Microsoft SQL Server Desktop Engine att du inte får använda SQL Server-klientverktygen till att ändra en Microsoft SQL Server Desktop Engine-databas. Med den här begränsningen kan du inte säkerhetskopiera eller återställa RMS-konfigurationsdatabasen, visa loggningsinformation eller ändra data som lagrats i konfigurationsdatabasen direkt. |
