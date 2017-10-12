---
TOCTitle: 'Publicering av RMS-tjänster'
Title: 'Publicering av RMS-tjänster'
ms:assetid: '3cca9325-6bd3-49ad-aa3f-e0693205d3f4'
ms:contentKeyID: 18124686
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720247(v=WS.10)'
---

Publicering av RMS-tjänster
===========================

RMS-tjänsternas URL:er publiceras för Active Directory när servrarna etableras. Vid etableringen skickas en fråga från installationsprogrammet för RMS till Active Directory för att kontrollera om det finns andra RMS-servrar installerade i samma skog. Om inga andra RMS-servrar har installerats konfigureras servern som rotcertifikatserver. Innan du kan använda RMS måste du registrera anslutningspunkten i Active Directory, som gör att klienterna kan identifiera rotcertifikatserverns URL. Klienter som begär anslutning till tjänster som körs på rotcertifikatservern börjar med att tillfråga Active Directory om denna URL. Mer information finns i ”Registrera RMS-tjänstens anslutningspunkt” i ”Använda en RMS-server”.

| ![](images/Cc720247.note(WS.10).gif)Obs!                                                                                                                    |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om topologin innehåller flera servrar som bildar ett rotcertifieringskluster, pekar URL:en på den belastningsfördelande servern i klustret som administratören avdelar vid etableringen. |
