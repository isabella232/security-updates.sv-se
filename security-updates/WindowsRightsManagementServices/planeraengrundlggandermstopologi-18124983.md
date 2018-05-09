---
TOCTitle: 'Planera en grundläggande RMS-topologi'
Title: 'Planera en grundläggande RMS-topologi'
ms:assetid: 'fec3201e-201f-4faf-910e-fa44132af83d'
ms:contentKeyID: 18124983
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747755(v=WS.10)'
---

Planera en grundläggande RMS-topologi
=====================================

Den grundläggande RMS-topologin utgörs av en eller flera fysiska servrar som fungerar som ett rotcertifikatkluster. Detta kluster används för certifiering, licensiering och publicering i organisationen. För alla distributioner utom de allra minsta konfigureras normalt flera fysiska servrar i ett kluster bakom en enda URL. Klustret skapas genom att den första servern etableras som rotcertifikatserver. Därefter läggs resten av servrarna till i klustret tills du har nått den nivå av rotcertifikatservrar som krävs för att hantera den beräknade aktiviteten. I följande figur illustreras denna topologi.

![](images/Cc747755.a3332719-4d25-4694-a89a-7c31fd97ca3b(WS.10).gif "Grundläggande topologi")

När du ansluter servrar till ett kluster delar de samma konfigurations- och loggningsdatabaser, vilka är SQL Server-databaser. SQL Server kan antingen finnas på rotcertifikatservern eller på en separat server.

Belastningsutjämning konfigureras på alla servrar i rotcertifikatklustret. Alla certifikatbegäran och licensbegäran skickas till rotcertifikatklustret via den gemensamma URL som du anger vid konfigurationen av den första servern i klustret.

Om systemet ska hantera en litet antal klienter kan du konfigurera RMS på en enskild server med en lokal databas. Denna server används för all certifiering och licensiering i organisationen. Konfigurationen innebär dock att ett enskilt serverfel påverkar hela systemet. Var därför noga med att säkerhetskopiera systemet regelbundet.
