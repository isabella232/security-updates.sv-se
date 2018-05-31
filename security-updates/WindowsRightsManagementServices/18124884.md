---
TOCTitle: 'RMS-exkludering'
Title: 'RMS-exkludering'
ms:assetid: 'c17e393e-b6a9-4ae5-aee5-18baa6b32d4d'
ms:contentKeyID: 18124884
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747656(v=WS.10)'
---

RMS-exkludering
===============

Genom exkludering kan en enhet förhindras att skaffa nya licenser från en viss server eller ett visst kluster i ett RMS-system. Exkludering skiljer sig från återkallning i det avseende att exkludering inte gör enheterna ogiltiga. Alla befintliga licenser som är knutna till exkluderade enheter är fortfarande giltiga. Endast nya begäran om licensiering nekas.

Varje RMS-server eller -kluster har egna exkluderingsprinciper som inte fortplantas till hela systemet. Via webbplatsen **Administration av RMS** kan administratörer ange exkluderingsprinciper för varje RMS-server och -kluster.

Administratörer kan basera exkludering av enheter på lockbox-version, Windows-version, rättighetskontocertifikat eller RMS-aktiverat program.
