---
TOCTitle: Så här aktiverar du certifiering av servertjänster
Title: Så här aktiverar du certifiering av servertjänster
ms:assetid: '0ed78c85-7acb-4e3b-a594-613f8ccb5b14'
ms:contentKeyID: 18124660
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720196(v=WS.10)'
---

Så här aktiverar du certifiering av servertjänster
==================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen för att kunna utföra den här processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Processen kan bara användas för rotklustret.

Den här processen förutsätter att du har skapat en användargrupp som innehåller de användarkonton som servertjänsterna personifierar när de använder rättighetsskyddat innehåll.

Aktivera certifiering av servertjänster
---------------------------------------

#### Så här aktiverar du certifiering av servertjänster

1.  Logga in på datorn som en medlem av den lokala administratörsgruppen.

2.  Öppna en webbläsare för filsystem och gå till mappen &lt;systemenhet&gt;:\\Inetpub\\wwwroot\\\_wmcs\\Certification.

3.  Om du vill tilldela servertjänster rättighetskontocertifikat (RAC) högerklickar du på filen ServerCertification.asmx och klickar sedan på **Egenskaper**.

4.  På fliken **Säkerhet** klickar du på **Lägg till** och lägger till den grupp du har skapat för användarkategorin och **RMS-tjänstgruppen**.

5.  I listorna över **Behörigheter** för grupperna markerar du kryssrutan **Tillåt** för behörigheterna **Läs & Kör** och klickar sedan på **OK**.

6.  Steg 1 - 4 ska upprepas för varje server i klustret.

| ![](images/Cc720196.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| För Microsoft Exchange Server 2007 måste du lägga till varje Bridgehead-servers Active Directory-datorobjekt i DACL-listan (Discretionary Access Control) för ServerCertification.asmx. På samma sätt måste du för Microsoft Office SharePoint Server 2007 lägga till Office SharePoint Server 2007-serverns Active Directory-datorobjekt i DACL-listan. Vi rekommenderar att du lägger till en säkerhetsgrupp till den här DACL-listan och lägger till lämpliga datorobjekt i den. |
