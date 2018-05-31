---
TOCTitle: Definiera krav för nyckelhantering
Title: Definiera krav för nyckelhantering
ms:assetid: 'f0e08fb8-bf5e-4278-a09f-daa57696e786'
ms:contentKeyID: 18124963
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747797(v=WS.10)'
---

Definiera krav för nyckelhantering
==================================

I RMS skyddas och kontrolleras rättigheter till innehåll med hjälp av krypteringsnycklar. Krypteringsnycklarna är de informationsgrundstenar som gör det möjligt för systemet att fungera sömlöst och säkert. Administratören måste hantera dessa nycklar på ett korrekt sätt och skydda dem från dataförlust, systemfel och stöld.

I standardkonfigurationen lagras servernyckelparet med tillhörande GUID i en tabell i konfigurationsdatabasen. Servernyckelparet krypteras med ett lösenord som du väljer under etableringsprocessen.

Du skyddar servernyckelparet och GUID genom att säkerhetskopiera konfigurationsdatabasen till ett lagringsmedium (t.ex. en CD) och sedan spara mediet med säkerhetskopian på en säker plats (t.ex. i ett kassaskåp på annan plats). Hur ofta du behöver göra säkerhetskopior beror både på hur ofta du gör administrativa justeringar och vilken risknivå ni accepterar för dataförlust orsakad av medieförsämringar och andra medieproblem. Kontrollera att du kan avgöra vilket lösenord som ska användas till den privata nyckeln i den säkerhetskopierade databasen. Utan rätt lösenord kan du inte återställa säkerhetskopian på RMS-servern.

Om du använder SQL Server som databasserver kan du använda SQL Server Enterprise Manager till att kopiera värdet för den krypterade nyckelinformationen direkt till en skyddad diskett eller något annat medium. Eftersom den privata nyckeln är skyddad måste RMS-installationen köras under samma RMS-tjänstkonto som när säkerhetskopieringen gjordes, om du återställer den från ett säkert medium till en RMS-installation.

Om du skyddar serverns privata nyckel med en programvarubaserad eller maskinvarubaserad CSP måste du säkerhetskopiera nyckelbehållaren och nyckeln manuellt. När du använder en HSM höjer du skyddsnivån för privata nycklar eftersom de lagras i en maskinvara som inte kan utsättas för programvarubaserade attacker. Data som behöver dekrypteras eller signeras skickas till HSM:en, dekrypteras eller signeras och skickas sedan vidare.

För varje CSP, vare sig den är maskin- eller programvarubaserad, finns särskilda procedurer för säker säkerhetskopiering av nyckeln. Om du är osäker på vad som gäller bör du se efter i CSP-dokumentationen.
