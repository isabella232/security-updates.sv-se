---
TOCTitle: Så här aktiverar och inaktiverar du loggning
Title: Så här aktiverar och inaktiverar du loggning
ms:assetid: '8e672f95-566f-4070-9a2a-2f70f087148f'
ms:contentKeyID: 18124815
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747674(v=WS.10)'
---

Så här aktiverar och inaktiverar du loggning
============================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Kontrollera att RMS-servern är ansluten till databasservern och att databastjänsten har startats innan du aktiverar loggning. Om det inte går att leverera loggningsinformationen till loggningsdatabasen med Message Queuing placeras data i kö på RMS-serverns hårddisk. Den här processen fortsätter tills det inte längre finns något ledigt utrymme kvar på servern. RMS visar inget felmeddelande i den här situationen, eftersom den här funktionen ska göra att loggning fungerar även när anslutningen till SQL-servern avbryts.

Aktivera och inaktivera loggning
--------------------------------

#### Så här aktiverar och inaktiverar du loggning

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill aktivera eller inaktivera loggning.

2.  Klicka på **Loggningsinställningar** vid **Administrationslänkar**.

3.  Markera kryssrutan **Aktivera loggning** vid **Loggningsserver och loggningsdatabas** och klicka sedan på **Uppdatera**.

    Avmarkera kryssrutan och klicka på **Uppdatera** om du vill inaktivera loggning.

Mer information om hur du utför den här processen finns i ”[Aktivera och inaktivera loggning](https://technet.microsoft.com/50ccd827-2d39-41e7-a395-3d5f5836869b)” tidigare i det här avsnittet.
