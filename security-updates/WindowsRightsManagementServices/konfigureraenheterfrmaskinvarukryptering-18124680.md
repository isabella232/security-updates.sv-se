---
TOCTitle: Konfigurera enheter för maskinvarukryptering
Title: Konfigurera enheter för maskinvarukryptering
ms:assetid: '3a35a8ea-696c-4005-9892-cac6e773497a'
ms:contentKeyID: 18124680
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720248(v=WS.10)'
---

Konfigurera enheter för maskinvarukryptering
============================================

I RMS kan någon av Windows standard-CSP:er (kryptografiprovider) användas, t.ex. grundläggande och utökade CSP:er, till att generera de offentliga och privata nycklar som lagras i konfigurationsdatabasen och som används till att skydda innehåll. Du bör förse nycklarna med extra skydd eftersom de lagras i programmet. Du kan använda en maskinvarubaserad CSP från en HSM om du vill ha ett bättre skydd.

Om du använder en HSM till att öka skyddet av servernycklarna installerar och konfigurerar du den maskinvaran på servrarna innan du installerar Windows RMS.
