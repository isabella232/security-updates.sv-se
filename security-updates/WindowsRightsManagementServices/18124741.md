---
TOCTitle: Använda smartkort till att autentisera klienter
Title: Använda smartkort till att autentisera klienter
ms:assetid: '5caacd67-fb16-46f1-b1ad-4aef0a632bf0'
ms:contentKeyID: 18124741
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747579(v=WS.10)'
---

Använda smartkort till att autentisera klienter
===============================================

Om du använder smartkort i organisationen för att öka skyddet och kontrollen av användaruppgifter kan du nu även använda dem när du hämtar rättighetskontocertifikat och användarlicenser från RMS-servern. Om du vill konfigurera RMS-servern så att klientautentisering ska krävas måste du aktivera SSL (Secure Sockets Layer) för den webbplats där du etablerade RMS, och sedan konfigurera autentiseringsmetoden i IIS (Internet Information Services). Följ stegen nedan om du vill utföra den här åtgärden.

1.  Öppna **Internet Information Services Manager**.
2.  Expandera serverobjektet, högerklicka på webbplatsmappen och klicka sedan på **Egenskaper**.
3.  Klicka på fliken **Katalogsäkerhet**. Vid **Säker kommunikation** markerar du sedan kryssrutan **Aktivera katalogtjänstmappning i Windows**.
4.  Expandera webbplatsmappen, öppna den virtuella katalogen **\_wmcs** och expandera sedan den virtuella katalog (antingen **Licensiering** eller **Certifiering**) som du vill konfigurera autentisering för.
    -   Om du vill konfigurera autentisering när en användare begär en användarlicens högerklickar du på filen license.asmx och klickar sedan på **Egenskaper**.
    -   Om du vill konfigurera autentisering när en användare begär ett användarcertifikat högerklickar du på filen certification.asmx och klickar sedan på **Egenskaper**.
5.  Klicka på fliken **Filsäkerhet**. Vid **Säker kommunikation** klickar du sedan på **Redigera** så öppnas dialogrutan **Säker kommunikation**.
6.  Välj **Kräv en säker kanal (SSL)** och klicka sedan på ett av följande alternativ:
    -   **Kräv klientcertifikat**, om bara klienter med klientcertifikat, t.ex. smartkort, ska kunna ansluta sig till tjänsten.
    -   **Acceptera klientcertifikat**, om klienter ska ha möjlighet att ange autentiseringsuppgifter med hjälp av antingen ett smartkortscertifikat eller ett användarnamn och lösenord.
7.  Välj **Aktivera mappning av klientcertifikat** och klicka sedan på **OK**.
8.  Om du vill använda klientautentisering för både certifiering och licensiering upprepar du den här proceduren och väljer den andra virtuella katalogen.

När inställningarna har konfigurerats och en användare försöker öppna RMS-skyddat innehåll som publicerats med servern, uppmanas användaren att ange sina autentiseringsuppgifter innan ett rättighetskontocertifikat eller en användarlicens tillhandahålls.
