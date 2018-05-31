---
TOCTitle: Identifiering av underregistreringstjänsten
Title: Identifiering av underregistreringstjänsten
ms:assetid: 'b159953a-af38-4a9e-8c87-1aff5fb4e366'
ms:contentKeyID: 18124870
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747641(v=WS.10)'
---

Identifiering av underregistreringstjänsten
===========================================

En begäran om underregistrering måste skickas från en enskild licensieringsserver, eller den första licensieringsservern i ett kluster, till rotcertifikatservern för RMS så att ett serverlicensieringscertifikat erhålls. Det här sker genom att URL:en för underregistreringstjänsten för rotcertifiering hämtas av licensieringsservern på följande sätt.

Vid etableringen av en licensieringsserver skickas en fråga från installationsprogrammet för RMS till Active Directory om tjänstanslutningspunkten för rotcertifikatklustret. RMS använder den URL som sparats i denna tjänstanslutningspunkt till att identifiera rotcertifieringsklustret. Sedan skickas en begäran om ett serverlicensieringscertifikat från rotcertifikatserverns underregistreringstjänst.

När programmet ska göra en begäran om underregistrering hämtar licensieringsservern först URL:en från Active Directory till den virtuella katalogen Certification på servern, där underregistreringstjänsten finns placerad. Därefter läggs sökvägen till underregistreringstjänsten till.

URL:en för den virtuella katalogen Certification på rotcertifikatservern sparas i Active Directory på följande sätt:

http://*servernamn*/\_wmcs/Certification

När underregistreringstjänsten begärs på en licensieringsserver läggs namnet på programfilen för tjänsten till på följande sätt:

http://servernamn/\_wmcs/Certification/SubEnrollService.asmx

| ![](images/Cc747641.note(WS.10).gif)Obs!                                     |
|-----------------------------------------------------------------------------------------------------------|
| Om du har aktiverat SSL på en RMS-server kommer dessa URL:er att använda anslutningsprotokollet https://. |
