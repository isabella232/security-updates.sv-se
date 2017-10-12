---
TOCTitle: Ändra konfigurationsdatabasen
Title: Ändra konfigurationsdatabasen
ms:assetid: '6a7bec73-09e4-4060-b551-5990836df4bc'
ms:contentKeyID: 18124803
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747606(v=WS.10)'
---

Ändra konfigurationsdatabasen
=============================

De ändringar av konfigurationen som du gör via administrationswebbplatsen återspeglas i konfigurationsdatabasen för servern eller klustret. Du bör alltid ändra konfigurationsinställningar från administrationswebbplatsen, inte genom att manuellt ändra data i konfigurationsdatabasen. Det finns dock två situationer då du kan behöva ändra databasen manuellt:

-   **När loggningsdatabasen flyttas till en annan server.**Som standard är loggningsdatabasen installerad på samma server som konfigurationsdatabasen. Om du bestämmer dig för att flytta loggningsdatabasen till en annan server måste du ändra konfigurationsdatabasen så att den hänvisar till den nya platsen. Mer information om hur du flyttar en loggningsdatabas, bl.a. information om hur du registrerar den nya platsen i konfigurationsdatabasen, finns i ”[Flytta loggningsdatabasen](https://technet.microsoft.com/34ea8045-dc94-422e-9601-29927cfc1534)” tidigare i det här avsnittet.
-   **När användarnycklar som är associerade med rättighetskontocertifikat tas bort**. När du tar bort ett användarkonto från Active Directory eller när du exkluderar eller återkallar ett rättighetskontocertifikat via administrationswebbplatsen tas inte användarnycklarna som är associerade med rättighetskontocertifikatet bort från konfigurationsdatabasen. Du bör ta bort dessa inaktuella användarnycklar från konfigurationsdatabasen manuellt, både av säkerhetsskäl och för att underlätta spårning av antalet klientåtkomstlicenser (CAL). Mer information om hur du tar bort användarnycklar från konfigurationsdatabasen finns i ”[Ta bort användarkonton](https://technet.microsoft.com/bf73b141-d4d1-4807-a773-3aaff58b0db6)” tidigare i det här avsnittet. Mer information om hur du spårar CAL finns i ”[Spåra rättighetskontocertifikat](https://technet.microsoft.com/5bb0f3cf-fc44-4e60-a93f-c789d6f8a902)” tidigare i det här avsnittet.

Om du behöver ändra någonting direkt i konfigurationsdatabasen bör du först kontakta databasserveradministratören.
