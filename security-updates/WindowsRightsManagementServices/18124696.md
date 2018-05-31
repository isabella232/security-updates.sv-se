---
TOCTitle: Så här anger du den administrativa kontakten
Title: Så här anger du den administrativa kontakten
ms:assetid: '31777458-5530-4ae0-ac1f-131b3d98dd35'
ms:contentKeyID: 18124696
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720237(v=WS.10)'
---

Så här anger du den administrativa kontakten
============================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Den administratör som anges måste vara en lokal administratör på rotcertifikatservern. Orsaken är att den inloggade användaren måste ha behörigheter till filen SubEnrollService.asmx på rotcertifikatservern för att kunna etablera en licensieringsserver. Om användaren som försöker etablera en licensieringsserver inte har behörigheter till den filen kan han eller hon skicka en begäran till den aktuella administratören om att det aktuella användarkontot ska tilldelas nödvändiga behörigheter. Mer information finns i ”[Ange behörigheter för underregistreringstjänstfilen](https://technet.microsoft.com/737bb69b-fe26-4057-9569-e632f7bbf295)” tidigare i det här avsnittet.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Ange den administrativa kontakten
---------------------------------

#### Så här anger du den administrativa kontakten

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill ange en administrativ kontakt.

2.  Klicka på **Certifieringsinställningar** vid **Administrationslänkar**.

3.  Skriv in e-postadressen till den administratör som ska kontaktas vid problem med underregistrering av en licensieringsserver vid **Administrativ kontakt**. Använd formatet *användarnamn*@*domännamn*.se.

4.  Klicka på **Skicka** längst ned på sidan.
