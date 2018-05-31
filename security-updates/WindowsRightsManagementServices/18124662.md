---
TOCTitle: 'Använda gruppen RM-ansvariga'
Title: 'Använda gruppen RM-ansvariga'
ms:assetid: '0febcb3e-7124-4e51-971a-1013b928d33b'
ms:contentKeyID: 18124662
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720198(v=WS.10)'
---

Använda gruppen RM-ansvariga
============================

Under etableringen av RMS skapas en särskild grupp med RM-ansvariga som har fullständig behörighet till allt rättighetsskyddat innehåll. Medlemmar i gruppen RM-ansvariga tilldelas fullständiga ägarrättigheter i alla användarlicenser som utfärdas av den RMS-server eller det RMS-kluster där gruppen RM-ansvariga finns. Det innebär att medlemmar i den här gruppen kan dekryptera alla skyddade filer och att de även kan ta bort skyddet från dessa filer. Medlemmar av den här gruppen kan t.ex. ta bort skyddet från filer som har publicerats av en anställd som har slutat, så att en ny ägare kan publicera och hantera dessa filer.

Gruppen RM-ansvariga har som standard inga medlemmar, inte ens administratörer. På administrationswebbplatsen kan du ange en Active Directory-säkerhetsgrupp som ska användas som gruppen RM-ansvariga för RMS. Du kan antingen använda en befintlig Active Directory-grupp eller skapa en ny grupp för detta syfte. Gruppen måste finnas i samma Active Directory-skog som RMS-installationen. Alla användarkonton som är medlemmar av den grupp som används som RM-ansvariga för RMS tilldelas automatiskt behörigheterna i gruppen RM-ansvariga.

Mer information om hur du anger en grupp RM-ansvariga för RMS finns i ”[Så här konfigurerar du gruppen RM-ansvariga](https://technet.microsoft.com/f2ef847e-2824-471f-9079-5c343094aba8)” senare i det här avsnittet.

| ![](images/Cc720198.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                         |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Innan du kan ange en grupp som RM-ansvariga för RMS måste gruppen finnas i samma Active Directory-skog som RMS-installationen. Egenskaperna för den aktuella gruppen måste innehålla en e-postadress, inklusive ett fullständigt kvalificerat domännamn (FQDN) som är identiskt med kontonamnet. E-postadressen ska anges i formatet *gruppnamn*@*domännamn*. |
