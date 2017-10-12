---
TOCTitle: Identifiering av registreringstjänsten
Title: Identifiering av registreringstjänsten
ms:assetid: 'bbeb00bd-04e0-4df6-8615-76aa8125b620'
ms:contentKeyID: 18124882
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747737(v=WS.10)'
---

Identifiering av registreringstjänsten
======================================

Den första RMS-servern som ska etableras i en skog måste anslutas till Microsofts registreringstjänst för att registreras och för att ett serverlicensieringscertifikat ska erhållas. För att ta reda på registreringstjänstens URL skickas en UDDI-begäran från installationsprogrammet för RMS till [Microsofts UDDI-webbplats](http://go.microsoft.com/fwlink/?linkid=14794) (http://go.microsoft.com/fwlink/?LinkId=14794). Servrar som senare etableras som delar av rotcertifieringsklustret behöver inte skaffa serverlicensieringscertifikat eftersom de delar konfiguration med den första rotcertifikatservern.
