---
TOCTitle: Nyheter i Service Pack 2
Title: Nyheter i Service Pack 2
ms:assetid: 'a944cb73-d900-42bb-b7aa-92916dead408'
ms:contentKeyID: 18124861
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747629(v=WS.10)'
---

Nyheter i Service Pack 2
========================

Rights Management Services (RMS) med Service Pack 2 (SP2) innehåller följande funktioner:

-   **Inbygga funktioner för Microsoft® SQL Server™ 2005**. I tidigare versioner av RMS krävdes en tillfällig lösning för att kunna använda RMS med SQL Server 2005. Mer information om den lösningen finns i artikel 913372 i Microsoft Knowledge Base ([http://go.microsoft.com/fwlink/?LinkId=68638](http://go.microsoft.com/fwlink/?linkid=68638)). Det här problemet har åtgärdats i RMS med SP2.
-   **Microsoft Office SharePoint® Server 2007**. Den här versionen har funktioner för Office SharePoint Server 2007. När du hämtar dokument baserade på Office SharePoint Server 2007-rättigheter tilldelas de automatiskt RMS-behörighet i dokumentbiblioteket för Office SharePoint Server 2007. Den här funktionen aktiverar du genom att installera RMS med SP2-klienten på Office SharePoint Server 2007-servern. Du bör inte installera RMS med SP2-server och Office SharePoint Server 2007 på samma dator.
-   **Ökad säkerhet för meddelanden till loggningsdatabasen**. I den här versionen får alla Message Queuing-meddelanden från RMS-servrar till RMS-loggningsdatabasen en digital signatur.
-   **Mer utrymme för serverbatchning**. I den här versionen kan ett RMS-aktiverat program användas för att hämta flera användarlicenser för olika användarkonton från en enda licensbegäran till RMS-servern. Detta leder till ökade prestanda tack vare att belastningen från flera licensbegäran för en typ av rättighetsskyddat innehåll minskar.
-   **Utökad gruppexpandering mellan skogar**. I den här versionen sker RMS-gruppexpandering mellan skogar genom SOAP-begäran (Simple Object Access Protocol) till en ny ASP.NET-webbtjänst som körs på RMS-servern.
