---
TOCTitle: Så här registrerar du en anslutningspunkt för tjänst
Title: Så här registrerar du en anslutningspunkt för tjänst
ms:assetid: '630cc3c3-9ed9-4423-8874-cbaceb43b353'
ms:contentKeyID: 18124747
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720283(v=WS.10)'
---

Så här registrerar du en anslutningspunkt för tjänst
====================================================

Registrera en anslutningspunkt för tjänst
-----------------------------------------

Om du registrerar en anslutningspunkt för tjänst från en RMS-server i en underdomän kan du få ett felmeddelande som anger att SCP-registreringen misslyckades. Vanligtvis lyckades genomfördes registreringen korrekt, men registreringen genomförs först i toppdomänen och det tar tid för den att replikeras till den underdomän där RMS söker efter SCP-objektet. Meddelandet försvinner så snart SCP har replikerats till alla globala katalogservrar i skogen. Om det här felmeddelandet visas bör du vänta innan du försöker felsöka problemet för att se om det löser sig ändå.

#### Så här registrerar du en anslutningspunkt för tjänst

1.  Logga in på den server där du vill registrera en anslutningspunkt för tjänst. Använd ett domänkonto med behörigheter att skapa ett behållarobjekt under tjänstbehållaren i Active Directory-skogens konfigurationsbehållare. Den fördefinierade säkerhetsgruppen **Företagsadministratörer** är ett exempel på ett konto med tillräckliga behörigheter.

2.  Öppna sidan **Global administration** och klicka sedan på länken **Administrera RMS på den här webbplatsen**.

3.  Klicka på länken **RMS-tjänstens anslutningspunkt** på **administrationshemsidan**.

4.  På sidan för **RMS-tjänstens anslutningspunkt** klickar du på knappen för **registrering av URL**.
