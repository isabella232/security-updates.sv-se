---
TOCTitle: Så här redigerar du en principmall för rättigheter
Title: Så här redigerar du en principmall för rättigheter
ms:assetid: '9580b934-bd6f-4097-9d3c-4fc14a3147fa'
ms:contentKeyID: 18124824
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747684(v=WS.10)'
---

Så här redigerar du en principmall för rättigheter
==================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Redigera en principmall för rättigheter
---------------------------------------

#### Så här redigerar du en principmall för rättigheter

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill redigera en principmall för rättigheter.

2.  Klicka på **Principmallar för rättigheter** vid **Administrationslänkar**.

3.  Klicka på namnet på den mall som ska redigeras under **Mallnamn**.

4.  Ändra informationen i **Mallnamn**, **Mallbeskrivning** och **URL för begäran av rättigheter** vid **Mall-ID** efter behov.

5.  Gör något av följande vid **Användare och grupper**.

    -   Skriv in en giltig e-postadress till en användare eller grupp i **Lägg till användare och grupper**, klicka på **Lägg till** och markera sedan namnet i **Aktuella användare och grupper** om du vill lägga till en användare eller grupp. Markera alla rättigheter som ska beviljas den aktuella användaren eller gruppen vid **Rättigheter**.
    -   Markera namnet på en befintlig användare eller grupp i **Aktuella användare och grupper** och markera och avmarkera sedan kryssrutorna för rättigheter om du vill ändra rättigheterna.
    -   Markera namnet i **Aktuella användare och grupper** och klicka på **Ta bort** om du vill ta bort en användare eller grupp.

6.  Redigera informationen vid **Princip för förfallodatum** om du vill ändra när innehållslicenser upphör och när de måste förnyas.

7.  Redigera informationen vid **Utökad princip** om du vill ändra hur innehållslicenser implementeras, t.ex. hur beständiga författarrättigheter är, om betrodda webbläsare kan användas eller ej, licensernas beständighet i innehållet och användandet av programspecifika data.

8.  Ange om en lista över återkallade certifikat krävs för innehåll som har skapats med den aktuella mallen vid **Princip för återkallning**. Utför följande steg efter behov om du markerar **Begär återkallning**:

    -   I **URL** anger du URL:en till den plats där filen med listan över återkallade certifikat finns. Om du behöver hantera användare som inte är anslutna eller externa användare måste URL:en vara möjlig att nå både från företagets nätverk och från Internet. Mer information finns i ”[Implementera återkallning](https://technet.microsoft.com/4735f060-7197-4ae2-830a-f91bcc4de30a)” tidigare i det här avsnittet.
    -   Ange i hur många dagar listan över återkallade certifikat är giltig i **Uppdateringsintervall för lista över återkallade certifikat**. Om en användare har en kopia av listan över återkallade certifikat som är äldre än det här värdet måste användaren hämta en uppdaterad lista över återkallade certifikat för att kunna använda innehållet.
    -   Ange sökväg och filnamn i **Fil med offentlig nyckel** till filen med offentlig nyckel för listan över återkallade certifikat. Mer information om den här filen finns i ”Infoga en signatur i en lista över återkallade certifikat” tidigare i det här avsnittet.

    | ![](images/Cc747684.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Var försiktig när du implementerar återkallningar. Du måste förnya listan med jämna mellanrum baserat på det uppdateringsintervall som du anger. Annars upphör den automatiskt att gälla, vilket hindrar användare från att använda innehåll som är beroende av listan. Utvärdera uppdateringsintervallet för listan över återkallade certifikat noggrant så att du inte av misstag hindrar användare från att använda innehåll. Mer information finns i ”[Hantera återkallning](https://technet.microsoft.com/df732a7d-1fb0-4845-87ca-fab4bc5f98a0)” tidigare i det här avsnittet. |

9.  Klicka på **Skicka**.

Mer information om hur du utför den här processen finns i ”[Skapa och ändra principmallar för rättigheter](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)” tidigare i det här avsnittet.
