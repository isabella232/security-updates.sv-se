---
TOCTitle: Så här lägger du till en betrodd användardomän
Title: Så här lägger du till en betrodd användardomän
ms:assetid: 'ed672e58-6272-4ac0-a434-d1d938037e93'
ms:contentKeyID: 18124955
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747793(v=WS.10)'
---

Så här lägger du till en betrodd användardomän
==============================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Lägga till en betrodd användardomän
-----------------------------------

#### Så här lägger du till en betrodd användardomän

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill lägga till en betrodd användardomän.

2.  Klicka på **Principer för förtroenden** vid **Administrationslänkar**.

3.  Klicka på **Bläddra** vid **Betrodda användardomäner**, leta reda och dubbelklicka på serverlicensieringscertifikatet för den användardomän som du vill importera och upprätta förtroende med och klicka sedan på **Lägg till**.

    Domänens namn visas i listan **Betrodda användardomäner**.

4.  Klicka på **Betrodda domäner** bredvid certifikatets namn i listan om du vill öppna fönstret **Betrodda e-postdomäner** där du anger vilka e-postdomäner i den betrodda användardomänen som är betrodda.

5.  Välj ett av följande alternativ för förtroende:

    -   Välj alternativet **Lita på alla e-postdomäner** om du vill göra alla användarkonton som är medlemmar i den aktuella domänen betrodda.
        – eller -
    -   Välj alternativet **Lita endast på angivna e-postdomäner**, ange det domännamn som ska vara betrott, t.ex. exempel.com, och klicka sedan på **Lägg till**. Domänen läggs då till i listan Betrodda e-postdomäner. Markera ett namn i listan och klicka på **Ta bort** om du vill ta bort det. När du lägger till en domän läggs även alla underdomäner till i listan.

6.  Om du använder RMS i en miljö där du behöver expandera gruppmedlemskap mellan skogar markerar du kryssrutan **Lita på säkerhetsidentifierare (SID) för RM-licensiering för den här användardomänen**.

7.  Klicka på **Stäng fönstret och återgå till Principer för förtroenden** när du är färdig.

Mer information om hur du utför den här processen finns i ”[Lägga till och ta bort betrodda användardomäner](https://technet.microsoft.com/7c440b15-01c4-49f1-b43c-00f67f3388c1)” tidigare i det här avsnittet.
