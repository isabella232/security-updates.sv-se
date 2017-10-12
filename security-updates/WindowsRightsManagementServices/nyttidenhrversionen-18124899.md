---
TOCTitle: Nytt i den här versionen
Title: Nytt i den här versionen
ms:assetid: 'c68ec6fd-0ff5-467e-85a8-a53b9f089de3'
ms:contentKeyID: 18124899
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747748(v=WS.10)'
---

Nytt i den här versionen
========================

Rights Management Services (RMS) med Service Pack 1 (SP1) har funktioner för följande:

-   **Registrering av RMS-servern utan Internetanslutning**. I föregående version var du tvungen att ansluta RMS-servern till Internet för att kunna registrera den med Microsofts registreringstjänst och på så sätt få licensieringscertifikatet för rotservern. I RMS SP1 måste licensieringscertifikatet för rotservern fortfarande begäras från Microsofts registreringstjänst, men det kan begäras från en annan dator med Internetanslutning och sedan importeras till RMS-servern efter etablering.
-   **Klienterna är självaktiverande**. I föregående version var du tvungen att hämta datorcertifikat och lockboxar för klientdatorer från Microsofts aktiveringstjänst. Med RMS SP1 behövs inte någon anslutning till Microsofts aktiveringstjänst
-   **Funktioner för fler klienttyper**. I den här versionen kan RMS-servern användas till klienter på mobila enheter och till servertjänster. Som RMS-serveradministratör kan du bestämma om servern ska certifiera de här klienterna när de försöker använda tjänsterna.
-   **Funktioner för flerspråkiga mallar**. I föregående version baserades mallarna på språkinställningen i Internet Explorer. I den här versionen kan du på webbsidan för RMS-administration ange vilket språk som ska användas när du skapar mallar.
-   **Funktioner för klientautentisering med smartkort**. I den här versionen kan autentiseringsuppgifter som lagrats som x.509-certifikat på smartkort användas vid autentisering på RMS-servern vid tilldelning av rättighetskontocertifikat och användning av licenser.
