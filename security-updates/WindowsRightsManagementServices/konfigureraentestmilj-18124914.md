---
TOCTitle: Konfigurera en testmiljö
Title: Konfigurera en testmiljö
ms:assetid: 'cdd96b05-49e2-4b6f-bfae-40b5c028ec66'
ms:contentKeyID: 18124914
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747673(v=WS.10)'
---

Konfigurera en testmiljö
========================

RMS integreras med den befintliga Active Directory-infrastrukturen och databasservrarna, exempelvis sådana där Microsoft SQL Server™ 2000 körs. Eftersom det är känsliga komponenter bör du göra noggranna tester av RMS i en isolerad testmiljö innan du distribuerar den i organisationen. Det kräver att du konfigurerar separata Active Directory- och databasserverinstallationer i testmiljön.

Börja med den mest grundläggande konfigurationen av en RMS-server i en skog med en databasserver och en klient. När du har bekantat dig med RMS kan du låta konfigurationen växa och bli mer lik den topologi som du vill distribuera i organisationens produktionsmiljö, med flera skogar och externa anslutningar där det är nödvändigt. Även om testmiljön inte inkluderar alla redundans- och webbplatskonfigurationer i organisationens distributionsplan bör den innehålla minst en server för varje typ av komponent som kommer att distribueras.

I följande lista beskrivs enklast möjliga konfiguration för en testmiljö som du kan använda för att testa en grundläggande RMS-konfiguration:

-   En domänkontrollant där Windows 2000 Server med Service Pack 3 (SP3) eller senare körs, samt SQL Server 2000 med SP3a installerat. SQL Server tillhandahåller konfigurations-, katalogtjänst- och loggningsdatabaser för RMS. RMS kan antingen användas med Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) eller med SQL Server om databasen finns på samma server som RMS. Om du använder en fjärrserver för databasfunktionerna krävs SQL Server. Du kan hämta MSDE 2000 från Microsofts webbplats.

| ![](images/Cc747673.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows 2000 Server med Service Pack 3 (SP3) är minimikrav för domänkontrollanten, men Windows Server 2003 rekommenderas på grund av prestandaförbättringar i gruppexpanderingen i Active Directory. Vi rekommenderar att MSDE 2000 endast används för RMS-databaser i testmiljö, eftersom MSDE 2000 inte har funktioner för nätverksgränssnitt. Dessutom anger användarvillkoren till MSDE 2000 att du inte får använda klientverktyg i SQL Server för att manipulera MSDE 2000. Med den här begränsningen kan du inte se loggningsinformation eller ändra data som lagras i konfigurationsdatabasen. |

-   En rotcertifikatserver som kör Windows Server 2003 och där RMS är installerat och etablerat. Om du vill kan du lägga till fler servrar och skapa ett rotcertifikatkluster under tiden som testningen går framåt.
-   En klientdator som kör Windows XP Professional, en RMS-klient och ett RMS-aktiverat program.
-   Användarkonton med e-postadressattribut i Active Directory.

Information om hur du installerar och konfigurerar en grundläggande RMS-infrastruktur, samt hur du tillämpar kraven på infrastruktur i en produktionsmiljö finns i ”[Konfigurera en grundläggande infrastruktur](https://technet.microsoft.com/3a0a3a47-e755-4455-bb22-0e05053723e4)”.
