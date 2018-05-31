---
TOCTitle: 'Steg 1: Gå igenom installationskraven för WSUS'
Title: 'Steg 1: Gå igenom installationskraven för WSUS'
ms:assetid: '57d7f8ec-1523-4485-9967-604be9ba2aac'
ms:contentKeyID: 18152847
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720547(v=WS.10)'
---

Steg 1: Gå igenom installationskraven för WSUS
==============================================

I den här handledningen finns instruktioner om hur du installerar Microsoft Windows Server Update Services (WSUS) på Microsoft Windows Server 2003 (utom för Web Edition och alla 64-bitarsversioner). Om du har en server med Microsoft Windows 2000 Server och behöver mer information, går du till vitboken “Deploying Microsoft Windows Server Update Services” (på engelska).

Här följer några grundläggande krav för installationer med standardalternativen. Maskinvaru- och programvarukrav för övriga installationer finns i vitboken “Deploying Microsoft Windows Server Update Services”.

Rekommenderad maskinvara för en server med högst 500 klienter:

-   Processor med 1 GHz
-   1 GB RAM-minne

Programkrav
-----------

Om du vill installera WSUS med standardalternativen måste följande finnas på datorn. Mer information om programkrav för WSUS finns i vitboken “Deploying Microsoft Windows Server Update Services”. Om någon av uppdateringarna kräver att datorn startas om när installationen har slutförts, startar du om datorn innan du installerar WSUS.

-   Microsoft Internet Information Services (IIS) 6.0. Information om hur du installerar IIS finns i vitboken “Deploying Microsoft Windows Server Update Services” och i Hjälp- och supportcenter i Windows Server 2003.
-   Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003. Hämta programmet från [Download Center](http://go.microsoft.com/fwlink/?linkid=47358) på http://go.microsoft.com/fwlink/?LinkId=47358 (texten kan vara på engelska).
    Du kan även gå till http://www.windowsupdate.com och söka efter information om kritiska uppdateringar och Service Packs och hur du installerar Microsoft .NET Framework 1.1 Service Pack 1 för Windows Server 2003.
-   BITS 2.0 (Background Intelligent Transfer Service) BITS 2.0 för Windows Server 2003 kan för närvarande inte hämtas från Download Center. Hämta programmet på [Microsoft-webbplatsen](http://go.microsoft.com/fwlink/?linkid=47357) för Windows Server Update Services Open Evaluation på http://go.microsoft.com/fwlink/?LinkId=47357 (texten kan vara på engelska).

| ![](images/Cc720547.note(WS.10).gif)Obs!                                                                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Databasprogram som krävs för WSUS anges inte här eftersom standardinstallationen av WSUS på Windows Server 2003 innehåller databasprogrammet Windows SQL Server™ 2000 Desktop Engine (WMSDE). |

Krav på diskutrymme och övriga rekommendationer
-----------------------------------------------

Serverns filsystem måste uppfylla följande krav för att WSUS ska kunna installeras:

-   Både systempartitionen och den partition där du installerar WSUS måste vara NTFS-formaterade.
-   För systempartitionen krävs minst 1 GB ledigt diskutrymme.
-   För den volym där innehåll lagras krävs minst 6 GB ledigt diskutrymme. 30 GB rekommenderas dock.
-   För den volym där Windows SQL Server 2000 Desktop Engine (WMSDE) installeras krävs minst 2 GB ledigt diskutrymme.

Krav för Automatiska uppdateringar
----------------------------------

Automatiska uppdateringar är klientkomponenten i WSUS. För Automatiska uppdateringar finns inga maskinvarukrav förutom en nätverksanslutning. Du kan använda Automatiska uppdateringar med WSUS på datorer med något av följande operativsystem:

-   Microsoft Windows 2000 Professional med Service Pack 3 (SP3) eller Service Pack 4 (SP4), Windows 2000 Server med SP3 eller SP4 eller Windows 2000 Advanced Server med SP3 eller SP4.
-   Microsoft Windows XP Professional, med eller utan Service Pack 1 eller Service Pack 2.
-   Microsoft Windows Server 2003, Standard Edition; Windows Server 2003, Enterprise Edition; Windows Server 2003, Datacenter Edition eller Windows Server 2003, Web Edition.
