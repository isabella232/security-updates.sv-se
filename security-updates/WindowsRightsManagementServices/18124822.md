---
TOCTitle: Underhålla katalogtjänstdatabasen
Title: Underhålla katalogtjänstdatabasen
ms:assetid: '911a62f2-c1d6-4091-99b0-b53211be27a7'
ms:contentKeyID: 18124822
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747680(v=WS.10)'
---

Underhålla katalogtjänstdatabasen
=================================

I RMS finns en katalogtjänstdatabas som ligger på databasservern. Där finns information om användare, identifierare (t.ex. e-postadresser), säkerhets-ID (SID), gruppmedlemskap och alternativa identifierare. Informationen hämtas från LDAP-frågor som skickas till den globala katalogen i Active Directory via RMS-licensieringstjänsten och sparas lokalt i databasen. Det ger bättre svarstider från servern när användarna begär användarlicenser.

Eftersom data som lagras i den här databasen infogas och tas bort ofta blir den lätt fragmenterad. Du bör regelbundet (varje dag eller vecka) organisera om databasen för alla index i alla databastabeller i DRMS\_DirectoryServices. Då byggs indexen om så att inga data fragmenteras. Fragmenterade data kan leda till sämre prestanda och serverfel om det får fortgå utan att administratören ingriper.

Om du använder SQL Server som databasserver kan du omorganisera databaser via Underhållsguiden eller genom att köra ett eget skript med SQL Server Agent.

Om du märker att transaktionsloggen växer till orimlig storlek när du gör om indexeringen i databasen kan du minska tillväxten genom att byta från läget Fullständig återställning till läget Bulkloggad innan du gör om indexeringen.
