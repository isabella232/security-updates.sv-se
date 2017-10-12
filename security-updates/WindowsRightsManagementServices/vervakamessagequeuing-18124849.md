---
TOCTitle: Övervaka Message Queuing
Title: Övervaka Message Queuing
ms:assetid: 'a7109399-3a84-4681-874b-f6ea1646b0a0'
ms:contentKeyID: 18124849
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747716(v=WS.10)'
---

Övervaka Message Queuing
========================

Med RMS-loggning används Message Queuing (kallas även MSMQ) till att skicka händelser till loggningsdatabasen. Varje RMS-frontserver skickar meddelanden till Message Queuing-tjänsten, och lyssnartjänsten för loggning på varje frontserver hämtar loggningsmeddelanden från Message Queuing-kön och skriver dem till loggningsdatabasen. Om det inte går att komma åt loggningsdatabasen eller databasservern, eller om lyssnartjänsten för loggning stoppas, lagras meddelandena i kön av Message Queuing. Om du tänker stänga av loggningsdatabasen eller databasservern rekommenderar vi att du först stänger av lyssnartjänsten för loggning på varje frontserver. Starta sedan om lyssnartjänsten för loggning på varje frontserver när databasen eller databasservern har startats.

Om databasen slutar fungera medan lyssnartjänsten för loggning fortfarande körs går det inte att skriva några loggningsmeddelanden till databasen i lyssnartjänsten. Meddelandena flyttas då till en Message Queuing-kö med ”förlorade” meddelanden tills databasen är tillgänglig igen. I det här läget skrivs nya loggningsmeddelanden till databasen. Meddelanden i kön med förlorade meddelanden skrivs inte automatiskt till loggningsdatabasen. Gör så här om du vill visa och ta bort meddelanden i kön med förlorade meddelanden:

1.  Öppna MMC-snapin-modulen Datorhantering genom att klicka på **Start**, peka på **Alla program**, peka på **Administrationsverktyg** och sedan klicka på **Datorhantering**.
2.  Klicka på MSMQ under Tjänster och program i konsolträdet och klicka sedan på Privata köer.
3.  Två köer visas. Båda har ett namn som börjar med **drms\_logging** följt av namnet på det aktuella klustret. En av köerna har namnet **drms\_logging\_***&lt;klusternamnet&gt;***\_deadletter**. Det är kön med förlorade meddelanden. Klicka på könamnet och klicka sedan på Kömeddelanden.
4.  Dubbelklicka på varje meddelande vars egenskaper du vill se.
5.  Högerklicka på **Kömeddelanden**, markera **Alla aktiviteter** och klicka sedan på **Töm** om du vill ta bort kön.

I standardkonfigurationen lagras alla meddelanden i kö med Message Queuing tills det inte längre finns något ledigt utrymme kvar på servern. Om Message Queuing förbrukar allt tillgängligt hårddiskutrymme går det inte att hantera klientbegäran med RMS-servern. Du förhindrar det här genom att begränsa den mängd diskutrymme som Message Queuing får använda för meddelanden i kö. Gör så här:

1.  Öppna MMC-snapin-modulen Datorhantering genom att klicka på Start, peka på Alla program, peka på Administrationsverktyg och sedan klicka på Datorhantering.
2.  Klicka på MSMQ under Tjänster och program i konsolträdet och klicka sedan på Privata köer.
3.  Två köer visas. Båda har ett namn som börjar med drms\_logging. Utför följande steg för båda köerna:
    -   Klicka på Egenskaper.
    -   Markera kryssrutan Begränsa meddelandelagring till (kB) och ange sedan den totala maximala storleken, i kilobyte, för meddelanden som kan lagras i kön.

Om en kö fylls ignoreras nya meddelanden från RMS när de anländer och följande händelsemeddelande, som är associerat med händelse-ID 48, skickas till systemets händelselogg:

”Det gick inte att skicka egenskapsmängden till Message Queuing.”

Du bör konfigurera verktygen för systemövervakning så att en avisering skickas när den här händelsen inträffar, eftersom den är ett tecken på att det har uppstått ett fel med loggningsdatabasen.
