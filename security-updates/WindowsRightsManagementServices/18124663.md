---
TOCTitle: 'Inaktivera RMS-servrar'
Title: 'Inaktivera RMS-servrar'
ms:assetid: '11badb02-62c1-455c-96b7-935bbcb496bc'
ms:contentKeyID: 18124663
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720200(v=WS.10)'
---

Inaktivera RMS-servrar
======================

När du inaktiverar RMS ändras RMS-serverns funktion så att du kan tillhandahålla en nyckel som används till att dekryptera det RMS-skyddade innehåll som har publicerats. Med den nyckeln kan innehållet sparas utan RMS-skydd. Det är användbart om du bestämmer dig för att inte längre använda RMS-skydd i organisationen.

Kör servern i inaktiverat läge tillräckligt länge för att alla användare ska ha möjlighet att spara sitt innehåll utan RMS-skydd och så att nätverks- och systemadministratörer hinner inaktivera RMS-skyddet på alla klienter där tjänsten används.

Du kan inaktivera RMS från webbsidan **Säkerhetsinställningar** på administrationswebbplatsen. Det går inte att återställa en inaktiverad server till en standard-RMS-konfiguration. Om installationen dessutom ingår i betrodda publiceringsdomäner inaktiveras även dessa.

Efter inaktiveringen innehåller administrationswebbplatsen bara sidan **Inaktivering av RMS**. Inga övriga administrationsfunktioner finns. Du måste utföra följande steg för att slutföra inaktiveringen av servern:

1.  Ge **RMS Service Group** läs- och körbehörighet till den virtuella inaktiveringsroten.
2.  Lägg till gruppen **Alla** i DACL-listan för filen decommissioning.asmx och ge gruppen läsbehörighet.
3.  Informera användarna om att du inaktiverar RMS-installationen och be dem att ansluta sig till servern och spara sitt innehåll utan RMS-skydd.
4.  Konfigurera alla RMS-aktiverade program i företaget så att de ansluts till sidan decommissioning.asmx. Beroende på vilket RMS-aktiverat program det är kan detta kontrolleras via en registernyckel- eller gruppolicyinställning.
5.  Om organisationen använder RMS-aktiverade program där installationen används för publicering automatiskt ska du en använda en grupprincip till att ange en registerpost på de datorer där dessa program är installerade så att programmen använder inaktiveringstjänsten.
6.  När inget innehåll längre skyddas säkerhetskopierar du serverns privata nyckel och avinstallerar sedan RMS från servern.
