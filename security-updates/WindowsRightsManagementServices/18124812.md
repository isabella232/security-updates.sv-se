---
TOCTitle: Så här inaktiverar du RMS
Title: Så här inaktiverar du RMS
ms:assetid: '8b563c25-17cd-4b9b-ae42-695497ab6439'
ms:contentKeyID: 18124812
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747665(v=WS.10)'
---

Så här inaktiverar du RMS
=========================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

| ![](images/Cc747665.Warning(WS.10).gif)Varning!                                                    |
|---------------------------------------------------------------------------------------------------------------------------------|
| Det går inte att återställa en inaktiverad server till en standard-RMS-konfiguration. Det går inte att ångra den här processen. |

| ![](images/Cc747665.Warning(WS.10).gif)Varning!                                                                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| När du har inaktiverat RMS måste du ta bort det fullständigt genom att klicka på Lägg till eller ta bort program innan du försöker installera en ny förekomst av RMS. |

Inaktivera RMS
--------------

#### Så här inaktiverar du RMS

1.  Logga in på den server där du vill inaktivera RMS.

2.  Öppna sidan **Global administration** och klicka sedan på länken **Administrera RMS på den här webbplatsen**.

3.  Klicka på länken **Säkerhetsinställningar** på sidan **Hemsida för Global administration**.

4.  Markera kryssrutan **Inaktiverar RMS-installationen** vid **Inaktivera RMS** och klicka sedan på **Inaktivera**.

5.  Klicka på **OK** när du blir ombedd att bekräfta att du permanent vill inaktivera RMS-installationen.
