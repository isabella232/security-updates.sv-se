---
TOCTitle: 'Tips om RMS-administrationsmetoder'
Title: 'Tips om RMS-administrationsmetoder'
ms:assetid: '385f8112-da00-417f-a2b8-42dc1e06b717'
ms:contentKeyID: 18124701
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720245(v=WS.10)'
---

Tips om RMS-administrationsmetoder
==================================

Tänk på följande när du administrerar RMS.

-   **Distribuera inte ytterligare tjänster på RMS-servrar**
    Om du kör andra tjänster än RMS-tjänster på servrarna kan konflikter uppstå som leder till säkerhetsproblem. Använd prestandaräknare, som hjälper dig att upptäcka konflikter och försämringar i tjänsten.
-   **Säkerhetskopiera konfigurationsdatabaserna regelbundet**
    I konfigurationsdatabaserna lagras information som är avgörande för att RMS ska fungera. Dessutom lagrar rotcertifikatklustrets konfigurationsdatabas nyckelpar för hela installationen. Om du säkerhetskopierar regelbundet kan du snabbt återställa RMS igen om en databasserver upphör att fungera. Förutom regelbunden säkerhetskopiering bör du också regelbundet testa giltigheten i säkerhetskopiorna genom att göra teståterställningar (i en separat testmiljö). Mer information finns i ”Säkerhetskopiera och återställa systemet för RMS” i ”Planera en RMS-distribution”.
-   **Rensa loggningsdatabasen regelbundet**
-   **Använd Microsoft Operations Manager (MOM) till att övervaka RMS-servern**
    Använd MOM och RMS MOM-paketet till att ringa in kritiska händelser, upptäcka försämringar i tjänsten och skicka meddelanden om sådana händelser.
