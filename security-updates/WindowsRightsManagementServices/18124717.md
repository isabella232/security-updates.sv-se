---
TOCTitle: Så här exporterar du en betrodd användardomän
Title: Så här exporterar du en betrodd användardomän
ms:assetid: '40281ba3-2674-43ca-aa6d-1deb9302eb0e'
ms:contentKeyID: 18124717
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720259(v=WS.10)'
---

Så här exporterar du en betrodd användardomän
=============================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Med betrodda användardomäner kan användare tilldelas licenser från en RMS-server när de har rättighetskontocertifikat som beviljats från en annan RMS-server.

Exportera en betrodd användardomän
----------------------------------

#### Så här exporterar du en betrodd användardomän

1.  På sidan **Principer för förtroenden** klickar du på **Exportera** i området **Betrodda användardomäner**.

2.  Dialogrutan **Filhämtning** visas. Klicka på **Spara**.

3.  Dialogrutan **Spara som** visas. Vi rekommenderar att du ändrar bin-filnamnet till att innehålla namnet på servern du använder, t.ex. RMS\_server1\_licenscert.bin.

    Filen sparas på skrivbordet som standard. Du kan ange en annan plats om du vill.

4.  Klicka på **Spara** så sparas filen på den plats du har angett.

Mer information om hur du utför den här processen finns i ”[Lägga till och ta bort betrodda användardomäner](https://technet.microsoft.com/7c440b15-01c4-49f1-b43c-00f67f3388c1)” tidigare i det här avsnittet.
