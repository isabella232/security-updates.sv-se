---
TOCTitle: 'Så här konfigurerar du gruppen RM-ansvariga'
Title: 'Så här konfigurerar du gruppen RM-ansvariga'
ms:assetid: 'f2ef847e-2824-471f-9079-5c343094aba8'
ms:contentKeyID: 18124964
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747798(v=WS.10)'
---

Så här konfigurerar du gruppen RM-ansvariga
===========================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Innan en grupp kan utses till gruppen RM-ansvariga för RMS måste gruppen finnas i Active Directory, och gruppens egenskaper måste innehålla en e-postadress (angiven som ett fullständigt kvalificerat domännamn) som är identisk med kontonamnet.

Konfigurera gruppen RM-ansvariga
--------------------------------

#### Så här konfigurerar du gruppen RM-ansvariga

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill konfigurera gruppen RM-ansvariga.

2.  Klicka på **Säkerhetsinställningar** vid **Administrationslänkar**.

3.  Klicka på **Aktivera** vid **RM-ansvariga** och lägg till gruppen RM-ansvariga.

4.  Skriv in det fullständigt kvalificerade domännamnet för en befintlig grupp i den aktuella Active Directory-skogen i **Namn på gruppen RM-ansvariga** och klicka sedan på *Spara*. Använd formatet *gruppnamn*@**domännamn.**se. Medlemmarna i gruppen kommer att beviljas ägarrättigheter till alla dokument som skyddas av RMS.

    Klicka på **Inaktivera** om du vill inaktivera rättigheterna för gruppen RM-ansvariga.

Mer information om hur du utför den här processen finns i ”[Använda gruppen RM-ansvariga](https://technet.microsoft.com/0febcb3e-7124-4e51-971a-1013b928d33b)” tidigare i det här avsnittet.
