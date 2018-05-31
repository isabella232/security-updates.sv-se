---
TOCTitle: 'Planera databasserver-infrastrukturen'
Title: 'Planera databasserver-infrastrukturen'
ms:assetid: 'b12354bd-3143-4d1f-b5aa-450c4550653c'
ms:contentKeyID: 18124876
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747731(v=WS.10)'
---

Planera databasserver-infrastrukturen
=====================================

I RMS utförs alla åtgärder med databaser och lagrade procedurer. Därför behövs en databasinfrastruktur om du vill använda RMS i organisationen. Databasservern kan ligga på samma server som RMS eller på en annan server. Om det inte finns någon databasserver i infrastrukturen kan du använda Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) Release A som databasserver när du testar RMS.

Vi rekommenderar att Microsoft SQL Server Desktop Engine endast används tillsammans med RMS-databaser i testmiljö, eftersom Microsoft SQL Server Desktop Engine inte innehåller alla verktyg som behövs för att fungera med en databas i företagsskala. Eftersom MSDE inte har funktioner för fjärrnätverk måste du installera det på samma server som RMS och du kan då inte lägga till fler RMS-servrar i RMS-klustret. Dessutom anger villkoren för användning av Microsoft SQL Server Desktop Engine att du inte får använda SQL Server-klientverktygen till att ändra en Microsoft SQL Server Desktop Engine-databas. Med den här begränsningen kan du inte säkerhetskopiera eller återställa RMS-konfigurationsdatabasen, visa loggningsinformation eller ändra data som lagrats i konfigurationsdatabasen direkt.

Om du avser att lägga databaserna på en annan server än den server där RMS-installationen finns måste du använda en heltäckande databasserverprodukt, t.ex. SQL Server, till att hantera databaserna. Tänk på att tilldela RMS-tjänstkontot tillräckliga behörigheter att läsa, skriva till och skapa de databaser på databasservern som du använder för att hantera RMS.

Trots att RMS är utvecklat för och testat med databasservrar där SQL Server 2000 och MSDE körs, samt att Microsoft inte godkänner användning av RMS tillsammans med andra databasproviders än SQL Server 2000 eller MSDE, så kan RMS köras på andra databasservrar som använder de ADO.NET-gränssnitt som tillhandahålls av Microsoft .NET Framework. Därför kan andra databasleverantörer ha utvecklat kompatibla databasproviders för RMS. Du kan använda en annan valfri databasprovider tillsammans med RMS med villkoret att motsvarande databasserver uppfyller följande krav:

-   Databasservern måste vara Transact-SQL-kompatibel eftersom RMS-initieringsskripten och de lagrade RMS-procedurerna använder Transact-SQL.
-   Databasservern måste ha funktioner för Microsoft SQL Server-specifika tillägg.

Databasprovidern måste kunna:

-   Svara på metodanrop från namnområdet System.Data.SqlClient i .NET Framework.
-   Tillhandahålla motsvarande funktioner som namnområdet System.Data.SqlClient.
-   Använda Windows-integrerad autentisering i stället för SQL-autentisering.

Om du använder RMS i någon annan konfiguration kontaktar du den databas- eller lösningsleverantör vars databasprovider du använder i din anpassade distribution.

| ![](images/Cc747731.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Alla RMS-databaser skapas med Fullständig återställning aktiverat som standard, men inga säkerhetskopior av transaktionsloggar skapas. Det kan göra att hårddisken på servern blir full, vilket kan leda till fel på databasservern. Fullständig återställning rekommenderas för databasen DRMS\_configuration. De andra DRMS-databaserna kan konfigureras så att en annan modell används för säkerhetskopiering, enligt vad som passar i din organisation. |

Avsnittet behandlar:

-   [Beräkna databasens tillväxt](https://technet.microsoft.com/87652cc2-b886-4797-8d40-356669768089)
-   [Underhålla katalogtjänstdatabasen](https://technet.microsoft.com/911a62f2-c1d6-4091-99b0-b53211be27a7)
-   [Underhålla loggningsdatabasen](https://technet.microsoft.com/de55058b-0d1a-4997-8a45-e14678ddd13f)
