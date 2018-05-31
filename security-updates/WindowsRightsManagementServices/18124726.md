---
TOCTitle: Introduktion till inaktiveringsprocessen
Title: Introduktion till inaktiveringsprocessen
ms:assetid: '57bd9949-9433-437b-93ed-ffb2dff9992e'
ms:contentKeyID: 18124726
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720276(v=WS.10)'
---

Introduktion till inaktiveringsprocessen
========================================

Du kan se vilka tjänster som finns i RMS i IIS (Internet Information Services). Till exempel registreras användare och datorer i certifieringstjänsten, och i licensieringstjänsten publiceras innehåll och åtkomst delas ut till RMS-skyddad information. Inaktiveringstjänsten, som är en tilläggstjänst, måste vara aktiverad på RMS-servern för att inaktiveringsprocessen ska startas. När inaktiveringstjänsten är aktiverad avaktiveras alla andra RMS-tjänster på servern.

När inaktiveringstjänsten har aktiverats på RMS-servern kan ett program få en innehållsnyckel från inaktiveringstjänsten som gör att RMS-skyddat innehåll dekrypteras permanent i programmet.

När RMS-servern körs i inaktiverat läge kan användare med eller utan rättigheter till det ursprungliga RMS-skyddade innehållet få en innehållsnyckel och fullständiga rättigheter till innehållet.

När innehållet har dekrypterats ska användaren spara innehållet utan RMS-skydd. Notera att användaren måste registreras i RMS-infrastrukturen för att kunna använda inaktiveringstjänsten. Användare utan aktiverad RMS-klient kan inte använda inaktiveringstjänsten för att få tillgång till RMS-skyddat innehåll.
