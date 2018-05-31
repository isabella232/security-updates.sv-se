---
TOCTitle: 'Exkludera lockbox-versioner'
Title: 'Exkludera lockbox-versioner'
ms:assetid: 'e287f026-aab2-43ab-93bc-48087da82f36'
ms:contentKeyID: 18124929
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747700(v=WS.10)'
---

Exkludera lockbox-versioner
===========================

Du kan se till att klienter tvingas använda en tidigaste version av RMS-klientprogramvaran genom att använda den lockbox-version som är associerad med klienten, så att tidigare versioner av RMS-klientprogramvaran exkluderas. När du aktiverar den här funktionen anger du den senaste lägsta version av lockbox som har signerats i Microsofts aktiveringstjänst. Du aktiverar sedan exkludering av lockbox på administrationswebbplatsen för varje kluster där du vill att funktionen ska gälla. Alla certifierings- och licensieringsbegäran kontrolleras, så att kravet på tidigaste version av lockbox garanterat uppfylls.

Om du har aktiverat exkludering baserat på lockbox-version så kan inte klienter där en tidigare lockbox-version används än den version du angav hämta rättighetskontocertifikat eller använda användarlicenser eftersom deras begäran nekas. För sådana klienter måste en ny version av RMS-klientprogramvaran installeras så att en ny lockbox fås där den aktuella versionen av programvaran används.

I RMS-klienten för Service Pack 1 (SP1) används en lockbox-version som är större än eller lika med 5.0.0.0. Genom att ange exkludering av lockbox till tidigaste version tvingar du RMS-klienterna i organisationen att uppgraderas till RMS-klienten för SP1 om det ska gå att använda RMS-skyddat innehåll.

Om användare med exkluderade lockbox-versioner tidigare har fått licenser utfärdade kan de fortfarande använda innehållet utan att hämta någon ny lockbox-version.
