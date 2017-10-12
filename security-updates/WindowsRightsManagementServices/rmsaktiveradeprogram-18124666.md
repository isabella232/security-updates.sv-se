---
TOCTitle: 'RMS-aktiverade program'
Title: 'RMS-aktiverade program'
ms:assetid: '30bb5565-81d3-43d9-a64d-cf0c5b990712'
ms:contentKeyID: 18124666
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720231(v=WS.10)'
---

RMS-aktiverade program
======================

För att kunna skapa eller använda RMS-skyddat innehåll måste en användare ha ett RMS-aktiverat program installerat på sin dator, vilket beskrivs i det här avsnittet. Utöver det måste RMS-klienten installeras och aktiveras på användarens dator. Mer information finns i ”[RMS-klient](https://technet.microsoft.com/03294fa2-8350-430d-b4b0-03d5169937c2)” och ”[RMS-datoraktivering](https://technet.microsoft.com/09a0d631-9860-477f-9d10-df61b3bfe125)” senare i det här avsnittet.

Med RMS-aktiverade program kan användare ange rättigheter i form av publiceringslicenser för de filer de skapar och på så sätt bestämma hur innehållet får användas. RMS-aktiverade program behandlar också den krypterade filinformationen och gör så att användare använder innehållet enligt de behörigheter som anges i publiceringslicensen.

Utvecklare kan använda Rights Management Services Client SDK till att skapa RMS-aktiverade program som licensierar, publicerar och använder RMS-skyddat innehåll. RMS-aktiverade program kan utvecklas för datorer med Microsoft® Windows® 98 Second Edition eller senare installerat.

Utvecklare kan också skriva RMS-aktiverade serverprogram med hjälp av SDK-gränssnittet för Windows Rights Management Services. Med hjälp av dessa program kan en användare publicera men inte använda innehåll.

Användare som inte har något annat RMS-aktiverat program som behövs vid användning av RMS-skyddat material i e-post och på webbsidor kan hämta och använda tilläggsprogrammet Rights Management för Microsoft® Internet Explorer. Till exempel kan kunder som använder OWA (Outlook Web Access) utnyttja Rights Management för Internet Explorer till att läsa RMS-skyddade e-postmeddelanden.

Tilläggskomponenten Rights Management Add-On for Internet Explorer kan hämtas från [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=14450) (http://go.microsoft.com/fwlink/?LinkId=14450).

| ![](images/Cc720231.note(WS.10).gif)Obs!                                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du använder Rights Management Add-on for Internet Explorer med Windows XP Service Pack 2 kan den förbättrade säkerhetskonfigurationen skapa kompatibilitetsproblem med programvaran. |

Om extranät-URL:erna för alla domäner i organisationen inte läggs till på sidorna för Lokalt intranät i Internet Explorer kommer användare som använder Rights Management Add-on for Internet Explorer att upprepade gånger få frågan om de är säkra på att de vill ansluta till de här sidorna. Om de svarar fel på frågan kan resultatet bli att ett nytt rättighetskontocertifikat hämtas för användarkontot med RMS-klienten.

Du kan använda ett skript till att ange de här platserna på rätt sätt genom hela organisationen. Använd skriptet till att ange de URL-adresser som behövs i registret som en del av zonen Lokalt intranät. Zonen Lokalt intranät har tillräckligt hög säkerhet som standard för att inga fler frågor ska skickas.
