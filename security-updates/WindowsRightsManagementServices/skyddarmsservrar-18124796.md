---
TOCTitle: 'Skydda RMS-servrar'
Title: 'Skydda RMS-servrar'
ms:assetid: '7e6c4d3a-6cfb-4e96-9dda-ead83f961a6e'
ms:contentKeyID: 18124796
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747574(v=WS.10)'
---

Skydda RMS-servrar
==================

Utgå från följande rekommendationer när du hanterar användarkonton och säkerhetsinställningar på RMS-servrar:

-   De virtuella katalogerna på den webbplats som du använder när du administrerar RMS innehåller DACL-listor (Discretionary Access Control Lists) som endast beviljar lokala administratörer åtkomst. En lokal administratör kan skapa en extra säkerhetsgrupp och kontrollera åtkomsten ytterligare genom att lägga till och ta bort medlemmar och genom att ange ytterligare åtkomstkontrollposter på administrationswebbsidorna.
-   Av säkerhetsskäl bör du ändra DACL-inställningarna på webbsidan Säkerhetsinställningar (SecurityPolicy.aspx). Etablering tillåts genom att åtkomstkontrollposterna tilldelar fullständig kontroll till det konto som etablerar RMS. Efter etableringen bör du ändra åtkomstkontrollposterna så att de gäller för en enskild användare eller för en begränsad säkerhetsgrupp.
-   Utöver de beviljade behörigheterna och rättigheterna som gäller för varje RMS-server bör du överväga vad som krävs för att skydda konfigurationsdatabasen, vilket påverkar säkerheten i hela distributionen. Mer information finns i ”[Skydda konfigurationsdatabasen](https://technet.microsoft.com/e023b96f-81d0-45fb-8cc5-becaf6d47ae1)” senare i det här avsnittet.

Mer information om hur du skyddar Microsoft SQL Server™ finns på webbsidan **SQL Server Security** på [Microsofts webbplats](http://www.microsoft.com/) (http://www.microsoft.com/).

Mer information om hur du skyddar datorer där operativsystemet Microsoft Windows Server 2003 körs finns i ”Windows Server 2003 Security Guide” på Microsoft Download Center på [Microsofts webbplats](http://www.microsoft.com/) (http://www.microsoft.com/).
