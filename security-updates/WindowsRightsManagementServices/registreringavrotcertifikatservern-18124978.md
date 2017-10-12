---
TOCTitle: Registrering av rotcertifikatservern
Title: Registrering av rotcertifikatservern
ms:assetid: 'f08bc919-f090-4843-b2ce-b40d558012ce'
ms:contentKeyID: 18124978
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747734(v=WS.10)'
---

Registrering av rotcertifikatservern
====================================

Den första servern i en RMS-installation måste registreras via Microsofts registreringstjänst. Den servern är en rotcertifikatserver och kan registreras automatiskt när du etablerar servern om den är ansluten till Internet. Om servern ingår i ett slutet nätverk kan du registrera den manuellt. Mer information finns i ”Så här registrerar du en rotcertifikatserver manuellt” i ”Använda en RMS-server”.

En begäran om registrering har följande indataparametrar:

-   En 1024-bitars offentlig nyckel. Den här nyckeln är den offentliga RMS-nyckeln.
-   Version, namn och URL för den RMS-server som ska registreras.

Microsofts registreringstjänst använder endast informationen till att skapa serverlicensieringscertifikatet och sparar den enbart för att medge återkallning av certifikatet.

Microsofts registreringstjänst lämnar ut en certifikatkedja som innehåller registreringsserverns licensieringscertifikatkedja samt ett certifikat som signerats av registreringsservern. Certifikatet innehåller serverns offentliga nyckel som signerats med registreringstjänstens privata nyckel och den registrerade serverns version och URL. Certifikatet ger rättigheter till rotcertifikatservern att utfärda serverlicensieringscertifikat till licensieringsservrar, rättighetskontocertifikat, klientlicensieringscertifikat samt publicerings- och användarlicenser.

Serverlicensieringscertifikatet är giltigt i ett år. Giltighetsperioden börjar när certifikatet utfärdas. Certifikatet kan förnyas vid slutet av giltighetsperioden. Certifikat och licenser som utfärdas av servern är giltiga i sju år. Giltighetsperioden börjar när certifikatet eller licensen utfärdas.

Information om återkallning av certifikatet läggs till i serverlicensieringscertifikatet så som den anges i begäran om registrering. Den offentliga nyckeln för Microsofts registreringstjänst läggs till i certifikatet som en återkallelsenyckel. Om en återkallelsenyckel från tredje part anges läggs även den till i certifikatet som en återkallelsenyckel.
