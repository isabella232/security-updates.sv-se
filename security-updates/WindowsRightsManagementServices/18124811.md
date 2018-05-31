---
TOCTitle: Så här avinstallerar du RMS
Title: Så här avinstallerar du RMS
ms:assetid: '885e3b4f-ea32-466f-9f7f-d8440b0f7c28'
ms:contentKeyID: 18124811
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747587(v=WS.10)'
---

Så här avinstallerar du RMS
===========================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Avinstallera RMS
----------------

#### Så här avinstallerar du RMS

1.  Logga in på den server som du vill avinstallera RMS från.

    | ![](images/Cc747587.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                 |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Om du avinstallerar RMS från en server i rotcertifikatklustret måste du först ta bort etableringen av den genom att klicka på **Ta bort RMS från den här webbplatsen** på sidan **Global administration**. Du behöver inte ta bort etableringen av en licensieringsserver innan du avinstallerar RMS från den. |

2.  Öppna **Lägg till eller ta bort program** på **Kontrollpanelen**.

3.  I dialogrutan **Lägg till eller ta bort program** klickar du på **Windows Rights Management Services** och sedan på **Ta bort**, så tas RMS SP1 bort.
