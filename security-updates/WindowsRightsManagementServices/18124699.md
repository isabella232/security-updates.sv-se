---
TOCTitle: 'Registrera RMS-tjänstens anslutningspunkt'
Title: 'Registrera RMS-tjänstens anslutningspunkt'
ms:assetid: '446d83ec-3224-45e2-9697-625e7db338f3'
ms:contentKeyID: 18124699
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720260(v=WS.10)'
---

Registrera RMS-tjänstens anslutningspunkt
=========================================

Med RMS-tjänstens anslutningspunkt (SCP) identifieras anslutnings-URL:en till tjänsten för alla RMS-aktiverade klienter i organisationen. Inga klienter kan använda RMS eller begära användar- och publiceringslicenser eller rättighetskontocertifikat utan en giltig anslutningspunkt för tjänsten.

Du kan registrera anslutningspunktens URL till rotcertifikatklustret från sidan **RMS-tjänstens anslutningspunkt** på administrationswebbplatsen. Du kan också avregistrera anslutningspunktens URL från sidan **RMS-tjänstens anslutningspunkt** om du av någon anledning vill återställa URL:en. Du måste vara inloggad med ett giltigt domänanvändarkonto som har tillräckliga behörigheter att skapa ett behållarobjekt under tjänstbehållaren, för att registrera och avregistrera anslutningspunktens URL.

Under tjänstbehållaren i Active Directory skapas ett nytt behållarobjekt med namnet RightsManagementServices. Under denna behållare skapas ett SCP-objektet med namnet MSRMRootCluster. Det SCP-objektet har två värden för attributet Keywords:

-   MSRMRootCluster
-   1.0

De här attributen används av klienter och andra servrar till att hitta URL:en till rotklustret i Active Directory. SCP-objektets serviceBindingInformation innehåller URL:en till rotklustret, i formatet http://*klusternamn*/\_wmcs/Certification.
