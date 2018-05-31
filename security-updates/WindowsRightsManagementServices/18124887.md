---
TOCTitle: Ta bort användarkonton
Title: Ta bort användarkonton
ms:assetid: 'bf73b141-d4d1-4807-a773-3aaff58b0db6'
ms:contentKeyID: 18124887
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747653(v=WS.10)'
---

Ta bort användarkonton
======================

När du tar bort ett användarkonto i Active Directory kommer användarens rättighetskontocertifikat, som finns i tabellen med användarnycklar i rotcertifikatklustrets konfigurationsdatabas, inte att tas bort automatiskt. Därför kan tabellen med användarnycklar växa okontrollerat om inte gamla användare tas bort i takt med att nya användare läggs till.

Du kan hantera konfigurationsdatabasen genom att köra en lagrad procedur som tar bort en användarnyckel baserat på nyckelns säkerhetsidentifierare (SID) varje gång det associerade användarkontot tas bort från Active Directory. Du kan också välja att regelbundet köra ett skript som tar bort alla användarnycklar från konfigurationsdatabasen om de associerade SID:na inte längre finns i Active Directory. Observera att om du väljer den metoden belastas både SQL Server och Active Directory.
