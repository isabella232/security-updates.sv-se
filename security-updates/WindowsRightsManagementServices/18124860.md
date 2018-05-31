---
TOCTitle: Beräkna databasens tillväxt
Title: Beräkna databasens tillväxt
ms:assetid: '87652cc2-b886-4797-8d40-356669768089'
ms:contentKeyID: 18124860
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747585(v=WS.10)'
---

Beräkna databasens tillväxt
===========================

När du beräknar hur mycket lagringsutrymme som krävs för RMS-databaserna ska du räkna med en minimikapacitet på 10 megabyte (MB) och lägga till en (1) MB per 500 användare i RMS-konfigurationsdatabasen. Loggningsdatabasen kan ligga på en annan server än konfigurationsdatabasen.

Om du använder loggningsfunktionen i RMS måste loggningsdatabasen kunna hantera en tillväxt på cirka 1 MB för varje användare under den inledande användarcertifieringsfasen med hög loggningsaktivitet. Om din distribution till exempel ska hantera 1 000 användare kommer loggningsdatabasen att växa till 1 gigabyte (GB) allt eftersom användarna aktiveras och certifieras via RMS-certifikatservern. Vid rutinmässig drift kan loggningsdatabasen växa med 200 kilobyte (kB) per användare och dag (om du genomför ett fasindelat införande bör du beräkna 1 MB extra för varje ny användare som läggs till systemet).
