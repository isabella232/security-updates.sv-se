---
TOCTitle: Så här exporterar du en betrodd publiceringsdomän
Title: Så här exporterar du en betrodd publiceringsdomän
ms:assetid: '3fb138dd-e324-43f8-97e0-da0027a036a3'
ms:contentKeyID: 18124690
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720252(v=WS.10)'
---

Så här exporterar du en betrodd publiceringsdomän
=================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Exportera en betrodd publiceringsdomän
--------------------------------------

#### Så här exporterar du en betrodd publiceringsdomän

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill lägga till en betrodd publiceringsdomän.

2.  Klicka på **Principer för förtroenden** vid **Administrationslänkar**.

3.  På sidan **Principer för förtroenden** klickar du på **Exportera** bredvid nyckelbehållaren för den här RMS-servern i området **Betrodda publiceringsdomäner**.

4.  Dialogrutan **Export av betrodd publiceringsdomän** visas.

5.  Ange det lösenord du vill använda till att kryptera filen för den betrodda publiceringsdomänen. Du kommer att behöva det här lösenordet om du ska kunna importera filen till en annan RMS-server. Lösenordet måste vara ett starkt lösenord.

6.  Ange lösenordet på nytt för att kontrollera att du har angett det lösenord du vill använda.

7.  Ange sökvägen till och filnamnet som ska användas för XML-filen för den betrodda publiceringsdomänen. Kontrollera att du har angett xml som filnamnstillägg.

8.  Klicka på **Exportera** så skapas filen för den betrodda publiceringsdomänen.

Mer information om hur du utför den här proceduren finns i ”[Lägga till och ta bort betrodda publiceringsdomäner](https://technet.microsoft.com/d87b502d-5497-4ccd-badf-f6807d587cee)” tidigare i det här avsnittet.
