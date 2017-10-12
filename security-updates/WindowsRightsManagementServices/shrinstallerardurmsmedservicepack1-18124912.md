---
TOCTitle: Så här installerar du RMS med Service Pack 1
Title: Så här installerar du RMS med Service Pack 1
ms:assetid: 'dab20175-a690-43f8-b943-768d289daa0d'
ms:contentKeyID: 18124912
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747689(v=WS.10)'
---

Så här installerar du RMS med Service Pack 1
============================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Datorn som du installerar RMS på måste antingen vara en medlemsserver i en domän eller en domänkontrollant. Det går inte att distribuera RMS på en fristående server i en arbetsgrupp.

| ![](images/Cc747689.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Etablera inte RMS på några andra servrar förrän du har slutfört både installationen och etableringen av den första rotcertifikatservern. Instruktioner finns i ”[Så här etablerar du den första rotcertifikatservern](https://technet.microsoft.com/debc42f3-74ff-4c99-b7a4-4921fccdabc2)”, ”[Så här etablerar du en licensieringsserver](https://technet.microsoft.com/4d67b898-0ba9-4eef-ab7d-ee0ca55a688e)” och ”[Så här lägger du till en server i ett kluster](https://technet.microsoft.com/db635238-5528-4bec-9cc6-8244e2b3d733)” senare i det här avsnittet. |

| ![](images/Cc747689.Important(WS.10).gif)Viktigt!                                                                                                                                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RMS SP1 kan installeras på en server där den föregående versionen av RMS körs. Om du däremot har inaktiverat RMS måste RMS tas bort fullständigt med Lägg till eller ta bort program innan du försöker installera RMS SP1. |

Installera RMS med Service Pack 1
---------------------------------

#### Så här installerar du RMS med Service Pack 1

1.  Logga in med ett domänkonto som är medlem av den lokala administratörsgruppen på den server där du vill installera RMS SP1.

2.  Kontrollera listan med programvara som ska installeras när dialogrutan **Välkommen** visas och klicka sedan på **Nästa**.

3.  Kontrollera innehållet i dialogrutan **Licensavtal**, välj **Jag accepterar** och klicka sedan på **Nästa**.

4.  Acceptera standardplatsen eller ange en ny plats i **Mapp** och klicka sedan på **Nästa**.

5.  Klicka på **Installera** i dialogrutan **Bekräfta installationen** och starta installationen.

6.  Klicka på **Stäng** när dialogrutan **Installationen är slutförd** visas.

    | ![](images/Cc747689.note(WS.10).gif)Obs!                                                  |
    |------------------------------------------------------------------------------------------------------------------------|
    | Uppdatera sidan **Global administration** i Microsoft Internet Explorer om felmeddelandet Programmet startar om visas. |

Du kan också installera RMS från kommandotolken. Instruktioner finns i ”[RMS-serverinstallation via kommandotolken](https://technet.microsoft.com/b55b1e2a-dd14-4168-a37f-9cdedbec660b)” senare i det här avsnittet.
