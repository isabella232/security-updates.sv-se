---
TOCTitle: 'Planera en distribuerad RMS-topologi'
Title: 'Planera en distribuerad RMS-topologi'
ms:assetid: '8773a1e0-6ac3-41f5-9866-5890cef08d04'
ms:contentKeyID: 18124800
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747657(v=WS.10)'
---

Planera en distribuerad RMS-topologi
====================================

I vissa situationer kan du behöva distribuera en eller flera licensieringsservrar som inte ingår i rotcertifikatklustret. Normalt används det här till att hantera avdelningar med direkt kontroll över utfärdandet av såväl publicerings- som användarlicenser, t.ex. juridiska avdelningar där särskilda säkerhetskrav kan motivera kontroll på avdelningsnivå. Rotcertifikatklustret tillhandahåller kontocertifieringstjänster för licensieringsservrarna. Kombinationen med ett rotcertifikatkluster och en eller flera licensieringsservrar kallas för en distribuerad topologi.

Observera att licensieringsservrar kan distribueras i ett kluster, på samma sätt som rotcertifikatservern. Och precis som i ett rotcertifikatkluster används en egen tjänst för belastningsutjämning i licensieringskluster. Alla licensierade servrar och licensieringskluster använder en separat SQL Server-instans till att tillhandahålla konfigurations- och loggningsdatabaser för den aktuella servern eller det aktuella klustret.

Även om du kan konfigurera Windows RMS-installationen så att endast certifieringstjänsterna körs från rotinstallationen, eller så att hela licensieringstjänsten körs från en eller flera licensieringsservrar eller ett eller flera licensieringskluster, så är inte det den normala konfigurationen. Normalt ökar du antalet servrar i rotcertifikatklustret så att prestanda- och redundanskrav tillgodoses i stället för att distribuera fler licensieringsservrar (såvida du inte konfigurerar stöd för licensiering på avdelningsnivå). Följande diagram illustrerar denna topologi.

![](images/Cc747657.01fa5a85-5711-41aa-932a-124049d34186(WS.10).gif)

Om du skapar en distribuerad topologi kan det leda till ökade administrativa kostnader i organisationen eftersom en distribuerad topologi är mer komplex. Om organisationen har flera licensieringskluster och skogar kan du behöva åsidosätta vissa registernycklar på RMS-klientdatorerna så att de begär licensiering från rätt RMS-server. Dessutom kan det uppstå förtroendeproblem mellan domänerna. På grund av det måste du konfigurera domänerna ytterligare för att aktivera användandet av RMS-skyddat innehåll.

Anslutningspunkter för tjänster i en distribuerad topologi
----------------------------------------------------------

När du etablerar en RMS-server läggs en kluster-URL till i en anslutningspunkt för tjänsten i Active Directory-skogen. Det finns en anslutningspunkt för rotcertifikatklustret och en för varje licensieringskluster som du har etablerat i skogen. Anslutningspunkten måste registreras för rotcertifikatklustret innan du etablerar ett licensieringskluster. När du etablerar licensieringsklustret använder underregistreringsprocessen den aktuella URL:en till att söka efter rotcertifikatklustret i nätverket och hämta ett serverlicensieringscertifikat.

Om du distribuerar ett rotcertifikatkluster i stället för en enskild rotcertifikatserver måste det gå att nå alla servrar i klustret (via en virtuell adress) med en gemensam URL.

Det finns många olika sätt att implementera virtuell adressering, t.ex. resursallokerings-DNS, tjänsten Utjämning av nätverksbelastning, maskinvarubaserade lösningar m.fl. Med virtuell adressering får du tillgång till belastningsutjämning mellan servrarna samtidigt som systemet inte blir beroende av en enda server för licensiering och publicering.

I RMS används den gemensamma URL:en för licensförvärv och för det publicerade värde som används i användardatorer vid sökning efter RMS-klustret i Active Directory eller i registret. Ingen användardator behöver ha direkt åtkomst till en enskild server i ett kluster.
