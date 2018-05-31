---
TOCTitle: Så här spårar du rättighetskontocertifikat
Title: Så här spårar du rättighetskontocertifikat
ms:assetid: 'f9efac9f-c725-4bce-a89f-7691b0d8ffc0'
ms:contentKeyID: 18124985
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747752(v=WS.10)'
---

Så här spårar du rättighetskontocertifikat
==========================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Den här funktionen är endast tillgänglig i rotcertifikatklustret. Den är inte tillgänglig i några licensieringsservrar eller licensieringskluster.

Den här processen kan bara användas till att beräkna antalet användarlicenser och är bara användbar för debiterbara licenser. Det är ett beräknat antal som visas på sidan Certifieringsrapport för RM-konto. Om du inte har uppdaterat konfigurationsdatabasen och tagit bort användare som inte längre är aktiva stämmer inte det här antalet. Om du dessutom har användare som har fått flera licenser utfärdade i flera skogar ingår inte dessa ytterligare licenser i antalet som visas.

Spåra rättighetskontocertifikat
-------------------------------

#### Så här spårar du rättighetskontocertifikat

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill spåra certifikat.

2.  Klicka på Certifieringsrapport för RM-konto vid **Administrationslänkar**.

3.  Under **Totalt antal certifierade användare** kontrollerar du hur många användare som har fått rättighetskontocertifikat från det aktuella rotcertifikatklustret.

Mer information finns i ”[Spåra rättighetskontocertifikat](https://technet.microsoft.com/5bb0f3cf-fc44-4e60-a93f-c789d6f8a902)” tidigare i det här avsnittet.
