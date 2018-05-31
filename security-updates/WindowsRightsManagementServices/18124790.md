---
TOCTitle: Utöka den grundläggande infrastrukturen till att hantera kluster
Title: Utöka den grundläggande infrastrukturen till att hantera kluster
ms:assetid: '78f0f2f0-a075-409c-9f46-26eb62d1d05b'
ms:contentKeyID: 18124790
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747567(v=WS.10)'
---

Utöka den grundläggande infrastrukturen till att hantera kluster
================================================================

Om du implementerar kluster för stora distributioner måste du kontrollera att infrastrukturen är konfigurerad så att de aktuella klusterkraven kan hanteras. Tänk på följande när du gör din distributionsplan.

DNS-registrering
----------------

Kontrollera att eventuell DNS-registrering som visar de virtuella IP-adresserna för extranätet också visar adressen i intranätet.

Interna användarlicensbegäran kommer att misslyckas om inte DNS-registrering utförs för intranätet. Om det inte går att ändra DNS-inställningarna kan du ändra värdtabellen för varje server som ingår i klustret så att kluster-URL:en mappas till klustrets virtuella IP-adress. DNS-registrering måste utföras innan tjänsten etableras. Om du redan har etablerat tjänsten måste du avinstallera RMS från servern och sedan upprepa etableringsprocessen.

Belastningsutjämning
--------------------

Konfigurera nödvändig maskin- och programvara för serverbaserad eller maskinvarubaserad belastningsutjämning eller för tjänsten Utjämning av nätverksbelastning, beroende på vad som fungerar bäst för fördelning av begäran i klustret.
