---
TOCTitle: 'Ändra RMS-tjänstkontots lösenord'
Title: 'Ändra RMS-tjänstkontots lösenord'
ms:assetid: '435c9cef-b622-48b3-9d4d-4bf5cac7d52d'
ms:contentKeyID: 18124719
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720273(v=WS.10)'
---

Ändra RMS-tjänstkontots lösenord
================================

Beroende på vilken lösenordsprincip som du angav för RMS-servrarna kan RMS-tjänstkontots lösenord upphöra att gälla efter en tid. När lösenordet upphör att gälla fungerar inte RMS. Därför måste du ändra lösenordet innan det upphör att gälla.

**Använda ett RMS-tjänstkonto**

När du använder ett RMS-tjänstkonto ändrar du lösenordet på varje RMS-server på följande sätt:

1.  Om servern finns i ett kluster ser du till att den inte används av systemet.
2.  Logga in på servern med inloggningsuppgifterna för RMS-tjänstkontot.
3.  Ändra RMS-tjänstkontots lösenord.
    Tjänster som körs på andra servrar som använder samma RMS-tjänstkonto kommer att sluta att fungera eftersom de referenser som dessa servrar använder inte längre är giltiga.
4.  Logga ut från servern.
5.  Logga in på servern igen som RMS-administratör.
6.  Konfigurera om användar-ID:t på servern genom att klicka på **Ändra RMS-tjänstkonto** på sidan **Global administration** och ange sedan domän, användarnamn och lösenord på sidan **Ändra RMS-tjänstkonto**.
7.  Starta om IIS.
8.  Anslut servern till systemet igen, om det är aktuellt.
9.  Upprepa steg 6 till 8 för varje server i klustret.

Det här är det enklaste sättet att ändra RMS-tjänstkontots lösenord. Det kan dock resultera i en viss tids avbrott för RMS medan Active Directory uppdateras med det nya lösenordet när du ändrar RMS-tjänstkontots lösenord på en server. Programpoolerna startas om med jämna mellanrum i IIS. De programpooler som körs med de gamla referenserna kommer inte att kunna startas förrän du har ändrat RMS-tjänstkontots lösenord och startar om IIS på den aktuella servern. RMS fungerar inte förrän programpoolerna körs igen.

**Använda två RMS-tjänstkonton**

Med den här metoden skapar du först två RMS-tjänstkonton med olika principer för förfallodatum eller datum. Under normal drift körs RMS med det första kontot. När du vill ändra det första tjänstkontots lösenord utför du stegen nedan på varje RMS-server:

1.  Om servern finns i ett kluster ser du till att den inte används av systemet.
2.  Ange att RMS ska köras under det andra RMS-tjänstkontot. Instruktioner om hur du ändrar kontot finns i ”[Ändra RMS-tjänstkontot](https://technet.microsoft.com/f257d66d-b823-41e4-bcb7-7c90eb295238)” senare i det här avsnittet.
3.  Starta om IIS.
4.  Anslut servern till systemet igen, om det är aktuellt.

När alla RMS-servrar använder det andra RMS-tjänstkontot kan du ändra lösenordet till det första RMS-tjänstkontot utan att det påverkar driften av RMS-systemet. Genom att på det här sättet byta mellan två konton undviker du driftavbrott för RMS.
