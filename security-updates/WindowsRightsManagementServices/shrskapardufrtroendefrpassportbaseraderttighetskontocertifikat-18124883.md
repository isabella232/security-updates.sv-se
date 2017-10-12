---
TOCTitle: 'Så här skapar du förtroende för Passport-baserade rättighetskontocertifikat'
Title: 'Så här skapar du förtroende för Passport-baserade rättighetskontocertifikat'
ms:assetid: 'c096fa36-c40d-4b28-843c-e9cbbe8eef70'
ms:contentKeyID: 18124883
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747655(v=WS.10)'
---

Så här skapar du förtroende för Passport-baserade rättighetskontocertifikat
===========================================================================

Microsoft tillhandahåller en certifieringstjänst för konton som använder Microsoft .NET Passport-referenser till att upprätta rättighetskontocertifikatet för användaren. Om du vill att användare med rättighetskontocertifikat från den här tjänsten ska kunna erhålla användarlicenser från ditt RMS-kluster måste du ange en betrodd användardomän som godkänner användarreferenser från Microsofts kontocertifieringstjänst.

För att du ska kunna använda den här funktionen måste du konfigurera Internet Information Services (IIS) så att den tillåter anonym åtkomst till RMS-licensieringstjänsten. Det här steget är avgörande för externa användare eftersom licensieringstjänsten är konfigurerad så att integrerad Windows-autentisering används som standard. Om anonym åtkomst inte har angetts kommer inte externa användare med Passport-baserade rättighetskontocertifikat (RAC) att kunna få licenser.

Skapa förtroende för Passport-baserade rättighetskontocertifikat
----------------------------------------------------------------

#### Så här aktiverar du anonym åtkomst till RMS-licensieringstjänsten

1.  Öppna snapin-modulen för **Internet Information Services (IIS)-hanteraren** och expandera den server som är värd för RMS.

2.  Expandera **webbplatser** i konsolträdet och expandera sedan den webbplats där du har konfigurerat RMS. Det blir **standardwebbplatsen**.

3.  Expandera webbplatsen **\_wmcs** i konsolträdet och välj den virtuella katalogen **Licensiering**.

4.  Högerklicka på den virtuella katalogen **Licensiering** och välj **Egenskaper**.

5.  I dialogrutan **Egenskaper för Licensiering** klickar du på fliken **Katalogsäkerhet**.

6.  Klicka på **Redigera** i **Behörighets- och åtkomstkontroll**.

7.  Markera kryssrutan **Aktivera anonymåtkomst**.

#### Så här skapar du förtroende för Passport-baserade rättighetskontocertifikat

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill skapa förtroende för Passport-baserade rättighetskontocertifikat.

2.  Klicka på **Principer för förtroenden** vid **Administrationslänkar**.

3.  Klicka på **Lita på Passport-RAC:er** vid **Betrodda användardomäner**. Microsoft RM Certification Service visas i listan **Betrodda användardomäner**.

4.  Du kan exkludera användare baserat på e-postadress om du vill. Klicka på **Exkluderade identiteter** och skriv sedan in e-postadressen till den användare som inte är betrodd.
