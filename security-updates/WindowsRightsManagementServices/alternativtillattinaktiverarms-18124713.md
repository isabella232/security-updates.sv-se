---
TOCTitle: Alternativ till att inaktivera RMS
Title: Alternativ till att inaktivera RMS
ms:assetid: '4d32f35e-997d-4d10-ab66-efe217e853f7'
ms:contentKeyID: 18124713
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720268(v=WS.10)'
---

Alternativ till att inaktivera RMS
==================================

Om du planerar för fortsatt användning av RMS i organisationen men behöver sluta använda vissa RMS-servrar av någon anledning kan du överväga följande alternativ till inaktivering.

**Konfigurera en betrodd publiceringsdomän**

All RMS-skyddad information krypteras med den privata nyckeln på RMS-servern. Med en betrodd publiceringsdomän kan du importera en privat nyckel från en RMS-server till en annan. Det gör att användarlicenser kan utfärdas från RMS-servern mot publiceringslicenser som har utfärdats av en annan RMS-server. När nyckeln har exporterats kan servern inaktiveras och avinstalleras.

**Konfigurera gruppen RM-ansvariga**

Om det RMS-skyddade innehållet inte kan öppnas på grund av att användarna saknar rättigheter till innehållet kan du bevilja full kontroll över allt RMS-skyddat material som publiceras via servern till gruppen RM-ansvariga. Medlemmar i gruppen RM-ansvariga tilldelas fullständiga ägarrättigheter i alla användarlicenser som utfärdas av den RMS-server eller det RMS-kluster där gruppen RM-ansvariga finns. Det innebär att medlemmar i den här gruppen kan dekryptera alla skyddade filer och att de även kan ta bort skyddet från dessa filer. Medlemmar av den här gruppen kan t.ex. ta bort skyddet från filer som har publicerats av en anställd som har slutat, så att en ny ägare kan publicera och hantera dessa filer.

Gruppen RM-ansvariga innehåller inte automatiskt några medlemmar, inte ens administratörer inkluderas. Den här gruppen måste vara en distributionsgrupp i Active Directory med ett e-postnamn som exakt matchar gruppnamnet i formatet ”*gruppnamn*@*domännamn*.com”. Gruppnamnet måste vara exakt samma som e-postadressattributet och är skiftlägeskänsligt.
