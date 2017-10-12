---
TOCTitle: 'Steg 1: Bekräfta installationskraven för WSUS 3.0 SP2'
Title: 'Steg 1: Bekräfta installationskraven för WSUS 3.0 SP2'
ms:assetid: 'ec01bd75-5def-4899-8cee-ddab827bbd83'
ms:contentKeyID: 21799712
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Dd939916(v=WS.10)'
---

Steg 1: Bekräfta installationskraven för WSUS 3.0 SP2
=====================================================

Innan du installerar eller uppgraderar till Windows Server Update Services 3.0 Service Pack 2 (WSUS 3.0 SP2) ska du bekräfta att både servern och klientdatorerna uppfyller systemkraven för WSUS 3.0 SP2 och att du har tillräckliga behörigheter för att slutföra installationen.

Krav på servermaskinvara och serverprogramvara för att installera WSUS 3.0 SP2
------------------------------------------------------------------------------

1.  Bekräfta att servern uppfyller WSUS 3.0 SP2-systemkraven för maskinvara, operativsystem och annan obligatorisk programvara. Systemkraven finns i Viktigt för WSUS 3.0 SP2 på [http://go.microsoft.com/fwlink/?LinkId=139840](http://go.microsoft.com/fwlink/?linkid=139840). Om du använder Serverhanteraren för att installera WSUS 3.0 SP2 Server kan du bekräfta att programvarukraven uppfylls genom att följa stegen i avsnittet Förbereda för installation av WSUS 3.0 SP2.
2.  Om du installerar roller eller programvara som kräver att servern startas om när installationen har slutförts, ska du starta om servern innan du installerar WSUS 3.0 SP2.

Krav på klientprogramvara
-------------------------

Automatiska uppdateringar fungerar som för WSUS 3.0. För Automatiska uppdateringar finns inga maskinvarukrav förutom en nätverksanslutning.

1.  Bekräfta att den dator där du installerar Automatiska uppdateringar uppfyller WSUS 3.0 SP2-systemkraven för klientdatorer. Systemkraven finns i Viktigt för WSUS 3.0 SP2 på [http://go.microsoft.com/fwlink/?LinkId=139840](http://go.microsoft.com/fwlink/?linkid=139840).
2.  Om du installerar programvaruuppdateringar som kräver att datorn startas om, ska du starta om datorn innan du installerar WSUS 3.0 SP2.

Behörigheter
------------

Följande behörigheter krävs för de angivna användarna och katalogerna:

1.  Kontot NT Authority\\Network Service måste ha behörigheten Fullständig behörighet för följande mappar för att snapin-modulen Administration av WSUS ska kunna visas korrekt:
    -   %windir%\\Microsoft .NET\\Framework\\v2.0.50727\\Temporary ASP.NET Files
    -   %windir%\\Temp
2.  Bekräfta att det konto som du tänker använda för att installera WSUS 3.0 SP2 är medlem i den lokala gruppen Administratörer.

Förbereda för installation av WSUS 3.0 SP2
------------------------------------------

Om du använder Windows 7 eller Windows Server 2008 SP2 kan du installera WSUS 3.0 SP2 från Serverhanteraren. Om du använder något annat operativsystem som stöds, eller om du endast ska installera administrationskonsolen för WSUS, går du till nästa avsnitt i den här handboken för att installera WSUS 3.0 SP2 med hjälp av filen WSUSSetup.exe.

**Så här förbereder du för installation av WSUS 3.0 SP2 Server med hjälp av Serverhanteraren**
1.  Logga in på den server där du ska installera WSUS 3.0 SP2 med ett konto som är medlem i den lokala gruppen Administratörer.

2.  Klicka på **Start**, peka på **Administrationsverktyg** och klicka sedan på **Serverhanteraren**.

3.  Klicka på **Lägg till roller** under Rollsammanfattning i rutan till höger i fönstret Serverhanteraren.

4.  Om sidan Innan du börjar visas klickar du på **Nästa**.

5.  Kontrollera att **Programserver** och **Webbserver (IIS)** har markerats på sidan Välj serverroller. Om de har markerats ägnar du resten av det här steget till att bekräfta att de serverroller som krävs har markerats. Annars installerar du Programserver och Webbserver (IIS) enligt följande.

    1.  Markera **Programserver** och **Webbserver (IIS)** på sidan Välj serverroller. Klicka på **Nästa**.
    2.  Om du installerar rolltjänster för Programserver klickar du på **Nästa** på sidan Programserver. Acceptera standardinställningarna på sidan Rolltjänster för Programserver och klicka sedan på **Nästa**.
    3.  Om du installerar rolltjänster för Webbserver (IIS) klickar du på **Nästa** på sidan Webbserver (IIS). Utöver standardinställningarna på sidan Rolltjänster för Webbserver (IIS) markerar du **ASP.NET**, **Windows-autentisering**, **Komprimering av dynamiskt innehåll** och **IIS 6-kompatibilitetshantering**. Om guiden Lägg till roller visas klickar du på **Lägg till nödvändiga rolltjänster**. Klicka på **Nästa**.
    4.  Klicka på **Installera** på sidan Bekräfta installationsinställningarna.
    5.  Kontrollera att meddelandet Installationen har slutförts visas på sidan Installationsresultat för de rolltjänster som har installerats i det här steget och klicka sedan på **Stäng**.

Nästa steg
----------

[Steg 2: Installera WSUS Server eller administrationskonsolen](https://technet.microsoft.com/6db6fcb0-c55d-43b9-9b07-4040c6267759).

Ytterligare resurser
--------------------

[Steg-för-steg-guide för Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)
