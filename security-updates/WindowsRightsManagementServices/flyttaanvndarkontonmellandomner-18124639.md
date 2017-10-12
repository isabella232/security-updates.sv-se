---
TOCTitle: Flytta användarkonton mellan domäner
Title: Flytta användarkonton mellan domäner
ms:assetid: '0010b0ea-07c0-41c9-81f7-5881343d1d55'
ms:contentKeyID: 18124639
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720179(v=WS.10)'
---

Flytta användarkonton mellan domäner
====================================

När du konfigurerar och etablerar en rotcertifikatserver i en organisation registreras den i Active Directory som en RMS-tjänstleverantör i inställningarna för den aktuella skogen. Det kan bara finnas ett rotcertifikatkluster i varje Active Directory-skog.

Normalt skapas ett nytt SID för ett användarkonto när du flyttar det från en domän till en annan domän i samma skog. När användaren sedan försöker hämta ett nytt rättighetskontocertifikat från servern identifieras användaren som ny användare av servern på grund av det nya SID:t. Servern genererar nya nycklar för användaren och utfärdar det nya rättighetskontocertifikatet med hjälp av användarens ursprungliga e-postadress. När användaren försöker använda det nya rättighetskontocertifikatet med en befintlig licens matchar inte SID:t och nycklarna, och användaren måste därför erhålla nya licenser. Det här gäller också när du flyttar ett användarkonto till en domän i en annan skog.
