---
TOCTitle: Så här exkluderar du rättighetskontocertifikat
Title: Så här exkluderar du rättighetskontocertifikat
ms:assetid: 'e5cd9dec-ac29-437e-8515-dc697ec75edf'
ms:contentKeyID: 18124935
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747785(v=WS.10)'
---

Så här exkluderar du rättighetskontocertifikat
==============================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Dessa villkor framtvingas av klienten när användarlicensen binds till det skyddade innehållet.

Exkludera rättighetskontocertifikat
-----------------------------------

#### Så här exkluderar du rättighetskontocertifikat

1.  Öppna sidan **Global Administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill exkludera rättighetskontocertifikat.

2.  Klicka på **Exkluderingsprinciper** vid **Administrationslänkar**.

3.  Klicka på **Aktivera** i området för exkludering av rättighetskontocertifikat om du vill exkludera en användares rättighetskontocertifikat.

4.  Ange vilken metod som ska användas till att ange vilka kontocertifikat som ska exkluderas:

    -   Klicka på **Användarnamn** för det rättighetskontocertifikat som ska exkluderas om du vill exkludera kontocertifikat baserat på användarnamn. Skriv in namnet på användaren som ska exkluderas (i formatet *användarnamn*@*domännamn*.se) och klicka sedan på **Lägg till**. Använd det här alternativet när du vill exkludera kontocertifikat för interna användare med Active Directory-användarkonton.
    -   Klicka på **Offentlig nyckelsträng** för det rättighetskontocertifikat som ska exkluderas om du vill exkludera kontocertifikat baserat på offentlig nyckel. Skriv in den offentliga nyckelsträngen för det rättighetskontocertifikat som ska exkluderas och klicka sedan på **Lägg till**. Använd det här alternativet när du vill exkludera kontocertifikat för externa användare som saknar Active Directory-användarkonton.

    | ![](images/Cc747785.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Klicka på det exkluderade rättighetskontocertifikatet i listan och klicka sedan på **Ta bort markerade offentliga nycklar från exkluderingslistan** om du vill ta bort ett kontocertifikat från exkluderingslistan. Användaren med det aktuella kontocertifikatet kan sedan hämta en licens för RMS-skyddat innehåll från den aktuella servern. |

    | ![](images/Cc747785.note(WS.10).gif)Obs!                      |
    |--------------------------------------------------------------------------------------------|
    | Klicka på **Inaktivera** om du vill inaktivera exkluderingen av rättighetskontocertifikat. |

Mer information om hur du utför den här processen finns i ”[Exkludera rättighetskontocertifikat](https://technet.microsoft.com/cba5e901-942c-4d06-9865-e6c4648c95e6)” tidigare i det här avsnittet.
