---
TOCTitle: Använda prestandaräknare
Title: Använda prestandaräknare
ms:assetid: '096c3b17-c082-46c4-939c-4373af0c9dec'
ms:contentKeyID: 18124627
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720180(v=WS.10)'
---

Använda prestandaräknare
========================

RMS innehåller flera uppsättningar prestandaobjekt och prestandaräknare som kan användas i Systemövervakaren vid övervakning av aktiviteten i RMS-tjänsterna. Prestandaräknarna är specifika för varje RMS-prestandaobjekt och innehåller följande objekt:

-   RMS: ActivationProxy-prestandaräknare för aktivering av proxybegäran
-   RMS: Certification-prestandaräknare för kontocertifieringsbegäran
-   RMS: DirectoryServices-prestandaräknare för Active Directory-sökningar
-   RMS: Enrollment-prestandaräknare för underregistreringsbegäran
-   RMS: Licensing-prestandaräknare för publicerings- och användarlicensbegäran
-   RMS: Logging-prestandaräknare för loggningsaktiviteter

De här prestandaräknarna installeras automatiskt under etableringen, men du måste lägga till räknarna i loggen om du vill initiera övervakning.

Så här lägger du till en prestandaräknare:

1.  Klicka på **Start**, peka på **Administrationsverktyg** och klicka sedan på **Prestanda**.
2.  Högerklicka på ett tomt område i informationsfönstret i dialogrutan **Prestanda** och klicka sedan på **Lägg till räknare**.
3.  Välj den räknare som du vill lägga till i objektlistan **Prestanda** i dialogrutan **Lägg till räknare** och klicka sedan på **Lägg till**.

Du kan använda alternativen **Prestandaloggar och -varningar** som finns i dialogrutan **Prestanda** till att övervaka och hantera loggfiler. Mer information om de olika prestandaräknare som är tillgängliga i RMS finns i ”[Prestandaräknare för RMS](https://technet.microsoft.com/a2f4e30d-3c6f-4e74-bd11-8f2103f88b0c)” senare i det här avsnittet. En allmän information om prestandaräknare finns i Hjälp om Systemövervakaren.
