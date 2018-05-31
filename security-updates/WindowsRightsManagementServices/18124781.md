---
TOCTitle: Så här lägger du till en betrodd publiceringsdomän
Title: Så här lägger du till en betrodd publiceringsdomän
ms:assetid: '731416d8-ddf4-4d4a-9f1a-bbd1ea48fe3c'
ms:contentKeyID: 18124781
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747624(v=WS.10)'
---

Så här lägger du till en betrodd publiceringsdomän
==================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Om du skyddar den privata RMS-nyckeln med en HSM och du importerar ett serverlicensieringscertifikat från en RMS-installation där det programvarubaserade standardskyddet för privata nycklar används, måste du ange ett lösenord för den privata nyckeln på sidan **Säkerhetsinställningar** på varje RMS-server i klustret innan du importerar certifikatet.

Lägga till en betrodd publiceringsdomän
---------------------------------------

#### Så här lägger du till en betrodd publiceringsdomän

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill lägga till en betrodd publiceringsdomän.

2.  Klicka på **Principer för förtroenden** vid **Administrationslänkar**.

3.  Klicka på **Bläddra** vid **Betrodda publiceringsdomäner**. Leta reda och dubbelklicka på certifikatet för den publiceringsdomän som du vill lägga till. Skriv in lösenordet som krävs för att dekryptera filen i **Lösenord för dekryptering av den fil som importeras** och klicka sedan på **Importera**.

    Den lösenordskrypterade filen innehåller licensieringscertifikatet, den privata nyckeln (om nyckeln lagras i programvara) och principmallar för rättigheter.

4.  Domänens namn visas i listan **Betrodda publiceringsdomäner**.

Mer information om hur du utför den här proceduren finns i ”[Lägga till och ta bort betrodda publiceringsdomäner](https://technet.microsoft.com/d87b502d-5497-4ccd-badf-f6807d587cee)” tidigare i det här avsnittet.
