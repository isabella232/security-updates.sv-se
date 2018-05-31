---
TOCTitle: Implementera återkallning
Title: Implementera återkallning
ms:assetid: '4735f060-7197-4ae2-830a-f91bcc4de30a'
ms:contentKeyID: 18124709
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747554(v=WS.10)'
---

Implementera återkallning
=========================

Certifikat och licenser kan återkallas med alla enheter som ingår i certifikatets eller licensens förtroendekedja. Alla certifikat och licenser som har utfärdats med en rotcertifikatserver kan återkallas med den rotcertifikatservern. Dessutom kan certifikaten återkallas av en tredje part om en sådan utses av RMS-administratören.

Om du vill återkalla ett certifikat eller en licens som har utfärdats med en RMS-server skapar du och distribuerar en lista över återkallade certifikat och använder sedan listan i en principmall för rättigheter. Gör så här:

1.  Skapa en lista över återkallade certifikat som anger vilka enheter som ska återkallas. Listan är en oformaterad textfil i XML-format med XrML-kod. Mer information finns i ”[Skapa listor över återkallade certifikat](https://technet.microsoft.com/1ef75199-3344-4225-84de-a863a777696a)” senare i det här avsnittet.
2.  Generera ett nyckelpar för listan. Signera sedan filen med den privata nyckeln med hjälp av verktyget Revocation List Signing som är framtaget för detta syfte. Instruktioner finns i ”Infoga en signatur i en lista över återkallade certifikat”. Du bör automatisera den här processen så att den genomförs regelbundet – helst varje dag.
3.  Placera filen med listan över återkallade certifikat på en plats där användare som vill använda den kan komma åt den. Du bör placera filen på en plats som går att komma åt både inifrån nätverket och via Internet, gärna på en webbplats. Det garanterar att användare kommer åt filen både inifrån företagets nätverk och när de inte kommer åt nätverket.
4.  Skapa en principmall för rättigheter som innehåller krav på en lista över återkallade certifikat. Mer information finns i ”[Skapa och ändra principmallar för rättigheter](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)” senare i det här avsnittet.

Du kan också återkalla rotcertifikatserverns serverlicensieringscertifikat. Eftersom det certifikatet har utfärdats av Microsoft registreringstjänst kan Microsoft återkalla rotcertifikatserverns serverlicensieringscertifikat. Det sker genom att Microsoft lägger till det aktuella serverlicensieringscertifikatet i Microsofts lista över återkallade certifikat och sedan publicerar listan.

Dessutom kan rotcertifikatserverns serverlicensieringscertifikat återkallas av en tredje part om RMS-administratören valde att aktivera det alternativet under etableringen. Om alternativet har aktiverats måste en lista över återkallade certifikat som omfattar det serverlicensieringscertifikat som har signerats med denna tredje parts privata nyckel göras tillgänglig för klienterna. Mer information finns i ”[Återkalla serverlicensieringscertifikat](https://technet.microsoft.com/8020861d-d196-4431-8282-044675ef5616)” senare i det här avsnittet.

| ![](images/Cc747554.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Var försiktig när du implementerar återkallningar. Du måste förnya listan med jämna mellanrum baserat på det uppdateringsintervall som du anger. I annat fall upphör den automatiskt att gälla, vilket hindrar användare från att använda innehåll som är beroende av listan. Utvärdera uppdateringsintervallet för listan över återkallade certifikat noggrant så att du inte av misstag hindrar användarna från att använda innehåll. Kontrollera också att användarna kommer åt filen både inifrån företagets nätverk och när de inte kommer åt nätverket. Mer information finns i ”[Definiera principer för återkallning](https://technet.microsoft.com/e2fffe9f-def7-439b-a8aa-43f8a065813d)” tidigare i det här avsnittet. |
