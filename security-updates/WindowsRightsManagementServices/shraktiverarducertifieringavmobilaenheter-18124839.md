---
TOCTitle: Så här aktiverar du certifiering av mobila enheter
Title: Så här aktiverar du certifiering av mobila enheter
ms:assetid: '93ec088e-9056-4c3c-bd97-1173fb194578'
ms:contentKeyID: 18124839
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747603(v=WS.10)'
---

Så här aktiverar du certifiering av mobila enheter
==================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Processen kan bara användas för rotcertifikatklustret.

Den här processen förutsätter att du har skapat en användargrupp som innehåller användarkontona för användare av mobila enheter som använder RMS-skyddat innehåll.

Aktivera certifiering av mobila enheter
---------------------------------------

#### Så här aktiverar du certifiering av mobila enheter

1.  På rotcertifikatservern öppnar du en webbläsare för filsystem och går till mappen &lt;systemenhet&gt;:\\Inetpub\\wwwroot\\\_wmcs\\Certification.

2.  Om du vill tilldela mobila enheter rättighetskontocertifikat (RAC) högerklickar du på filen MobileDeviceCertification.asmx och klickar sedan på **Egenskaper**.

3.  På fliken **Säkerhet** klickar du på **Lägg till** och lägger till den grupp du har skapat för användarkategorin och **RMS-tjänstgruppen**.

4.  I listan över **Behörigheter** för grupperna markerar du kryssrutan **Tillåt** för behörigheterna **Läs** och **Läs & kör** och klickar sedan på **OK**.
