---
TOCTitle: Så här tar du bort RMS
Title: Så här tar du bort RMS
ms:assetid: '9fa63daa-5fb9-4afd-8371-b38248619857'
ms:contentKeyID: 18124852
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747706(v=WS.10)'
---

Så här tar du bort RMS
======================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

När du tar bort en server tas den bort ur tabellen ClusterServer i konfigurationsdatabasen. När den sista servern i ett kluster tas bort tas databasen för katalogtjänster bort från SQL Server. När den sista rotcertifikatservern i ett kluster tas bort måste du manuellt avregistrera certifieringstjänstens anslutningspunkt (SCP). Under borttagningen och avinstallationen tas inte SCP:n bort från Active Directory.

Om du väljer att avinstallera en rotcertifikatserver innan den är etablerad visas en varning om att etableringen av tjänsten på webbplatsen inte har tagits bort och att tjänstens anslutningspunkt inte tas bort från Active Directory. Om du fortsätter genom att välja **Ja** tas etableringen bort på webbplatsen. Avinstallationen gör inte att tjänstens anslutningspunkt tas bort från Active Directory.

Ta bort RMS
-----------

#### Så här tar du bort RMS

1.  Logga in på den server som du vill ta bort RMS från.

2.  Öppna sidan **Global administration**.

3.  Klicka på **Ta bort RMS från den här webbplatsen** bredvid den webbplats där RMS är etablerat och klicka sedan på **OK**.

4.  Klicka på **Avregistrera URL** på webbsidan för RMS-tjänstens anslutningspunkt och avregistrera certifieringstjänstens anslutning från Active Directory.
