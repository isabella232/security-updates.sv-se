---
TOCTitle: Använda administrationshemsidan
Title: Använda administrationshemsidan
ms:assetid: '6c155977-bd0e-47d6-ac65-1746cddb505e'
ms:contentKeyID: 18124759
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720290(v=WS.10)'
---

Använda administrationshemsidan
===============================

Från **administrationshemsidan** kan du visa information om servern och klustret och komma åt administrativa alternativ. Den här sidan är bara tillgänglig om servern har etablerats.

Webbsidan är tillgänglig från den server som du vill administrera. Gör så här:

1.  Logga in som lokal administratör.
2.  Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS**.
3.  Klicka på **Administrera RMS på den här webbplatsen** på sidan **Global administration**.

Om du har aktiverat fjärradministration med SSL (Secure Sockets Layer) kan du även komma åt **administrationshemsidan** från en annan dator. Gör så här:

1.  Skriv in följande URL i webbläsarens adressfält:
    https://*klustrets\_namn:portnummer*/\_wmcs/admin
    *klustrets\_namn:portnummer* är den URL som du angav för klustret under etableringen. Ange bara portnumret i de fall då du angett ett annat portnummer än standardporten (80).
2.  Skriv in referenserna för en lokal administratör på den aktuella servern när du ombeds att göra det.

**Administrationshemsidan** innehåller information om klustret, t.ex. kluster-URL:en, konfigurationsdatabasens namn och plats, serverlicensieringscertifikatets förfallodatum o.s.v. Här finns också länkar till sidor där du konfigurerar följande administrativa alternativ för klustret:

-   **Principer för förtroenden.**Lägga till och ta bort betrodda domäner. Mer information finns i ”[Hantera förtroenden och principer för förtroenden](https://technet.microsoft.com/1c96ee74-fd28-4511-be21-087e2b04c3ee)” senare i det här avsnittet.
-   **Principmallar för rättigheter**. Skapa och ändra principmallar för rättigheter. Mer information finns i ”[Hantera principmallar för rättigheter](https://technet.microsoft.com/718286dc-3399-4556-96c9-ec3a33d31877)” senare i det här avsnittet.
-   **Loggningsinställningar**. Aktivera och inaktivera loggning och visa namnet på loggningsservern och databasen. Mer information finns i ”[Hantera loggning](https://technet.microsoft.com/8fccfc57-2135-494e-8e44-f6191bf5e4a0)” senare i det här avsnittet.
-   **Inställningar för extranätets kluster-URL.**Ange en externt tillgänglig URL för begäran om licensiering och kontocertifiering. Mer information finns i ”[Konfigurera en extranät-URL](https://technet.microsoft.com/88fec9ff-c96c-4d20-8856-0485e7507572)” senare i det här avsnittet.
-   **RMS-proxyinställningar.**Ange proxyserverns adress, aktuell autentiseringstyp och det användarnamn som ska användas när RMS-servern ansluter till Internet via en proxyserver. Mer information finns i ”[Konfigurera RMS-proxyinställningar](https://technet.microsoft.com/179d2970-62e9-4487-aa5b-f4334234991e)” senare i det här avsnittet.
-   **Säkerhetsinställningar.**Återställ lösenordet för serverns privata nyckel, definiera gruppen RM-ansvariga vars medlemmar kan dekryptera allt licenserat innehåll samt inaktivera RMS. Mer information finns i ”[Hantera säkerhet vid RMS-användning](https://technet.microsoft.com/62050812-de4f-4392-8d63-f2f89aa01ed4)” senare i det här avsnittet.
-   **Certifieringsinställningar.**Ange giltighetstid för rättighetskontocertifikat och ange en administrativ kontakt. (Det här alternativet är bara tillgängligt i rotcertifikatklustret, inte på licensieringsservrar.) Mer information finns i ”[Hantera rättighetskontocertifikat](https://technet.microsoft.com/49c5c2ba-e197-4e4b-b3b3-b3248f068bcc)” senare i det här avsnittet.
-   **Exkluderingsprinciper.**Ange exkludering baserat på lockbox-version, rättighetskontocertifikat, Windows-version eller RMS-aktiverat program. Mer information finns i ”[Hantera exkluderingsprinciper](https://technet.microsoft.com/ee31e099-e095-4648-95da-0009fbeb48cb)” senare i det här avsnittet.
-   **Certifieringsrapport för RM-konto.**Visa hur många rättighetskontocertifikat som har utfärdats. (Det här alternativet är bara tillgängligt i rotcertifikatklustret, inte på licensieringsservrar.) Mer information finns i ”[Spåra rättighetskontocertifikat](https://technet.microsoft.com/5bb0f3cf-fc44-4e60-a93f-c789d6f8a902)” senare i det här avsnittet.

Följande delar i det här avsnittet beskriver hur du använder de här funktionerna. Stegvisa instruktioner finns i ”[Så här gör du i RMS](https://technet.microsoft.com/82032075-f361-438f-a2c4-93ab29ae6cff)” senare i det här avsnittet.

| ![](images/Cc720290.note(WS.10).gif)Obs!                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| På webbplatsen Administration av RMS används popup-fönster för konfiguration av vissa funktioner. Om du använder blockering av popup-fönster tillsammans med webbläsaren bör du konfigurera webbläsarinställningarna så att popup-fönster tillåts på webbplatsen Administration av RMS. |
