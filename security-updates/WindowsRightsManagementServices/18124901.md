---
TOCTitle: Återställa lösenordet för den privata nyckeln
Title: Återställa lösenordet för den privata nyckeln
ms:assetid: 'ceba927e-a7fd-4b06-bb70-5e5d9d6d099c'
ms:contentKeyID: 18124901
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747675(v=WS.10)'
---

Återställa lösenordet för den privata nyckeln
=============================================

När du etablerar en server anger du en metod för att skydda den privata RMS-nyckeln. Om du valde det programvarubaserade standardskyddet för privata nycklar angav du ett starkt lösenord som användes för kryptering av serverns privata nyckel i konfigurationsdatabasen. Om du glömmer bort lösenordet kan en medlem av gruppen RM-ansvariga återställa det enligt beskrivningen i avsnittet ”[Så här återställer du lösenordet för den privata nyckeln](https://technet.microsoft.com/f71df255-fe19-4e07-810e-87309a5e8e88)” senare i det här avsnittet.

Om du kör RMS i klustermiljö måste du återställa den privata nyckeln på alla RMS-frontservrar i installationen. Om du inte gör det kommer inte servrarna att fungera eftersom de inte kan dekryptera servernyckeln i konfigurationsdatabasen.

Mer information om starka lösenord finns i Hjälp- och supportcenter i Windows Server 2003.
