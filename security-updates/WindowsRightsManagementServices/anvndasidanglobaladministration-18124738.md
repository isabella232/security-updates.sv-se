---
TOCTitle: Använda sidan Global administration
Title: Använda sidan Global administration
ms:assetid: '57bbf402-2351-4dee-823c-27f4dd32447c'
ms:contentKeyID: 18124738
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747575(v=WS.10)'
---

Använda sidan Global administration
===================================

Från sidan **Global administration** på administrationswebbplatsen kan du etablera och ta bort RMS-servrar samt ändra RMS-tjänstkontot.

Webbsidan är tillgänglig från den server som du vill administrera. Gör så här:

1.  Logga in som en lokal administratör.
2.  Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS**.

Det går inte att komma åt sidan **Global administration** från en webbläsare på en fjärrdator.

Om du inte har etablerat den server som du besöker sidan **Global administration** från visas följande alternativ för alla webbplatser som körs på servern:

-   **Etablera RMS på den här webbplatsen**. Klicka på den här länken om den aktuella servern är den första server som du vill etablera i klustret. Det här startar etableringsprocessen där nödvändiga RMS-resurser, t.ex. virtuella kataloger, installeras. Dessutom installeras databaserna på databasservern. Mer information finns i ”[Så här etablerar du den första rotcertifikatservern](https://technet.microsoft.com/debc42f3-74ff-4c99-b7a4-4921fccdabc2)” senare i det här avsnittet.
-   **Lägg till den här servern i ett kluster**. Klicka på den här länken om du vill etablera servern och lägga till den i ett befintligt kluster. Du kan koppla en server till ett rotcertifikatkluster eller ett licensieringskluster. RMS-resurserna, t.ex. virtuella kataloger, installeras. Däremot skapas inte några databaser eftersom klusterdatabaserna kommer att användas i servern. Mer information finns i ”[Så här lägger du till en server i ett kluster](https://technet.microsoft.com/db635238-5528-4bec-9cc6-8244e2b3d733)” senare i det här avsnittet.

Om du ansluter till sidan **Global administration** från en server som redan har etablerats visas följande alternativ:

-   **Administrera RMS på den här webbplatsen.**Klicka på den här länken om du vill visa sidan Klusteradministration. Mer information finns i ”[Använda administrationshemsidan](https://technet.microsoft.com/6c155977-bd0e-47d6-ac65-1746cddb505e)” senare i det här avsnittet.
-   **Ändra RMS-tjänstkonto.**Klicka på den här länken om du vill ange ett annat RMS-tjänstkonto som RMS ska köras under. Mer information finns i ”[Ändra RMS-tjänstkontot](https://technet.microsoft.com/f257d66d-b823-41e4-bcb7-7c90eb295238)” senare i det här avsnittet.
-   **Ta bort RMS från den här webbplatsen.** Klicka på den här länken om du vill ta bort RMS. När du tar bort RMS tas virtuella RMS-kataloger och program bort från servern men RMS avinstalleras inte. Mer information finns i ”[Så här avinstallerar du RMS](https://technet.microsoft.com/885e3b4f-ea32-466f-9f7f-d8440b0f7c28)” senare i det här avsnittet.

| ![](images/Cc747575.note(WS.10).gif)Obs!                                                                                                                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| På webbplatsen Administration av RMS används popup-fönster för konfiguration av vissa funktioner. Om du använder blockering av popup-fönster tillsammans med webbläsaren bör du konfigurera webbläsarinställningarna så att popup-fönster tillåts på webbplatsen Administration av RMS. |
