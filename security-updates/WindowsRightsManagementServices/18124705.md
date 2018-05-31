---
TOCTitle: Aktivera inaktiveringstjänsten
Title: Aktivera inaktiveringstjänsten
ms:assetid: '45226e85-b50d-41cc-aca7-0f603f8509d5'
ms:contentKeyID: 18124705
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720261(v=WS.10)'
---

Aktivera inaktiveringstjänsten
==============================

Vid inaktivering av RMS-systemet behövs den privata nyckel som används till att skydda all publicerad information. Den privata nyckeln lagras i konfigurationsdatabasen med DPAPI-kryptering (Data Protection API) och baseras på det lösenord som angavs vid etableringen. Om den privata nyckeln för RMS lagras på en HSM lagras den privata nyckeln i HSM i stället för i konfigurationsdatabasen.

| ![](images/Cc720261.Caution(WS.10).gif)Varning!                                                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Vid inaktivering av RMS-systemet ser du till att du kan lösenordet för den privata nyckeln. Om du inte kan lösenordet ska du återställa lösenordet för den privata nyckeln innan du inaktiverar RMS-servern. |

Första steget vid borttagning av RMS-systemet är att inaktivera servrarna i klustret. Eftersom inaktivering är en licensfunktion kan en server i ett underregistrerat RMS-licenskluster inaktiveras utan att det påverkar RMS-rotklustret eller något annat underregistrerat RMS-licenskluster. Därför måste du inaktivera RMS-rotklustret och eventuella licenskluster separat eftersom varje licenskluster har en egen privat nyckel som används till att skapa publiceringslicenser.

Så här aktiverar du inaktiveringstjänsten:

1.  Gå till webbplatsen Administration av Windows RMS.
2.  Klicka på **Administrera RMS** och därefter på **Säkerhetsinställningar**.
3.  Markera kryssrutan vid **Inaktiverar RMS-installationen**.
4.  Klicka på **OK** i dialogrutan så bekräftas inaktiveringsprocessen.

Det går inte att återställa en inaktiverad server till en standard-RMS-konfiguration. Det går inte att ångra den här processen.

När du har inaktiverat RMS måste du ta bort det fullständigt genom att klicka på **Lägg till eller ta bort program** innan du försöker installera en ny förekomst av RMS.
