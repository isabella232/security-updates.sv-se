---
TOCTitle: 'RMS-konfigurationsdatabasen'
Title: 'RMS-konfigurationsdatabasen'
ms:assetid: '769adbdc-f32f-464b-85c4-e8b160036187'
ms:contentKeyID: 18124774
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747634(v=WS.10)'
---

RMS-konfigurationsdatabasen
===========================

I RMS används en databasserver, t.ex. Microsoft® SQL Server eller Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) Release A, till att lagra information om konfiguration och principer. Det finns en konfigurationsdatabas för varje RMS-server eller RMS-kluster. I databasen sparas, delas och hämtas konfigurationsinformation och annan information.

Konfigurationsdatabasen för rotcertifikatservern eller klustret innehåller en lista med Windows-användaridentiteter och deras rättighetskontocertifikat. Certifikatnyckelparet krypteras med den offentliga nyckeln för RMS-servern innan det sparas i databasen. Konfigurationsdatabaser för licensieringsservrar innehåller inte denna information.

RMS-tjänstgruppen har körrättigheter för databasens sparade procedurer.

**Viktigt!   **Vi rekommenderar att MSDE 2000 endast används med RMS-databaser i testmiljö, eftersom MSDE 2000 inte har funktioner för nätverksgränssnitt. Dessutom anger villkoren för användning av MSDE 2000 att du inte kan använda SQL Server-klientverktyg till att ändra en MSDE 2000-databas. Den här begränsningen gör att det inte går att visa loggningsinformation och att ändra data som lagras i konfigurationsdatabasen.
