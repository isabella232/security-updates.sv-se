---
TOCTitle: Arbeta med principmallar för rättigheter
Title: Arbeta med principmallar för rättigheter
ms:assetid: 'ff4f1143-f6b9-4dd8-aa4c-c2cbbf6fdf06'
ms:contentKeyID: 18124982
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747804(v=WS.10)'
---

Arbeta med principmallar för rättigheter
========================================

När du har skapat en principmall för rättigheter kan du styra hur den tillämpas i organisationen genom att kontrollera distributionen till utgivare.

I RMS lagras principmallar för rättigheter i konfigurationsdatabasen. Dessutom behålls en kopia av alla principmallar för rättigheter i en delad mapp som du själv anger. Mer information finns i ”[Så här anger du platsen för principmallen för rättigheter](https://technet.microsoft.com/e1bee46d-33db-424f-ba45-1dcedcb883ab)” senare i det här avsnittet. Kontrollera att mallarna har lagrats på en plats som är tillgänglig från nätverket och att platsen uppfyller organisationens riktlinjer för säkerhet. Du bör inte skapa delade mappar för mallar i de kärnmappar som används i RMS, t.ex. mapparna Program och IISRoot.

När en utgivare publicerar skyddat innehåll väljer han eller hon en principmall för rättigheter bland de mallar som finns på den lokala datorn. Administratören måste distribuera principmallar för rättigheter från en delad mapp till användarnas datorer för att mallarna ska vara tillgängliga för användarna.

När en användare använder skyddat innehåll hämtar det RMS-aktiverade programmet den senaste versionen av den principmall för rättigheter som användes till att publicera innehållet från konfigurationsdatabasen. Dessa inställningar tillämpas sedan på innehållet med det RMS-aktiverade programmet. När du ändrar en principmall för rättigheter på RMS-servern uppdateras mallen i RMS i såväl konfigurationsdatabasen som den delade mappen (om RMS-servern är konfigurerad så att en filplats anges för lagring av kopior av principmallar för rättigheter). Du bör distribuera om principmallar för rättigheter till klientsystemen varje gång de har ändrats, så att användarna har tillgång till den senaste versionen på sina datorer.

Om du tar bort en principmall för rättigheter tas den bort både från konfigurationsdatabasen och från den delade mappen (som anges som filplats för lagring av kopior av mallar) när du tar bort mallen. Däremot tas den inte bort från användarnas datorer. Mallen måste tas bort manuellt från användarnas datorer. Du bör ta bort borttagna principmallar för rättigheter från alla klientdatorer. Om du inte gör det och den borttagna principmallen för rättigheter används till att publicera innehåll kommer inte några användarlicenser att utfärdas för innehållet, eftersom det inte går att hitta den angivna mallen i konfigurationsdatabasen.

Utför följande åtgärder när du arbetar med principmallar för rättigheter:

-   **Ange en delad mapp**. Innan du kan skapa den första principmallen för rättigheter måste du ange en delad mapp där alla principmallar för rättigheter lagras. Mer information finns i ”[Så här anger du platsen för principmallen för rättigheter](https://technet.microsoft.com/e1bee46d-33db-424f-ba45-1dcedcb883ab)” senare i det här avsnittet.
-   **Skapa och redigera principmallar för rättigheter**. Du kan skapa så många principmallar för rättigheter som krävs för att hantera rättigheter i organisationen. När du skapar en principmall för rättigheter definierar du vilka användare som berörs och vilka rättigheter som tillämpas. Du definierar också hur principmallen för rättigheter ska tillämpas på innehållet. Du kan därefter redigera principmallarna för rättigheter när du behöver uppdatera dem. Mer information finns i ”[Skapa och ändra principmallar för rättigheter](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)” senare i det här avsnittet.
-   **Distribuera principmallar för rättigheter**. En kopia av den aktuella principmallen för rättigheter måste finnas på en användares dator för att han eller hon ska kunna använda den. Du kan kontrollera vilka utfärdare som använder vilka principmallar för rättigheter genom att styra distributionen av mallar. Mer information finns i ”[Distribuera principmallar för rättigheter](https://technet.microsoft.com/ae6fa26f-d744-4ac9-9eb1-728ffab87bfe)” senare i det här avsnittet.
-   **Ta bort principmallar för rättigheter**. När en principmall för rättigheter inte längre är giltig kan du ta bort den. När du gör det bör du också ta bort den från användarnas datorer, så att de inte försöker använda innehåll som har publicerats med den principmall för rättigheter som har tagits bort. Mer information finns i ”[Ta bort principmallar för rättigheter](https://technet.microsoft.com/32bf98c7-edda-4507-a4b8-4c11bddd6e60)” senare i det här avsnittet.
