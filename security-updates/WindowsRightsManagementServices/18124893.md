---
TOCTitle: 'RMS-kontocertifiering'
Title: 'RMS-kontocertifiering'
ms:assetid: 'c9a385c5-6dbb-47f5-a80f-69718e6f9deb'
ms:contentKeyID: 18124893
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747750(v=WS.10)'
---

RMS-kontocertifiering
=====================

I kontocertifieringsprocessen skapas ett rättighetskontocertifikat som kopplar ett användarkonto till en särskild dator och som gör att användaren får tillgång till RMS-skyddat innehåll från den datorn. Första gången en användare publicerar RMS-skyddat innehåll eller försöker använda RMS-skyddat innehåll på en klientdator, skickas en begäran från det RMS-aktiverade programmet om ett rättighetskontocertifikat till kontocertifieringstjänsten.

Certifieringstjänsten kan autentisera användaren antingen genom Windows-autentisering eller ett x.509-certifikat som lagras i en enhet för maskinvarukryptering, t.ex. ett smartkort. När användaren har autentiserats skapar RMS-servern ett rättighetskontocertifikat till användaren som baseras på dennes autentiserade identitet. Användarens privata nyckel krypteras med den offentliga nyckeln för klientdatorns RMS-datorcertifikat, och den krypterade nyckeln bifogas i rättighetskontocertifikatet. Tjänsten utfärdar sedan rättighetskontocertifikatet till det program som begärt det, varefter certifikatet sparas på datorn så att det kan utnyttjas för kommande begäran om publicering eller användarlicenser. Rättighetskontocertifikatet sparas också i konfigurationsdatabasen.

Efter datoraktiveringsprocessen följer en kontocertifiering, eftersom klientdatorns RMS-datorcertifikat krävs för att begära rättighetskontocertifikatet.

En användare måste skaffa ett rättighetskontocertifikat för varje dator han eller hon använder. Om en användare ska arbeta vid mer än en dator utfärdas ett unikt rättighetskontocertifikat för varje dator, men alla datorer innehåller samma nyckelpar för den användaren.

När en användarlicens begärs från ett RMS-aktiverat program bifogas rättighetskontocertifikatet i begäran. I licensieringstjänsten används rättighetskontocertifikatets offentliga nyckel till att kryptera innehållsnyckeln. På så sätt säkerställs att endast den autentiserade användaren kan använda licensen.

Kontocertifieringsprocessen sker i följande steg:

1.  Första gången en användare publicerar RMS-skyddat innehåll eller försöker använda RMS-skyddat innehåll på en viss dator, skickas en begäran från det RMS-aktiverade programmet om ett rättighetskontocertifikat till kontocertifieringstjänsten på rotcertifikatservern.
2.  Kontocertifieringstjänsten autentiserar användaren med hjälp av Windows användarautentisering.
3.  Ett rättighetskontocertifikat skapas i kontocertifieringstjänsten för användaren baserat på dennes autentiserade identitet. Användarens privata nyckel krypteras med RMS-datorcertifikatets offentliga nyckel och den krypterade nyckeln bifogas i certifikatet. Sedan utfärdas rättighetskontocertifikatet av tjänsten till det program varifrån begäran skickats.
4.  Rättighetskontocertifikatet sparas på datorn eller enheten, så att det kan utnyttjas för kommande publicerings- eller licensieringsbegäran.

Kontocertifieringstjänsten som klienten använder till att begära rättighetskontocertifikatet ser olika ut beroende på vilken typ av dator som RMS-klienten är installerad på. Stationära datorer av standardmodell ansluts till kontocertifieringstjänsten (certification.asmx). Servertjänster som har aktiverats för användning med RMS SP1 tar emot rättighetskontocertifikat från servercertifieringstjänsten (ServeCertfication.asmx). Mobila enheter som kan användas med RMS SP1 tar emot rättighetskontocertifikat från certifieringstjänsten för mobila enheter (MobileDeviceCertfication.asmx). Endast kontocertifieringstjänsten är aktiverad i standardinstallationen av RMS SP1.

Mer information om att använda RMS SP1 med mobila enheter och servertjänster finns i avsnittet ”Aktivera RMS-serverfunktioner för mobila enheter och servertjänster” under Använda en RMS-server i den här dokumentationen.
