---
TOCTitle: Säkerhetskopiera och återställa principmallar för rättigheter
Title: Säkerhetskopiera och återställa principmallar för rättigheter
ms:assetid: 'a6ed3328-4128-45e8-9236-3de484b460de'
ms:contentKeyID: 18124855
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747625(v=WS.10)'
---

Säkerhetskopiera och återställa principmallar för rättigheter
=============================================================

Du skyddar viktiga principmallar för rättigheter genom att regelbundet säkerhetskopiera alla malldata som finns i konfigurationsdatabasen på ett medium och förvara säkerhetskopian på en säker plats. Om ett systemfel sedan inträffar kan du återställa principmallarna för rättigheter från säkerhetskopian.

Gör något av följande:

-   Säkerhetskopiera hela konfigurationsdatabasen som innehåller alla data om principmallar för rättigheter. Mer information om hur du säkerhetskopierar en SQL Server-databas finns i dokumentationen till SQL Server.
    eller
-   Säkerhetskopiera bara den information om principmallar för rättigheter som finns i konfigurationsdatabasen. Du gör det genom att exportera GUID- och TemplateData-information från tabellen DRMS\_RightsTemplate till en ny textfil. Mer information om hur du exporterar data från en SQL Server-databas finns i dokumentationen till SQL Server.

Om du behöver återställa den information om principmallar för rättigheter som finns i konfigurationsdatabasen kan du extrahera GUID- och TemplateData-informationen från tabellen DRMS\_RightsTemplate i säkerhetskopian av konfigurationsdatabasen. Du kan också importera dessa data från textfilen. Mer information om dessa åtgärder finns i dokumentationen till SQL Server.

| ![](images/Cc747625.note(WS.10).gif)Obs!                                                                     |
|-------------------------------------------------------------------------------------------------------------------------------------------|
| Kontakta SQL Server-administratören om du vill ha hjälp med att upprätta en plan för säkerhetskopiering av principmallar för rättigheter. |
