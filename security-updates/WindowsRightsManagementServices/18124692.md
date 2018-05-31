---
TOCTitle: Hantera loggstorleken
Title: Hantera loggstorleken
ms:assetid: '431b32b3-02f0-4666-b52c-183eb65154fd'
ms:contentKeyID: 18124692
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720271(v=WS.10)'
---

Hantera loggstorleken
=====================

Med loggningstjänsten skickas stora mängder data till SQL Server-databasen. Du bör kontrollera loggningsdatabasen regelbundet så att det finns tillräckligt med diskutrymme för alla data. Om du anser att mängden data som skickas är för stor och att all information inte intressant för dina rapporteringsbehov kan du minska loggfilernas storlek med SQL Server-filter, så att enbart de loggar du behöver lagras. Instruktioner om hur du filtrerar loggningsinformation finns i SQL Server Enterprise Manager-hjälpen.

Om du upptäcker att loggningsdatabasen växer allt för snabbt i förhållande till mängden ledigt diskutrymme kan du flytta loggningsdatabasen till en annan server. Information om det finns i ”[Flytta loggningsdatabasen](https://technet.microsoft.com/34ea8045-dc94-422e-9601-29927cfc1534)” senare i det här avsnittet.

| ![](images/Cc720271.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                              |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Du bör också regelbundet övervaka storleken på meddelandekön för utgående loggning med hjälp av Systemövervakaren. Kontrollera att lyssnartjänsten för loggning fungerar korrekt om köns storlek ökar markant. Mer information om hur du använder Systemövervakaren finns i Hjälp- och supportcenter i Windows Server 2003. |
