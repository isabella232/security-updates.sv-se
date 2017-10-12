---
TOCTitle: Tillhandahålla redundans och belastningsutjämning
Title: Tillhandahålla redundans och belastningsutjämning
ms:assetid: '162d547c-78a7-4848-b43e-58e481832af2'
ms:contentKeyID: 18124634
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720199(v=WS.10)'
---

Tillhandahålla redundans och belastningsutjämning
=================================================

Du bör distribuera redundanta RMS-servrar i kluster för att garantera att användare kan hämta licenser och publicera innehåll när de behöver det. Du bör distribuera åtminstone ett rotcertifikatkluster som består av minst två servrar. Om du dessutom distribuerar en separat licensieringsserver som hanterar specifika licensieringsbehov hos enskilda grupper i organisationen bör du även distribuera licensieringsservern som ett kluster med minst två servrar.

De enskilda servrarna i rotcertifikatklustret och i eventuella licensieringskluster bildar tillsammans en "webbgrupp" med en gemensam URL eller virtuell adress. Om organisationen använder ett serverkluster kan du integrera RMS i den teknik du använder för virtuell adressering, t.ex. resursallokerings-DNS, tjänsten Utjämning av nätverksbelastning eller en maskinvarubaserad lösning.

Virtuell adressering möjliggör inte bara belastningsutjämning när det används tillsammans med RMS. Det förhindrar också att systemet blir beroende av en enda fysisk server för certifierings- och licensieringstjänster. Ingen användardator behöver ha direkt åtkomst till en enskild server i ett kluster.
