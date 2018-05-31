---
TOCTitle: 'Steg 1: Gå igenom installationskraven för WSUS 3.0'
Title: 'Steg 1: Gå igenom installationskraven för WSUS 3.0'
ms:assetid: '912b37d7-021e-4c95-b317-49dd15b4611c'
ms:contentKeyID: 18152918
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708484(v=WS.10)'
---

Steg 1: Gå igenom installationskraven för WSUS 3.0
==================================================

I den här guiden beskrivs hur du installerar WSUS 3.0. Information om programvarukrav och vilka plattformar som stöds för WSUS 3.0 finns i filen Viktigt ([http://go.microsoft.com/fwlink/?LinkId=71220](http://go.microsoft.com/fwlink/?linkid=71220)). för operativsystemen Windows Server 2003 Service Pack 1 och Windows Server® 2008.

Programvarukrav för installation av WSUS 3.0 på Windows Server 2003 Service Pack 1
----------------------------------------------------------------------------------

Om du vill installera WSUS 3.0 på Windows Server 2003 Service Pack 1 behöver du ha följande programvara installerad på datorn. Om någon av uppdateringarna kräver att servern startas om när installationen har slutförts, startar du om servern innan du installerar WSUS 3.0.

-   Microsoft Internet Information Services (IIS) 6.0.
-   Uppdatering för BITS (Background Intelligent Transfer Service) 2.0 och WinHTTP 5.1 Windows Server 2003. Om du vill hämta det här programmet går du till Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkID=47251](http://go.microsoft.com/fwlink/?linkid=47251)).
-   Microsoft .NET Framework Version 2.0 Redistributable Package (x86). Om du vill hämta det här programmet går du till Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkID=68935](http://go.microsoft.com/fwlink/?linkid=68935)). (För 64-bitars plattformar går du också till Microsoft Download Center \[[http://go.microsoft.com/fwlink/?LinkID=70637](http://go.microsoft.com/fwlink/?linkid=70637)\].)
-   Microsoft Report Viewer Redistributable 2005. Om du vill hämta det här programmet går du till Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkID=70410](http://go.microsoft.com/fwlink/?linkid=70410)).
-   Microsoft Management Console 3.0 för Windows Server 2003 (KB907265). Om du vill hämta det här programmet går du till Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkID=70412](http://go.microsoft.com/fwlink/?linkid=70412)). (För 64-bitars plattformar går du också till Microsoft Download Center \[[http://go.microsoft.com/fwlink/?LinkID=70638](http://go.microsoft.com/fwlink/?linkid=70638)\].)

Programvarukrav för installation av WSUS 3.0 på Windows Server 2008
-------------------------------------------------------------------

Om du vill installera WSUS 3.0 på Windows Server 2008 behöver du ha följande programvara installerad på datorn. Om någon av uppdateringarna kräver att servern startas om när installationen har slutförts, startar du om servern innan du installerar WSUS 3.0.

-   Microsoft Internet Information Services (IIS) 7,0. Kontrollera att följande komponenter är aktiverade:
    -   Windows-autentisering
    -   ASP.NET
    -   6.0-kompatibilitetshantering
    -   IIS-metabaskompatibilitet
-   Microsoft Report Viewer Redistributable 2005. Om du vill hämta det här programmet går du till Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkID=70410](http://go.microsoft.com/fwlink/?linkid=70410)).
-   Microsoft SQL Server™ 2005 Service Pack 1. Om du vill hämta det här programmet går du till Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkID=66143](http://go.microsoft.com/fwlink/?linkid=66143)).

Uppdateringen för .NET Framework 2.0 och BITS 2.0 finns på Windows Server 2008 och ingår i operativsystemet.

Krav på diskutrymme och övriga rekommendationer
-----------------------------------------------

Serverns filsystem måste uppfylla följande krav för att WSUS 3.0 ska kunna installeras:

-   Både systempartitionen och den partition där du installerar WSUS 3.0 måste vara NTFS-formaterade.
-   För systempartitionen rekommenderas minst 1 GB ledigt diskutrymme.
-   För den volym där WSUS lagrar innehåll krävs minst 20 GB ledigt diskutrymme. 30 GB ledigt diskutrymme är önskvärt.
-   Minst 2 GB ledigt diskutrymme rekommenderas för den volym där WSUS installerar Windows® Internal Database.

Krav för installation av endast konsol
--------------------------------------

Med WSUS 3.0 kan du nu installera WSUS administrationskonsol på fjärrsystem separat från WSUS-servern. Installation av endast konsolen kan göras på följande operativsystem:

-   Windows Server® 2008
-   Windows Vista®
-   Windows Server 2003 Service Pack 1
-   Windows XP Service Pack 2

Följande programvarukrav gäler vid installation av endast konsol

-   Microsoft .NET Framework Version 2.0 Redistributable Package (x86) som finns att hämta från Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkId=68935](http://go.microsoft.com/fwlink/?linkid=68935)). För 64-bitars plattformar går du till Microsoft .NET Framework Version 2.0 Redistributable Package (x64) ([http://go.microsoft.com/fwlink/?LinkId=70637](http://go.microsoft.com/fwlink/?linkid=70637)).
-   Microsoft Management Console 3.0 för Windows Server 2003 (KB907265) som finns att hämta på Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkId=70412](http://go.microsoft.com/fwlink/?linkid=70412)). För 64-bitars plattformar går du till Microsoft Management Console 3.0 för Windows Server 2003 x64 Edition (KB907265) ([http://go.microsoft.com/fwlink/?LinkId=70638](http://go.microsoft.com/fwlink/?linkid=70638)).
-   Microsoft Report Viewer Redistributable 2005 som finns att hämta på Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkId=70410](http://go.microsoft.com/fwlink/?linkid=70410)).

Krav för Automatiska uppdateringar
----------------------------------

Automatiska uppdateringar är klientkomponenten i WSUS 3.0. För Automatiska uppdateringar finns inga maskinvarukrav förutom en nätverksanslutning. Du kan använda Automatiska uppdateringar med WSUS 3.0 på datorer med något av följande operativsystem:

-   Windows Vista.
-   Windows Server® 2008.
-   Microsoft Windows® Server 2003, alla versioner och Service Pack.
-   Microsoft Windows XP Professional, Service Pack 1 eller Service Pack 2.
-   Microsoft Windows 2000 Professional Service Pack 4, Windows 2000 Server Service Pack 4 eller Windows 2000 Advanced Server Service Pack 4.

Behörigheter
------------

Följande diskbehörigheter måste de specificerade användarna ha för de specificerade katalogerna:

1.  Antingen den inbyggda gruppen Användare eller kontot NT instans\\Nätverkstjänst (på Windows Server 2003) behöver läsbehörighet till rotmappen på den enhet där innehållskatalogen för WSUS finns. Om denna behörighet saknas går det inte att hämta BITS.
2.  Kontot NT instans\\Nätverkstjänst behöver behörigheten Fullständig behörighet till innehållskatalogen för WSUS, vanligen &lt;SystemDriver&gt;:WSUS\\WsusContent. Denna behörighet ställs in under WSUS-serverinstallationen när katalogen skapas, men en del säkerhetsprogramvara kan återställa behörigheten. Om denna behörighet saknas går det inte att hämta BITS.
3.  Kontot NT instans\\Nätverkstjänst behöver ha behörigheten Fullständig behörighet till följande mappar för att administrationssnapin-modulen för WSUS ska visas korrekt:
    -   %windir%\\Microsoft .NET\\Framework\\v2.0.50727\\Temporary ASP.NET Files
    -   %windir%\\Temp

Ytterligare information om behörighetsinställningar finns i artikeln DCPROMO Does Not Retain Permissions on Some IIS Folders på [http://go.microsoft.com/fwlink/?LinkID=76332](http://go.microsoft.com/fwlink/?linkid=76332).
