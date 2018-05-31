---
TOCTitle: Exkludera program
Title: Exkludera program
ms:assetid: 'b68ae4b2-b9ba-44ae-90cb-c88df600ec86'
ms:contentKeyID: 18124872
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747644(v=WS.10)'
---

Exkludera program
=================

Du kan ange mot vilken version av ett RMS-aktiverat program alla licensieringsbegäran ska kontrolleras. Genom programexkludering märks alla användarlicenser med ett villkor om att licensen bara kan bindas till det RMS-skyddade innehåll som den utfärdades för, om programmet som begär licensen inte ingår i exkluderingslistan.

Det här kan t.ex. vara användbart när ett företag distribuerar en säkerhetsuppdatering för ett program. Systemadministratörer kan använda de vanliga metoderna för att få klientdatorer att installera säkerhetsuppdateringen. De kan sedan konfigurera principer för programexkludering som definieras med hjälp av versionsinformationen för det program som används på administrationswebbplatsen. Den här exkluderingsprincipen hindrar att licenser utfärdas i RMS till klienter som kör tidigare versioner av programvaran.

RMS-aktiverade program exkluderas med utgångspunkt i programmets filnamn och versionsnummer. Det kan användas för att garantera att användarna installerar en senare och säkrare version av ett program när ett sådant är tillgängligt. Som exempel kanske ett RMS-aktiverat program i version 1.0.4.2315 distribueras i organisationen. Sedan upptäcker programutvecklaren ett säkerhetsproblem och utfärdar version 1.0.4.4200, där det problemet åtgärdas. Utöver implementationen av den nya versionen kan du även upprätta en exkluderingsprincip som förhindrar att användare använder skyddat innehåll med den tidigare versionen av programmet.

Liksom för andra typer av exkludering måste du konfigurera exkludering av program i varje kluster där du vill att funktionen ska gälla.

När du tillämpar den här exkluderingsprincipen på servern kan inte klienter som använder det exkluderade programmet begära nya licenser eller binda dem till RMS-skyddat innehåll. På klienterna går det däremot att fortsätta att använda tidigare licensierade filer med det exkluderade programmet.

| ![](images/Cc747644.note(WS.10).gif)Obs!                                                                                                                                                                                                                                            |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| I RMS krävs att programversionen anges i ett 4-siffrigt punktavgränsat format (\#.\#.\#.\# ). I vissa program anges dock programversionen i ett 2- eller 3-siffrigt punktavgränsat format. I så fall måste du lägga till .0 där det behövs så att versionsnumret stämmer överens med det format som krävs i RMS. |
