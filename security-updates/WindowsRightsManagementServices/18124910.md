---
TOCTitle: 'Ändra den privata RMS-nyckeln'
Title: 'Ändra den privata RMS-nyckeln'
ms:assetid: 'da32137e-394a-42b2-9552-ba20f4547c23'
ms:contentKeyID: 18124910
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747765(v=WS.10)'
---

Ändra den privata RMS-nyckeln
=============================

Vid etableringen skapas den privata RMS-nyckeln för servern. Den privata RMS-nyckeln krypteras och lagras i konfigurationsdatabasen. Du bör säkerhetskopiera och lagra den privata nyckeln på en säker plats. Dessutom bör du skydda den privata RMS-nyckeln med en HSM (Hardware Security Module) eftersom nyckeln används i krypteringsschemat för allt innehåll som skyddas av RMS-servern. Om den privata RMS-nyckeln har komprometterats måste du ta bort RMS på servern och sedan etablera RMS igen för att få en ny privat RMS-nyckel.

Om servern användes till att skydda innehåll ska alla ägare av innehåll meddelas, och innehållet bör publiceras på nytt på RMS-servern där den nya privata nyckeln används. Eventuella kopior av innehåll som skyddats med hjälp av den komprometterade privata nyckeln måste förstöras eftersom de inte har tillräckligt skydd.

| ![](images/Cc747765.Important(WS.10).gif)Viktigt!                                                                                                                                                                                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oavsett om servern har registrerats med Microsofts registreringstjänst eller inte måste etableringsprocessen upprepas på servern så att en ny privat nyckel erhålls. Om du bara försöker registrera RMS-servern igen kommer den tidigare privata RMS-nyckeln att användas. |
