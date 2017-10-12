---
TOCTitle: 'Säkerhetskopiera och återställa RMS-systemet'
Title: 'Säkerhetskopiera och återställa RMS-systemet'
ms:assetid: 'c11f3ac1-e512-402b-bf13-9ff21f5fe745'
ms:contentKeyID: 18124890
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747745(v=WS.10)'
---

Säkerhetskopiera och återställa RMS-systemet
============================================

När du gör en plan för systemåterställning bör planen också innehålla lösningar för fel på databasservern och fel på någon av RMS-servrarna. Om det uppstår ett databasfel kan du återställa funktionerna i en RMS-server eller ett RMS-kluster från en säkerhetskopia av konfigurationsdatabasen. Du behöver inte hämta något nytt serverlicensieringscertifikat eller någon privat nyckel för RMS-servern eftersom de objekten redan finns lagrade i konfigurationsdatabasen.

Planera säkerhetskopiering av RMS-system
----------------------------------------

Förutom servernyckeln lagras användardata i konfigurationsdatabasen, bl.a. information om den offentliga nyckeln. Du skyddar viktiga nyckeldata genom att säkerhetskopiera konfigurationsdatabasen på ett medium och spara säkerhetskopian på en säker plats. Konfigurationsdatabasen för rotcertifikatklustret ändras ofta och du bör därför säkerhetskopiera den databasen regelbundet. Ju oftare nya användare läggs till i organisationen, desto mer frekvent bör du säkerhetskopiera databaserna. När du säkerhetskopierar rotcertifikatservern bör du kontrollera att tabellen **sysmessages** i huvuddatabasen inkluderas i säkerhetskopian. Om den tabellen inte innehåller några RMS-specifika meddelanden fungerar inte rotcertifikatservern. Du får då ett felmeddelande. Om tabellen inte finns med i säkerhetskopian kan du återskapa den genom att upprepa etableringsprocessen med en befintlig databas.

RMS-loggningsdatabasen innehåller loggar som kan visa intressanta felsökningsdata och statistiska data, men den är vanligtvis inte en kritisk del av RMS-systemet. Katalogtjänstdatabasen är en lokal kopia av Active Directory-databasen som sparas i cache-minnet, och den återskapas automatiskt när du återställer ett RMS-system. Kontakta SQL Server-administratören om du vill ha hjälp med att upprätta en plan för säkerhetskopiering av RMS-databaserna.

Om du skyddar de privata RMS-nycklarna med en HSM (Hardware Security Module) bör du också säkerhetskopiera HSM-konfigurationen. Mer information om hur du säkerhetskopierar och återställer HSM-konfigurationen finns i dokumentationen som medföljde HSM:en.

| ![](images/Cc747745.note(WS.10).gif)Obs!                                                                                                                                                                                                              |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Se till att det finns rutiner för nyckelhantering i organisationen (t.ex. för säkerhetskopiering och återställande) innan du krypterar de privata RMS-nycklarna med någon annan programvarubaserad CSP (Cryptographic Service Provider) än den programvarubaserade standard-CSP:n. |

Planera återställning av RMS-system
-----------------------------------

Om du återställer en databasserver från en säkerhetskopia ska du se till att den version av RMS som körs är samma version som kördes när säkerhetskopian skapades. Informera användarna i RMS-systemet om att om de började använda RMS-systemet efter det datum då säkerhetskopian gjordes måste de skaffa ett nytt rättighetskontocertifikat. Inget skyddat innehåll går förlorat.

Om du vill återställa en enda RMS-server från ett kluster ska du bygga om servern, installera om RMS och koppla ihop servern med klustret med hjälp av den befintliga databasen. Den här aktiviteten påverkar inte användarna i RMS-systemet eftersom servrarna i klustret fungerar som en enda server.
