---
TOCTitle: 'Vanliga frågor om RMS: Principmallar för rättigheter'
Title: 'Vanliga frågor om RMS: Principmallar för rättigheter'
ms:assetid: '01515f08-9844-4c1a-9ab5-a5a60a901b50'
ms:contentKeyID: 18124623
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720175(v=WS.10)'
---

Vanliga frågor om RMS: Principmallar för rättigheter
====================================================

Vanliga frågor om RMS-mallar
----------------------------

-   [Kan jag använda en standard-RMS-mall för allt innehåll som skapats inom en organisation så att ett företag kan försäkra sig om att ha en minimal uppsättning av rättigheter?](#bkmk_57)
-   [Var finns RMS-principmallarna?](#bkmk_58)
-   [När mallar skapas binds användaralias och distributionslistor till dem. Hur kan en organisation med flera avdelningar tillhandahålla mallar med samma grundläggande rättigheter men bevilja rättigheterna till olika grupper beroende på innehåll?](#bkmk_59)
-   [Är rättigheterna för ett dokument statiska? Kan rättigheterna ändras för en fil som redan har skickats om publiceringslicensen är inbäddad i filen och inte finns på RMS-principservern?](#bkmk_60)

<span id="BKMK_57"></span>
#### Kan jag använda en standard-RMS-mall för allt innehåll som skapats inom en organisation så att ett företag kan försäkra sig om att ha en minimal uppsättning av rättigheter?

Ja. Genom att använda SDK för Rights Management Services kan du utveckla ett anpassat program som kan tillämpa de mallar som krävs. Information Rights Management i Office 2003 och senare kan däremot inte användas för att tillämpa mallar för innehåll.

<span id="BKMK_58"></span>
#### Var finns RMS-principmallarna?

Platsen för mallarna bestäms i det RMS-aktiverade programmet. I Office 2003 och senare lagras det som en användarinställning i registret på följande plats:

**HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\11,0\\Common\\DRM\\AdminTemplatePath**

-eller-

**HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\12.0\\Common\\DRM\\AdminTemplatePath** för Microsoft Office 2007.

| ![](images/Cc720175.note(WS.10).gif)Obs!                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om den här posten refererar till en lokal mapp i klienten måste mallfilerna kopieras till klienten. Om den refererar till en delad nätverksmapp är mappen inte tillgänglig när användaren är offline. |

<span id="BKMK_59"></span>
#### När mallar skapas binds användaralias och distributionslistor till dem. Hur kan en organisation med flera avdelningar tillhandahålla mallar med samma grundläggande rättigheter men bevilja rättigheterna till olika grupper beroende på innehåll?

Det finns två lösningar på det här scenariot:

-   Skapa en mall med namnet ”Företagshemligheter” och licensiera den till alla anställda inom affärsenheten. Använd sedan mallen i ett e-postmeddelande och skicka meddelandet till vissa personer. Fördelen är att det krävs en enskild mall för e-post för varje affärsenhet och dessutom kan användarna begränsas utifrån vem du skickar meddelandet till. Nackdelen är att vem som helst utanför gruppen som du ursprungligen skickade meddelandet till fortfarande kan läsa det.
-   Du kan även skapa flera mallar, inklusive en för varje distributionslista. Det ger mycket exaktare kontroll, men det innebär också att IT-avdelningen måste hantera flera mallar.

<span id="BKMK_60"></span>
#### Är rättigheterna för ett dokument statiska? Kan rättigheterna ändras för en fil som redan har skickats om publiceringslicensen är inbäddad i filen och inte finns på RMS-principservern?

Ja, det är möjligt när en RMS-principmall används. När innehåll publiceras med hjälp av en RMS-principmall sparas definitionen av principen på servern och kan ändras av en administratör när innehållet har publicerats. När en användare begär en licens för innehållet beviljar licensen rättigheter enligt den aktuella principen som är definierad på servern. Om rättigheterna ändras efter att en användarlicens har utfärdats till en användare kommer användaren även fortsättningsvis att beviljas de rättigheter som var aktuella när användarlicensen utfärdades. Om du vill tillämpa en ny principmall för rättigheter efter att innehållet har publicerats aktiverar du en princip för förfallodatum för mallen och anger sedan alternativet **Användarlicenser för innehåll måste förnyas efter: n dagar**. Vid n anger du antalet dagar efter vilket en användare måste begära en ny användarlicens.
