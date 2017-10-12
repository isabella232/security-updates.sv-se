---
TOCTitle: Lägga till och ta bort betrodda publiceringsdomäner
Title: Lägga till och ta bort betrodda publiceringsdomäner
ms:assetid: 'd87b502d-5497-4ccd-badf-f6807d587cee'
ms:contentKeyID: 18124908
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747687(v=WS.10)'
---

Lägga till och ta bort betrodda publiceringsdomäner
===================================================

Som standard kan RMS-servrar bara utfärda användarlicenser mot publiceringslicenser som utfärdats med en server i samma kluster som den aktuella servern. Om du har innehåll som publicerats med en annan rotcertifikatserver, antingen i din organisation, t.ex. en underorganisation i en annan skog, eller i en annan separat organisation, kan RMS-servern bevilja användare användarlicenser för innehållet om du konfigurerar en betrodd publiceringsdomän på RMS-servern. Genom att lägga till en betrodd publiceringsdomän upprättar du ett förtroende mellan RMS-servern och den andra rotcertifikatservern genom att importera den andra serverns serverlicensieringscertifikat. Det finns ingen gräns för hur många betrodda publiceringsdomäner du kan konfigurera för RMS-servern.

Du kan när som helst ta bort en betrodd publiceringsdomän från listan genom att ta bort certifikatet från listan över certifikat för betrodda publiceringsdomäner.

När du lägger till en betrodd publiceringsdomän importerar du serverlicensieringscertifikatet, den privata nyckeln (om den privata nyckeln skyddas av programvara och inte med en HSM) och alla principmallar för rättigheter för den RMS-server eller det RMS-kluster du vill lägga till. Administratören för servern eller klustret du vill skapa förtroende för måste exportera dessa objekt till en lösenordsskyddad fil och sedan ge dig ett lösenord så att du kan dekryptera filen. Administratören måste placera den filen i en delad mapp och meddela dig lösenordet. Du kan sedan importera filen genom att ange filens plats och lösenordet. Kontot där **administratörsprogrampoolen** körs måste ha behörigheter till den delade mappen för att filen ska kunna sparas.

Stegvisa instruktioner om hur du etablerar betrodda publiceringsdomäner finns i ”[Så här lägger du till en betrodd publiceringsdomän](https://technet.microsoft.com/731416d8-ddf4-4d4a-9f1a-bbd1ea48fe3c)” senare i det här avsnittet.

Om den privata nyckeln lagras i en HSM (Hardware Security Module) måste du först överföra den privata nyckeln till HSM:en på den betrodda servern. Information om hur du gör detta finns i dokumentationen som medföljde HSM:en. Beroende på vilken typ av HSM som används på de aktuella servrarna och på konfigurationen av HSM-enheterna är det inte säkert att du kan överföra den privata nyckeln från en HSM till en annan. Kontrollera dokumentationen som medföljde HSM:en om du vill ta reda på om det går att överföra den privata nyckeln utan att förlora några data på mål-HSM:en. Om det inte går att överföra den privata nyckeln korrekt går det inte att upprätta en betrodd publiceringsdomän mellan de aktuella servrarna.

| ![](images/Cc747687.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                      |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du skyddar den privata RMS-nyckeln med en HSM och du importerar ett serverlicensieringscertifikat från en RMS-installation där det programvarubaserade standardskyddet för privata nycklar används, måste du ange ett lösenord för den privata nyckeln på sidan Säkerhetsinställningar på varje RMS-server i klustret innan du importerar certifikatet. |
