---
TOCTitle: Så här fungerar återkallning i RMS
Title: Så här fungerar återkallning i RMS
ms:assetid: '469e3938-a59b-4c92-9779-ead64e724d00'
ms:contentKeyID: 18124702
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720263(v=WS.10)'
---

Så här fungerar återkallning i RMS
==================================

En återkallning verkställs genom att bindning, d.v.s. den process som tillåter en användare att använda innehåll, förhindras när en återkallad enhet är inblandad i en begäran om bindning. Återkallning verkställs med hjälp av listor över återkallade certifikat som distribueras till klientdatorer. Dessa listor är signerade XrML-filer som anger innehåll, program, användare och andra enheter som har återkallats av den enhet som utfärdar listan.

Varje gång en användare försöker använda skyddat innehåll skickar det RMS-aktiverade programmet en begäran om rättigheter i en bindningsbegäran till RMS-klienten. Om användaren t.ex. försöker öppna en fil görs en begäran i programmet om rättighet att visa innehållet, vilket gör det möjligt att öppna filen. Om användaren försöker göra ändringar i filen begär programmet rättighet att redigera innehållet.

Vid behandlingen av en bindningsbegäran går RMS-klienten igenom följande steg:

1.  Klientkomponenten kontrollerar om användarlicensen kräver någon återkallelselista.
2.  Om användarlicensen kräver en återkallelselista kontrollerar klientkomponenten om den angivna listan finns, om den är registrerad och om den är aktuell enligt den giltighetstid som angetts i användarlicensen.
3.  Klientkomponenten kontrollerar att den enhet som signerat återkallelselistan har angetts i användarlicensen som en enhet med rättighet att återkalla licensen.
4.  Om dessa kontroller lyckas undersöker klientkomponenten om någon enhet som är inblandad i den ursprungliga bindningsbegäran har återkallats. Om så är fallet nekar klientkomponenten denna begäran.

Listor över återkallade certifikat kan distribueras till klientdatorer av administratören eller hämtas till datorn av ett RMS-aktiverat program när en användarlicens kräver det. När en lista över återkallade certifikat används till att binda innehåll registreras den och kan sedan användas för bindningsbegäran med andra användarlicenser så länge programmet är öppet. När programmet avslutas avregistreras återkallelselistan.

I följande figur beskrivs bindningsprocessen och återkallelsefunktionen.

![](images/Cc720263.81aa2d70-d261-49ad-b446-96a2eddba1a5(WS.10).gif)

Återkallelse är en valfri funktion. RMS-administratören kan kräva att återkallning ska kunna ske genom att ange det i en eller flera av företagets principmallar för rättigheter. När återkallelse krävs kan en licens inte bindas om inte den krävda återkallelselistan finns, är registrerad på användarens dator och inte har överskridit det sista giltighetsdatum som angetts i användarlicensen.

Det är dock viktigt att notera att återkallelser fortfarande kan verkställas för en viss användarlicens även om den inte kräver det. En återkallning verkställs när en utfärdare av ett certifikat i den förtroendekedja som är inblandad i en bindningsbegäran har utfärdat en listan över återkallade certifikat som är registrerad på en klientdator. I sådana fall används listan över återkallade certifikat till att behandla bindningsbegäran även om de inblandade användarlicenserna inte kräver återkallning. Det gäller tills det RMS-aktiverade programmet avslutas, vilket medför att listan över återkallade certifikat avregistreras.

Om en användare t.ex. försöker använda innehåll vars användarlicens, som utfärdats av enhet A, kräver en listan över återkallade certifikat som utfärdats av enhet A, hämtar det RMS-aktiverade programmet listan över återkallade certifikat från den URL som anges i användarlicensen och registrerar sedan listan. När RMS-klienten behandlar en bindningsbegäran kontrollerar den om listan över återkallade certifikat innehåller några återkallningar.

Användaren, som lämnat det RMS-aktiverade programmet öppet, försöker sedan använda ett annat innehåll vars användarlicens också utfärdats av enhet A. Trots att denna användarlicens inte innehåller något återkallningsvillkor är listan över återkallade certifikat från enhet A fortfarande registrerad på användarens dator. I detta fall kommer klientkomponenten att kontrollera återkallelselistan innan den behandlar någon bindningsbegäran.

Användaren försöker sedan använda ett innehåll vars användarlicens har utfärdats av enhet C. Användarlicensen innehåller inte något återkallelsevillkor. Eftersom den enda återkallelselista som är registrerad på klientdatorn är den som utfärdats av enhet A, och enhet A inte ingår i förtroendekedjan för användarlicensen, påverkas inte bindningen av någon återkallelse.

Slutligen stänger användaren det RMS-aktiverade programmet och öppnar senare det andra innehållet, som inte innehöll något återkallningsvillkor, på nytt. Eftersom listan över återkallade certifikat som utfärdats av enhet A avregistrerades när programmet stängdes, kontrolleras inte listan på RMS-klienten innan bindningsbegäran behandlas.
