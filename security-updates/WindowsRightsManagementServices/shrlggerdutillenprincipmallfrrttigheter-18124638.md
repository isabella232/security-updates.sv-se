---
TOCTitle: Så här lägger du till en principmall för rättigheter
Title: Så här lägger du till en principmall för rättigheter
ms:assetid: '1a5555cd-6d39-4078-a879-4106864674be'
ms:contentKeyID: 18124638
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720206(v=WS.10)'
---

Så här lägger du till en principmall för rättigheter
====================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Lägga till en principmall för rättigheter
-----------------------------------------

#### Så här lägger du till en principmall för rättigheter

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill lägga till en principmall för rättigheter.

2.  Klicka på **Principmallar för rättigheter** vid **Administrationslänkar**.

3.  I **Språk** väljer du det språk du vill ska användas i mallen.

4.  Klicka på **Lägg till en principmall för rättigheter**.

5.  Ange ett namn, en beskrivning och en URL för begäran av rättigheter för mallen vid **Mall-ID**.

6.  Skriv in en giltig e-postadress till den användare eller grupp som ska läggas till i **Lägg till användare och grupper** vid **Användare och grupper** och klicka sedan på **Lägg till**. Upprepa stegen för varje användare och grupp du vill lägga till.

7.  Markera e-postadressen till en användare eller en grupp som ska tilldelas rättigheter i **Aktuella användare och grupper**.

8.  Markera kryssrutan bredvid alla rättigheter som ska beviljas den aktuella användaren eller gruppen. Upprepa stegen för alla användare och grupper som ska beviljas rättigheter.

9.  Välj ett av de tre alternativen för förfallodatum vid **Princip för förfallodatum** och ange sedan förfallodatum eller tid. Markera **Användarlicenser för innehåll måste förnyas efter** och ange antalet dagar mellan förnyelser om så önskas.

10. Markera ett eller flera av de fyra alternativen vid **Utökad princip**. Ange ett namn och ett värde för de data som ska användas och klicka sedan på **Lägg till** om du markerar **Använd programspecifika data**.

11. Markera kryssrutan **Begär återkallning** vid **Princip för återkallning** om du vill implementera återkallning. Följ sedan nedanstående steg:

    1.  I **URL eller UNC** anger du URL:en till den plats där filen med listan över återkallade certifikat finns. Om du behöver hantera användare som inte är anslutna eller externa användare måste URL:en vara möjlig att nå både från företagets nätverk och från Internet.
    2.  Ange i hur många dagar listan över återkallade certifikat är giltig i **Uppdateringsintervall för lista över återkallade certifikat**. Om en användare har en kopia av listan över återkallade certifikat som är äldre än det här värdet måste användaren hämta en uppdaterad lista över återkallade certifikat för att kunna använda innehållet.
    3.  Ange sökväg och filnamn i **Fil med offentlig nyckel** eller klicka på **Bläddra** och leta reda på filen med offentlig nyckel för listan över återkallade certifikat. Mer information om den här filen finns i ”Infoga en signatur i en lista över återkallade certifikat”.

    | ![](images/Cc720206.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Var försiktig när du implementerar återkallningar. Du måste förnya listan med jämna mellanrum baserat på det uppdateringsintervall som du anger. Annars upphör den automatiskt att gälla, vilket hindrar användare från att använda innehåll som är beroende av listan. Utvärdera uppdateringsintervallet för listan över återkallade certifikat noggrant så att du inte av misstag hindrar användare från att använda innehåll. Mer information finns i ”[Hantera återkallning](https://technet.microsoft.com/df732a7d-1fb0-4845-87ca-fab4bc5f98a0)” tidigare i det här avsnittet. |

12. Klicka på **Skicka**.

Mer information om återkallning finns i ”[Hantera återkallning](https://technet.microsoft.com/df732a7d-1fb0-4845-87ca-fab4bc5f98a0)” tidigare i det här avsnittet.

Information om överväganden när du anger alternativ för återkallning finns i ”[Definiera principer för återkallning](https://technet.microsoft.com/e2fffe9f-def7-439b-a8aa-43f8a065813d)” tidigare i det här avsnittet.

Mer information om hur du utför den här processen finns i[Skapa och ändra principmallar för rättigheter](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)” tidigare i det här avsnittet.
