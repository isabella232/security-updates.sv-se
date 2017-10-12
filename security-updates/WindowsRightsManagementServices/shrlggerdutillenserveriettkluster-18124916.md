---
TOCTitle: Så här lägger du till en server i ett kluster
Title: Så här lägger du till en server i ett kluster
ms:assetid: 'db635238-5528-4bec-9cc6-8244e2b3d733'
ms:contentKeyID: 18124916
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747690(v=WS.10)'
---

Så här lägger du till en server i ett kluster
=============================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

På varje server kan du bara etablera RMS på en webbplats. Om du vill etablera RMS på en annan webbplats än standardwebbplatsen använder du Internet Information Services Manager och lägger till webbplatsen innan du påbörjar etableringsprocessen. Stäng sidan **Global administration** om den webbplats du vill etablera inte visas i listan över webbplatser. Lägg till webbplatsen och starta sedan etableringen igen.

Om du distribuerar RMS i en miljö där Active Directory-domänens funktionalitetsnivå har angetts till enhetligt läge i Microsoft Windows 2000 är det inte säkert att Windows RMS kan läsa attributet **memberOf** för Active Directory-objekt vid försök att expandera gruppmedlemskap. RMS-tjänstkontot måste använda ett domänkonto som tillhör gruppen Åtkomst till äldre operativsystem (före Windows 2000) i skogen för att det ska gå att läsa attributet **memberOf** i RMS.

Lägga till en server i ett kluster
----------------------------------

#### Så här lägger du till en server i ett kluster

1.  Öppna sidan **Global administration** när du har installerat RMS på den server som du vill ansluta till ett rotcertifikat- eller licensieringskluster.

2.  Klicka på **Lägg till den här servern i ett kluster** bredvid den webbplats där du vill etablera RMS. Du kan välja standardwebbplatsen eller en annan webbplats som du skapar i IIS (Internet Information Services).

    | ![](images/Cc747690.Warning(WS.10).gif)Varning!                                                                                                                                                                                        |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Det går inte att köra ytterligare webbplatser eller webbtjänster på den server där RMS är installerat. Om du gör det kan det leda till att flera program och tjänster körs under samma konto som RMS, vilket kan kompromettera säkerheten för de privata nycklarna. |

3.  Skriv in namnet på och lösenordet för det RMS-tjänstkonto som normalt används för de vanligaste åtgärderna i RMS vid **RMS-tjänstkonto**. Använd formatet domännamn\\användarnamn. Kontot måste vara ett domänkonto. Alla servrar i ett kluster bör köras under samma RMS-tjänstkonto.

    | ![](images/Cc747690.Important(WS.10).gif)Viktigt!                                                                                                                                                                  |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Av säkerhetsskäl bör du skapa ett specifikt domänkonto som används som tjänstkonto för Windows RMS. Tilldela inte detta konto några andra behörigheter. RMS-tjänstkontot kan inte vara samma domänkonto som användes vid installationen av RMS. |

4.  Skriv in databasserverns namn och namnet på konfigurationsdatabasen för det aktuella klustret vid **Konfigurationsdatabas**. Vilken databas du väljer avgör till vilket kluster servern ansluts.

5.  Välj önskat skydd av den privata nyckeln i klustret vid **Skydd av privat nyckel**. Om du väljer det programvarubaserade standardskyddet av nycklar anger du det lösenord som användes vid kryptering av den privata nyckeln när den första servern i klustret etablerades.

6.  Klicka på **Skicka**.

    Stäng inte sidan om felmeddelanden visas. Åtgärda i stället felen, stoppa och starta om IIS från kommandoraden med IISReset, gå tillbaka till föregående sida, ange etableringsinformationen på nytt och klicka sedan på **Skicka** igen. Stäng fönstret och kontrollera att systemet uppfyller maskinvarukraven om meddelandet Begäran gjorde timeout visas. Försök sedan etablera servern igen.
