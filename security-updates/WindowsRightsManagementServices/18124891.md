---
TOCTitle: 'Ta bort RMS-skydd från innehåll'
Title: 'Ta bort RMS-skydd från innehåll'
ms:assetid: 'c30361e3-50d2-4474-a87d-d38de502cf9e'
ms:contentKeyID: 18124891
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747658(v=WS.10)'
---

Ta bort RMS-skydd från innehåll
===============================

Bestäm i förväg vilka filer som behöver återställas, av vem och när, så att viktig information bevaras när inaktiveringsprocessen är avslutad. När RMS-skyddet har tagits bort från alla nödvändiga RMS-skyddade filer kan servern avlägsnas från infrastrukturen.

Proceduren för att ta bort RMS-skydd från innehåll är som följer:

1.  Användaren ska ta bort alla befintliga användarlicenser från datorn. Det gör att RMS-klienten går direkt till servern för att få en licens för att öppna innehållet. Användarlicenser lagras i mappen %USERPROFILE%\\Local Settings\\Application Data\\Microsoft\\DRM på klientdatorn och har prefixet EUL för filnamnet.
2.  En användare med tillgång till inaktiveringsservern försöker att öppna en RMS-skyddad fil.
3.  Programmet ansluts till inaktiveringsservern och en innehållsnyckel skickas.
4.  Innehållet dekrypteras och kan redigeras, sparas, vidarebefordras eller skrivas ut.
5.  Användaren sparar innehållet utan RMS-skydd. Alla användare kan nu öppna innehållet utan att ansluta till RMS-servern.
