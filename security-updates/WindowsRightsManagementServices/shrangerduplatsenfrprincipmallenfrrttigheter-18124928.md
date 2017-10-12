---
TOCTitle: Så här anger du platsen för principmallen för rättigheter
Title: Så här anger du platsen för principmallen för rättigheter
ms:assetid: 'e1bee46d-33db-424f-ba45-1dcedcb883ab'
ms:contentKeyID: 18124928
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747781(v=WS.10)'
---

Så här anger du platsen för principmallen för rättigheter
=========================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Om du lagrar principmallar för rättigheter i en delad mapp och sedan ändrar plats för mappen måste du kopiera principmallarna för rättigheter manuellt från den gamla platsen till den nya.

Principmallar för rättigheter lagras också i konfigurationsdatabasen. Mer information om hur du distribuerar principmallar för rättigheter finns i ”[Distribuera principmallar för rättigheter](https://technet.microsoft.com/ae6fa26f-d744-4ac9-9eb1-728ffab87bfe)” tidigare i det här avsnittet.

Om du använder Microsoft Office 2003 som RMS-aktiverat program styrs placeringen av principmallar för rättigheter av registernyckeln `AdminTemplatePath`. RMS-klienten försöker då att hitta mallar på den plats som angetts i registernyckeln och inte på någon annan platser.

Ange platsen för principmallen för rättigheter
----------------------------------------------

#### Så här anger du platsen för principmallen för rättigheter

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill ange platsen för principmallar för rättigheter.

2.  Klicka på **Principmallar för rättigheter** vid **Administrationslänkar**.

3.  Ange UNC:n (Universal Naming Convention) till en delad mapp vid **Mallplats** där principmallarna för rättigheter för det aktuella klustret ska lagras. Använd formatet \\\\*servernamn*\\*resursnamn*. Kontot som **administratörsprogrampoolen** körs med måste ha skrivbehörighet till den delade mappen. Kontrollera att mallarna har lagrats på en plats som är tillgänglig från nätverket och att platsen uppfyller organisationens riktlinjer för säkerhet. Delade mappar för mallar bör inte skapas i de kärnmappar som används i RMS, t.ex. mapparna Program och IISRoot.

4.  Klicka på **Spara**.

5.  När du har skapat principmallar för rättigheter och sparar dem på den aktuella platsen måste de göras tillgängliga för användarna. Som standard söker RMS-klienten efter principmallar för rättigheter på följande plats på datorn:

    %HOMEPATH%\\Local Settings\\Application Data\\Microsoft\\DRM\\templates

    Principmallarna för rättigheter bör kopieras från den plats som anges i steg 3 till den här platsen av alla användare i organisationen som ska använda RMS.
