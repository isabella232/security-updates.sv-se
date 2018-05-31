---
TOCTitle: Exkludera rättighetskontocertifikat
Title: Exkludera rättighetskontocertifikat
ms:assetid: 'cba5e901-942c-4d06-9865-e6c4648c95e6'
ms:contentKeyID: 18124897
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747670(v=WS.10)'
---

Exkludera rättighetskontocertifikat
===================================

Om en användare är betrodd men användarens RMS-referenser har komprometterats kan du exkludera användarens rättighetskontocertifikat genom att exkludera den offentliga nyckeln. När du gör det nekas alla nya licensbegäran i RMS som omfattar det aktuella rättighetskontocertifikatet. När du har exkluderat ett rättighetskontocertifikat nekas en begäran nästa gång användaren försöker hämta en användarlicens för nytt innehåll. Om användaren vill hämta en användarlicens måste han eller hon först hämta ett nytt rättighetskontocertifikat med ett nytt nyckelpar.

Rättighetskontocertifikat kan exkluderas från sidan **Exkluderingsprinciper** på administrationswebbplatsen. När du exkluderar en användares rättighetskontocertifikat läggs den exkluderade nyckeln, användarens kontonamn samt datum och tid för exkluderingen till i tabellen DRMS\_GicExclusionList i rotcertifikatklustrets konfigurationsdatabas. Den informationen visas också på sidan **Exkluderingsprinciper** på administrationswebbplatsen. Dessutom tas de offentliga och privata nycklar som är associerade med det exkluderade kontocertifikatet bort från tabellen UD\_Users i konfigurationsdatabasen.

Om du vill exkludera ett rättighetskontocertifikat som finns på en rotcertifikatserver eller ett rotcertifikatkluster anger du användarens domänkonto på sidan **Exkluderingsprinciper** för rotcertifikatservern. Du bör exkludera rättighetskontocertifikat på alla underregistrerade servrar från administrationswebbplatsen för de aktuella servrarna. Om du vill exkludera en användare på en underregistrerad licensieringsserver eller i ett licensieringskluster anger du värdet för rättighetskontocertifikatets privata nyckel på sidan **Exkluderingsprinciper** på licensieringsserverns administrationswebbplats. Det här värdet kan du hämta från sidan **Exkluderingsprinciper** på rotcertifikatklustrets administrationswebbplats.

Du kan förenkla exkludering av rättighetskontocertifikat i en RMS-distribution med flera kluster genom att replikera tabellen DRMS\_GicExclusionList från konfigurationsdatabasen på rotcertifikatkluster till konfigurationsdatabasen i varje licensieringskluster. När du gör det behöver du inte ange värdet för den offentliga nyckeln manuellt på varje server.
