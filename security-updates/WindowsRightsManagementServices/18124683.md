---
TOCTitle: Optimera prestanda
Title: Optimera prestanda
ms:assetid: '24dc9ca4-652b-41a6-9a99-95fdeca9120b'
ms:contentKeyID: 18124683
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720220(v=WS.10)'
---

Optimera prestanda
==================

Det här avsnittet innehåller information om hur du optimerar prestanda i en RMS-distribution.

Optimera prestanda för katalogtjänster
--------------------------------------

Du kan övervaka de DirectoryServices-prestandaräknare som ingår i RMS. Vid behov kan du optimera prestanda genom att ändra de registerinställningar som styr attributen för Active Directory-cachen.

Med registerinställningarna styrs följande attribut för Active Directory-cachen:

-   Maximalt antal enheter som ska cachelagras
-   Giltighetstid för cachelagrad information för enheter.
-   Maximalt antal grupper som ska cachelagras
-   Giltighetstid för cachelagrad information för grupper.
-   Maximalt antal poster för gruppmedlemskap
-   Giltighetstid för cachelagrad information för gruppmedlemskap.

Normalt gäller att ju längre giltighetstiden är för cachelagrad information och ju fler poster som finns i cachen, desto snabbare kan RMS svara på begäran som kräver att information om katalogtjänster hämtas. Om informationen lagras i Active Directory-cachen krävs ingen läsning från Active Directory för att utföra en sökning. Det här kortar ned svarstiden för begäran.

Nackdelen med att lagra information i Active Directory-cachen är att det krävs mer systemminne. Ett annat problem som bör övervägas när du konfigurerar registerinställningar är att ju längre giltighetstid som anges för ett objekt, desto troligare är det att några av de resultat som returneras från Active Directory-cachen är ogiltiga. Det kan inträffa när information ändras i Active Directory men inte hinner bli uppdaterad i Active Directory-cachen. Om Active Directory-informationen ändras ofta bör du ange en kortare giltighetstid för cachelagrad information, så att giltighetstiden återspeglar ändringsintervallet.

DirectoryServices-prestandaräknare beskrivs i ”[RMS: DirectoryServices-prestandaräknare](https://technet.microsoft.com/37afea1d-f320-4040-96d8-57c0b45e6d46)” senare i det här avsnittet. Instruktioner om hur du använder dem finns i ”[Använda prestandaräknare](https://technet.microsoft.com/096c3b17-c082-46c4-939c-4373af0c9dec)” tidigare i det här avsnittet. De räknare som du bör övervaka är ”träffar” respektive ”missar”. RMS måste utföra en Active Directory-sökning för varje miss.

Information om registerinställningarna och instruktioner för hur du ändrar dem finns i ”[Ändra cacheinställningar för Active Directory](https://technet.microsoft.com/8789a7a5-2065-4fae-9104-e0a70f1f2fb6)” senare i det här avsnittet.

Optimera inställningarna för Active Directory-anslutningspoolen
---------------------------------------------------------------

Om du vill förbättra systemets prestanda kan du lägga till och ändra de registernycklar som kontrollerar inställningarna för Active Directory LDAP-anslutningspoolen (Lightweight Directory Access Protocol). Information om hur du konfigurerar registernycklar finns i ”[Ändra registerinställningar för anslutningspool](https://technet.microsoft.com/c61d91db-a1ad-4ca5-a492-015da629afbc)” senare i det här avsnittet.

RMS är utformat för att optimera LDAP-anslutningar. Med RMS upprättas en anslutning för varje global katalog i Active Directory och varje anslutning kan hantera flera trådar. Tack vare en anslutningspool som hanterar flera begäran blir hanteringen robust. I RMS används en algoritm för distribution av begäran så att det kan undvikas att en enskild global katalog belastas. Algoritmen utför en belastningsutjämning bland de globala kataloger som ingår i listan över globala kataloger som hanterar frågor. Dessutom hanteras LDAP-fel automatiskt så att begäran vid behov omdirigeras till en annan global katalog.

Med hjälp av en algoritm för topologiidentifiering, Topology Discovery, upprättas en lista över globala kataloger som hanterar frågor. Du kan ange ett lägsta och ett högsta antal tillgängliga globala kataloger som måste hittas med Topology Discovery innan några RMS-tjänster kan startas. Med Topology Discovery identifieras först de globala katalogerna på den aktuella platsen. Om det krävs ytterligare globala kataloger genomsöks även andra platser. Du kan också ange maximalt antal anslutningar som kan vara otillgängliga innan RMS slutar att ta emot begäran. Om en eller flera globala kataloger i frågelistan blir otillgängliga påbörjas en sökning med Topology Discovery efter alternativa globala kataloger att lägga till i frågelistan.

Du kan också välja att räkna upp de globala kataloger som du vill använda i RMS. I så fall görs ingen sökning efter globala kataloger att lägga till i frågelistan.

Du kan också konfigurera inställningar för hur belastningsutjämningen ska utföras mellan de globala katalogerna i RMS. Du kan ange hur viktiga följande överväganden ska vara i förhållande till varandra när du bestämmer om en specifik begäran ska skickas till en viss global katalog:

-   **Resursallokering (WtRoundRobin)**. Den här parametern anger den relativa vikten av belastningsutjämning som använder resursallokeringslogik. Standardinställningen för vikt är 1, vilket innebär att det är den parameter som är minst viktig för servern att beakta vid val av en global katalog.
-   **Antal trådar vid anslutning (WtThreadCount)**. Den här parametern anger den relativa vikten av det antal trådar som är allokerade till en anslutning. Standardinställningen för vikt är 100, vilket innebär att det är 100 gånger viktigare att antalet trådar för en global katalog är lågt när en anslutning väljs, än att belastningsutjämning med resursallokering används.
-   **Långsam anslutning (WtSlow)**. Den här parametern anger den relativa vikten av en långsam anslutning. Standardinställningen för vikt är 1 000, vilket innebär att det är 10 gånger viktigare att en anslutning till en global katalog inte är långsam, än att antalet trådar är lågt.
