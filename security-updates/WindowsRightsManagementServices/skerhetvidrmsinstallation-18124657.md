---
TOCTitle: 'Säkerhet vid RMS-installation'
Title: 'Säkerhet vid RMS-installation'
ms:assetid: '0a3d40b2-f27e-4e63-baff-a9c8433f5f91'
ms:contentKeyID: 18124657
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720192(v=WS.10)'
---

Säkerhet vid RMS-installation
=============================

Vid installationen och konfigurationen av filerna i RMS använder installationsprogrammet den inloggade användarens konto och identitet. Av den anledningen måste den administratör som utför installationen logga in med ett användarkonto som tillhör den lokala administratörsgruppen. Vid alla installationer, förutom installationer på enstaka datorer, måste detta konto också vara ett domänanvändarkonto.

Vid installationen startas tjänsten Windows Installer (Msiexec.exe). Den tjänsten ärver sitt överordnade användar-token. Om det förekommer anpassade åtgärder för efterbehandling, använder tjänsten Msiexec.exe den inloggade användarens identitet. Detta inträffar oavsett om processen startas från en webbläsare eller från kommandoraden.

Följande utförs i installationsprogrammet för RMS:

-   Filer kopieras till mappen C:\\Program Files\\RMS. Normalt ges både administratörer och särskilda användare åtkomsträttigheter till den mappen. Du kan bestämma vilken enhet och katalog mappen ska placeras i.
-   Webbplatsen för etablering, webbplatsen Administration av RMS, skapas på port 5720 (som standard). Den webbplatsen refererar till installerade filer.
-   Programpoolen WMCSProvisioningAppPool skapas och kopplas till webbplatsen Administration av RMS. Det tjänstkonto som används av denna programpool är tjänstkontot för Network Services.
-   Prestandaräknare installeras.
-   Läs- och skrivbehörighet ges till följande registernyckel åt RMS-tjänstgruppen.
    På datorer där 32-bitarsversionen av Windows Server 2003 körs:
    `HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\1.0`
    På datorer där 64-bitarsversionen av Windows Server 2003 körs:
    `HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\DRMS\1.0`
