---
TOCTitle: 'Så här ändrar du RMS-proxyinställningarna'
Title: 'Så här ändrar du RMS-proxyinställningarna'
ms:assetid: '8f50bd4d-26b1-4996-b361-722ee21607f3'
ms:contentKeyID: 18124831
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747594(v=WS.10)'
---

Så här ändrar du RMS-proxyinställningarna
=========================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Mer information om metoder för proxyserver-autentisering och hur de fungerar i Windows Server 2003 finns i hjälpen för Internet Information Services.

Ändra RMS-proxyinställningarna
------------------------------

#### Så här ändrar du RMS-proxyinställningarna

1.  Öppna sidan **Global administration** och klicka sedan på länken **Administrera RMS på den här webbplatsen**.

2.  Under **Klusteradministration** klickar du på länken **Säkerhetsinställningar**.

3.  Markera kryssrutan **Datorn ansluter till Internet via en proxyserver** om du inte tidigare har använt en proxyserver med RMS. Ytterligare inställningar som du måste fylla i visas på sidan.

4.  Skriv in IP-adressen till eller DNS-namnet på den proxyserver som du vill använda i rutan **Adress**.

5.  Skriv in det portnummer som används i proxyservern till att ansluta till Internet i rutan **Port**.

6.  Om du inte använder proxyservern när du ansluter till lokala resurser markerar du kryssrutan **Använd inte proxyserver för lokala adresser**.

7.  Markera kryssrutan **Den aktuella proxyservern kräver autentisering** om det är aktuellt.

    -   Välj aktuell autentiseringstyp i listan, antingen **Grundläggande**, **Sammanfattad** eller **Integrerad Windows**.
    -   Skriv in det användarnamn som ska anges i svar till proxyservern vid **Användarnamn**.
    -   Skriv in det lösenord som ska anges i svar till proxyservern vid **lösenord**.
    -   Skriv in lösenordet som du angav tidigare vid **Bekräfta lösenord** som en bekräftelse på att du skrev in det direkt.
    -   Ange vilken domän användaren tillhör vid **Domän** om proxyservern använder Windows-integrerad autentisering.

8.  Klicka på **Skicka**.
