---
TOCTitle: 'Så här exkluderar du lockbox-versioner'
Title: 'Så här exkluderar du lockbox-versioner'
ms:assetid: '515e5245-7a0e-414e-ac20-3ae32898179e'
ms:contentKeyID: 18124716
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720270(v=WS.10)'
---

Så här exkluderar du lockbox-versioner
======================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Exkluderingsvillkoren framtvingas av klienten när användarlicensen binds till det skyddade innehållet.

Exkludera lockbox-versioner
---------------------------

#### Så här exkluderar du lockbox-versioner

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill exkludera lockbox-versioner.

2.  Klicka på **Exkluderingsprinciper** vid **Administrationslänkar**.

3.  Klicka på **Aktivera** i området för **exkludering av RM-lockbox** om du vill exkludera lockbox-versioner.

4.  Klicka på knappen **Hämta version** om du vill ansluta till Internet och visa den tidigaste version av lockbox som signerats av Microsofts aktiveringstjänst. Om RMS-servern inte är ansluten till Internet kan du gå direkt till [Windows webbplats för RMS-aktiveringstjänsten](http://go.microsoft.com/fwlink/?linkid=12995) (http://go.microsoft.com/fwlink/?LinkID=12995) och visa den tidigaste versionen av lockbox.

5.  Kopiera versionsnumret på sidan **Tidigaste version av RM-lockbox** och klicka sedan på **Stäng**.

6.  Klistra in versionsnumret i **Tidigaste version av RM-lockbox** och klicka sedan på **Uppdatera**.

    | ![](images/Cc720270.note(WS.10).gif)Obs!                  |
    |----------------------------------------------------------------------------------------|
    | Klicka på **Inaktivera** om du vill inaktivera exkludering baserad på lockbox-version. |

Mer information om hur du utför den här processen finns i ”[Exkludera lockbox-versioner](https://technet.microsoft.com/e287f026-aab2-43ab-93bc-48087da82f36)” tidigare i det här avsnittet.
