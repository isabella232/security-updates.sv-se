---
TOCTitle: Säkerhetsgrupper i RMS
Title: Säkerhetsgrupper i RMS
ms:assetid: '25749a83-8c12-48ec-96ad-296d31fd55d4'
ms:contentKeyID: 18124648
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720215(v=WS.10)'
---

Säkerhetsgrupper i RMS
======================

Med RMS-installationsprogrammet skapas två grupper: RMS-tjänstgruppen och gruppen RM-ansvariga.

RMS-tjänstgruppen är en lokal säkerhetsgrupp som beviljas tillräckliga rättigheter för att komma åt alla resurser som krävs för driften av RMS. Vid installationen anger administratören ett användarkonto som ska användas som RMS-tjänstkonto. Detta användarkonto blir automatiskt medlem i RMS-tjänstgruppen och tilldelas därmed sina rättigheter. Vid normal drift körs i allmänhet RMS på det här användarkontot.

En annan viktig grupp i RMS är gruppen RM-ansvariga. Den här gruppen har full kontroll över allt innehåll, vilket innebär att en medlem i gruppen kan dekryptera alla filer med RMS-skyddat innehåll och ta bort allt RMS-skydd från dem. Gruppen RM-ansvariga har som standard inga medlemmar till en början, och RMS-administratörer ingår inte automatiskt i gruppen. Hur gruppen och dess medlemmar hanteras är av yttersta vikt för säkerheten för det RMS-skyddade innehållet. Mer information finns i ”Använda gruppen RM-ansvariga” i ”Använda en RMS-server”.
