---
TOCTitle: Flytta loggningsdatabasen
Title: Flytta loggningsdatabasen
ms:assetid: '34ea8045-dc94-422e-9601-29927cfc1534'
ms:contentKeyID: 18124677
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720238(v=WS.10)'
---

Flytta loggningsdatabasen
=========================

I RMS-standardkonfigurationen placeras konfigurations- och loggningsdatabaserna på samma server. Kontrollera regelbundet att SQL Server har tillräckligt med ledigt diskutrymme för både loggnings- och konfigurationsdatabaserna.

Om loggningsdatabasen blir för stor kan du när som helst flytta den till en annan server, men det går inte att flytta loggningsdatabasen från administrationswebbplatsen. Det måste du göra manuellt genom att följa dessa steg:

1.  Stäng av loggningen. Hur du gör det beskrivs i ”[Så här aktiverar och inaktiverar du loggning](https://technet.microsoft.com/8e672f95-566f-4070-9a2a-2f70f087148f)” senare i det här avsnittet.
2.  Kopiera loggningsdatabasen från den ursprungliga servern till målservern med hjälp av SQL Server Enterprise Manager. Kontrollera att tabellerna och de lagrade procedurerna skapas i den nya databasen. Ett sätt att göra det är att använda SQL Server Enterprise Manager-guiden för kopiering av databaser.
3.  Ändra konfigurationsdatabasen så att den innehåller den nya serverns och databasens namn. Gör följande i tabellen DRMS\_ClusterPolicies för den aktuella konfigurationsdatabasen i det aktuella klustret:
    -   Ändra värdet på principen LoggingDatabaseServer så att den återspeglar den nya databasserverns namn.
    -   Ändra värdet på principen LoggingDatabaseName så att den återspeglar den nya databasens namn.

    | ![](images/Cc720238.note(WS.10).gif)Obs!                                                                                                                                                                                  |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | SQL Server Enterprise Manager fungerar inte med db\_variant-fält, så du kan inte använda den typen av fält till den här uppgiften. Använd i stället den frågeanalysator som ingår i SQL Server eller något annat verktyg avsett för databasredigering. |

4.  Starta om IIS på alla servrar som ingår i klustret.
5.  Aktivera loggning igen.
