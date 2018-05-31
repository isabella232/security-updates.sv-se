---
TOCTitle: Underregistrering av licensieringsservrar
Title: Underregistrering av licensieringsservrar
ms:assetid: '7bc63397-9186-464c-8824-867038adce9b'
ms:contentKeyID: 18124782
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747640(v=WS.10)'
---

Underregistrering av licensieringsservrar
=========================================

Licensieringsservrar registreras automatiskt vid etableringen genom en process som kallas underregistrering. När du lägger till en ny server i ett licensieringskluster underregistreras den dock inte i direkt mening, eftersom klustrets serverlicensieringscertifikat och konfigurationsdatabas används.

I stället för att skicka en begäran om underregistrering till Microsofts registreringstjänst skickar licensieringsservern begäran till rotcertifikatservern. En begäran om underregistrering av en licensieringsserver är identisk med en begäran om registrering av rotcertifikatservern.

När rotcertifikatservern tar emot en begäran om underregistrering valideras att begäran är korrekt utformad. Därefter lämnas en certifikatkedja ut som innehåller rotcertifikatserverns licensieringscertifikatkedja och ett certifikat som signerats av rotcertifikatservern. Certifikatet innehåller serverns offentliga nyckel som signerats med rotcertifikatserverns privata nyckel. Certifikatet ger licensieringsservern rättighet att utfärda användar- och publiceringslicenser.

Serverlicensieringscertifikatet är giltigt i ett år. Giltighetsperioden börjar när certifikatet utfärdas. Certifikatet kan förnyas vid slutet av giltighetsperioden. Certifikat och licenser som utfärdas av servern är giltiga i sju år. Giltighetsperioden börjar när certifikatet eller licensen utfärdas.

Som standard är den tjänst som krävs för att behandla en begäran om underregistrering på rotcertifikatservern, SubEnrollService.asmx, konfigurerad så att all åtkomst nekas. För att en begäran ska kunna behandlas måste du ändra DACL-listorna så att RMS-administratörer får åtkomsträttigheter.
