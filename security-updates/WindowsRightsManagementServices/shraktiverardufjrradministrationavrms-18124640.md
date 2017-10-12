---
TOCTitle: Så här aktiverar du fjärradministration av RMS
Title: Så här aktiverar du fjärradministration av RMS
ms:assetid: '00f17054-5f5d-47e2-89c1-7a593b930bb3'
ms:contentKeyID: 18124640
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720181(v=WS.10)'
---

Så här aktiverar du fjärradministration av RMS
==============================================

Internet Explorer 6.0 eller senare måste vara installerat på den dator som används för fjärradministration av RMS.

Aktivera fjärradministration av RMS
-----------------------------------

#### Så här aktiverar du fjärradministration av RMS

1.  Logga in på den server som du vill kunna fjärradministrera.

2.  Öppna snapin-modulen **Internet Information Services (IIS) Manager** från **Administrationsverktyg**.

3.  Expandera det objekt som representerar den webbplats där du har etablerat RMS.

4.  Högerklicka på mappen **\_wmcs** och klicka på **Egenskaper**. Klicka på **Redigera** under **Säker kommunikation** på fliken **Katalogsäkerhet**, klicka på **Kräv en säker kanal (SSL)** och klicka sedan på **OK**. På så sätt tillämpas SSL-skydd (Secure Sockets Layer) för RMS-webbtjänster. Mer information om hur du hanterar webbplatser med IIS finns i Hjälp om IIS.

    | ![](images/Cc720181.Important(WS.10).gif)Viktigt!                                                                                                                                                                       |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Om du vill öka säkerheten och aktivera fjärråtkomst till administrationssidorna för RMS via HTTP kan du skydda RMS-webbtjänster med SSL. Hämta och installera ett giltigt SSL-webbservercertifikat om du tänker aktivera SSL för RMS-webbtjänsterna. |

5.  Högerklicka på mappen **Admin** och klicka sedan på **Egenskaper**. Klicka på **Redigera** under **IP-adress och domännamnsrestriktioner** på fliken **Katalogsäkerhet**, och klicka sedan på **Beviljas åtkomst** under **Åtkomstbegränsningar för IP-adresser** så att alla datorer tillåts begära en anslutning till den här webbplatsen.
