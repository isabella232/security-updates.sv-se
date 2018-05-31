---
TOCTitle: Så här exkluderar du program
Title: Så här exkluderar du program
ms:assetid: '422f2ddd-bcf4-45f1-905a-b8bad30fd7dd'
ms:contentKeyID: 18124691
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720262(v=WS.10)'
---

Så här exkluderar du program
============================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Exkluderingsprinciperna framtvingas av klienten när användarlicensen binds till det skyddade innehållet.

Exkludera program eller upphöra att exkludera program
-----------------------------------------------------

#### Så här exkluderar du program

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill kontrollera vilka programversioner som kan användas med rättighetsskyddat innehåll.

2.  Klicka på **Exkluderingsprinciper** vid **Administrationslänkar**.

3.  Klicka på **Aktivera** i området **Exkludering av program** om du vill exkludera ett RMS-aktiverat program eller en RMS-aktiverad komponent.

    Klicka på **Inaktivera** om du vill inaktivera exkludering av program.

4.  Skriv in filnamnet på det program eller den komponent som ska exkluderas, skriv in versionsnumret på de tidigaste och de senaste versioner som ska exkluderas (i formatet *x*.*x*.*x*.*x*) och klicka sedan på **Exkludera det här programmet**.

    Markera filnamnet på ett program eller en komponent och klicka sedan på **Ta bort markerade program från exkluderingslistan** om du vill ta bort programmet eller komponenten från exkluderingslistan.

    | ![](images/Cc720262.note(WS.10).gif)Obs!                                                                                                                                                                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | I RMS krävs att programversionen anges i ett 4-siffrigt punktavgränsat format (\#.\#.\#.\# ). I vissa program anges dock programversionen i ett 2- eller 3-siffrigt punktavgränsat format. I så fall måste du lägga till .0 där det behövs så att versionsnumret stämmer överens med det format som krävs i RMS. |

#### Upphöra att exkludera program

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill kontrollera vilka programversioner som kan användas med rättighetsskyddat innehåll.

2.  Klicka på **Exkluderingsprinciper** vid **Administrationslänkar**.

3.  Klicka på **Inaktivera** i området **Exkludering av program**.

Mer information om hur du utför den här processen finns i ”[Exkludera program](https://technet.microsoft.com/b68ae4b2-b9ba-44ae-90cb-c88df600ec86)” tidigare i det här avsnittet.
