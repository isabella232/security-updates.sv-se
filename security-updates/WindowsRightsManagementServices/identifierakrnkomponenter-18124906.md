---
TOCTitle: Identifiera kärnkomponenter
Title: Identifiera kärnkomponenter
ms:assetid: 'c9ec225b-0e51-42f5-aff6-0aecb62e3b27'
ms:contentKeyID: 18124906
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747751(v=WS.10)'
---

Identifiera kärnkomponenter
===========================

Det är viktigt att du har tillräcklig kunskap om kärnkomponenterna i en RMS-distribution och vilka funktioner de har för att kunna upprätta en lämplig topologi. I följande lista beskrivs de servrar som kommer att ingå i RMS-distributionen:

-   Rotcertifikatservrar. Rotcertifikatservern är den primära komponenten i en RMS-distribution. Alla andra komponenter är beroende av den här servern. På rotcertifikatservern körs alla RMS-tjänster, bl.a. kontocertifieringstjänsten som beviljar RMS-klienterna i organisationen RMS-kontocertifikat. Det kan bara finnas en rotcertifikatserver i varje Active Directory-skog. Men du kan lägga till flera servrar i installationen och skapa ett rotcertifikatkluster som kan användas för redundans och belastningsutjämning. För alla servrar som ingår i rotcertifikatklustret används samma konfigurationsdatabas, vilken är den databas som definierades när du etablerade den första certifikatservern i installationen.
-   Licensieringsservrar. En licensieringsserver tillhandahåller en valfri tjänst och är inte en del av rotcertifikatklustret. Däremot är licensieringsservern registrerad under rotcertifikatservern. En licensieringsserver är beroende av rotcertifikatservern för certifiering och andra tjänster (den kan inte tillhandahålla kontocertifieringstjänster), men den tillhandahåller licensieringstjänster för både publiceringslicenser och användarlicenser. Om du vill konfigurera redundans och belastningsutjämning kan du lägga till flera servrar i installationen och skapa ett licensieringskluster. För alla servrar som ingår i licensieringsklustret används samma konfigurationsdatabas, vilken är den databas som definierades när du etablerade den första licensieringsservern i klustret.
-   Servrar där komponenter i infrastrukturen körs. Distributionen kan innehålla ytterligare servrar som tillhandahåller den nödvändiga infrastrukturen, t.ex. komponenter som SQL Server 2000 och Active Directory. Vart du distribuerar sådana komponenter och hur många servrar som behövs beror på vilka krav som finns i organisationen.

Den RMS-topologi som du skapar för organisationen måste omfatta distributionen av de här komponenterna.
