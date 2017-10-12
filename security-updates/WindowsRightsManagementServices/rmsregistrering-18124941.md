---
TOCTitle: 'RMS-registrering'
Title: 'RMS-registrering'
ms:assetid: '999db3e1-e3ab-4513-87d9-d584ee334c00'
ms:contentKeyID: 18124941
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747698(v=WS.10)'
---

RMS-registrering
================

Vid registrering av en server skapas ett serverlicensieringscertifikat som därefter lämnas ut till servern. Med serverlicensieringscertifikat bekräftas identiteten på de servrar som ingår i systemet samt att identitetskontroll utförs vid användning av RMS-skyddat innehåll. Den första servern i varje licensieringskluster registreras med rotcertifikatklustret som en del i etableringsprocessen. Efterföljande servrar i klustret registreras inte separat.

Den första servern i ett rotcertifikatkluster (rotcertifikatservern) måste registreras i Microsofts registreringstjänst. Den proceduren kan utföras automatiskt som en del av etableringen om rotcertifikatservern är ansluten till Internet. Registreringsprocessen kan också genomföras offline om du exporterar en begäran till en fil, som sedan skickas till Microsofts registreringstjänst från en annan dator som har Internetuppkoppling. När registreringsbegäran har skickats får du tillbaka ett serverlicensieringscertifikat till rotcertifikatservern som kan importeras via administrationswebbsidorna för RMS.

Registreringsbegäran innehåller följande information:

-   Information om återkallning. Om RMS-installationen ska användas för standardåterkallning eller anpassad återkallning (från tredje part). Om återkallning från tredje part används inkluderas återkallningsrättighetens offentliga nyckel.
-   Certifikatets offentliga nyckel. Serverlicensieringscertifikatets offentliga nyckel. Den här offentliga nyckeln genereras på RMS-servern och skickas till Microsofts registreringstjänst, så att serverlicensieringscertifikatet hämtas.
-   SKU. Det officiella SKU-namnet för RMS.
-   Version. Versionsnumret för RMS-paketet.
-   URL. RMS-serverklustrets bas-URL.

När ett svar på registreringsbegäran skickas från Microsofts registreringstjänst lämnas följande information till RMS-servern i XML-format:

-   Serverlicensieringscertifikat.
-   Certifikatkedja av signeringsrättigheter.

Samma information skickas oavsett om RMS-rotcertifikatservern registreras med online- eller offlinemetoden. Ingen extra information sammanställs med någon av metoderna.

En beskrivning av stegen vid serverregistrering offline finns i ”Använda offlineregistrering till att registrera en rotcertifikatserver” i ”Använda en RMS-server”.

Vid registrering av en klient skapas ett klientlicensieringscertifikat som därefter lämnas ut till klienten. Certifikatet tillåter en användare att publicera RMS-skyddat innehåll från en dator som inte är ansluten till företagets nätverk. En användare kan begära ett klientlicensieringscertifikat när som helst. Det finns inget krav på att klienter ska registreras.

Alla begäran om registrering loggas.

Avsnittet behandlar:

-   [Registrering av rotcertifikatservern](https://technet.microsoft.com/f08bc919-f090-4843-b2ce-b40d558012ce)
-   [Underregistrering av licensieringsservrar](https://technet.microsoft.com/7bc63397-9186-464c-8824-867038adce9b)
-   [RMS-klientregistrering](https://technet.microsoft.com/9c1d07bf-7235-4694-8291-ac2e5b221f4a)
-   [RMS-datoraktivering](https://technet.microsoft.com/09a0d631-9860-477f-9d10-df61b3bfe125)
-   [RMS-kontocertifiering](https://technet.microsoft.com/c9a385c5-6dbb-47f5-a80f-69718e6f9deb)
