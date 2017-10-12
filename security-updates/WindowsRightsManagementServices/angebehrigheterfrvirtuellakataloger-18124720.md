---
TOCTitle: Ange behörigheter för virtuella kataloger
Title: Ange behörigheter för virtuella kataloger
ms:assetid: '45112111-9608-45b1-9a86-7b313d0a1579'
ms:contentKeyID: 18124720
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747549(v=WS.10)'
---

Ange behörigheter för virtuella kataloger
=========================================

När du har aktiverat inaktivering finns det tillgängligt som en tjänst. Inaktiveringstjänsten är en virtuell katalog i IIS med åtkomstbehörigheter kopplade till sig. För att användarna ska kunna komma åt tjänsten måste du ställa in åtkomst i den virtuella katalogen och i filen decommission.asmx.

Windows-integrerad autentisering är aktiverat som standard för den virtuella katalogen, men det är bara personer med system- och administratörskonto som har åtkomst till filen. När du anger behörigheter för decommission.asmx-filens DACL-lista kan du ge behörighet att ta bort RMS-skyddet till en specifik grupp betrodda användare. Du kan också låta alla få tillgång till tjänsten.

Innan användaren kan börja använda inaktiveringstjänsten måste användarens program modifieras så att begäran om en användarlicens kan skickas till den nya inaktiverings-pipelinen. I Microsoft Office System 2003 gör du det genom att lägga till en registerpost på användarens dator. Om du använder Office 2003 kan du göra enligt följande:

1.  Öppna registereditorn.
2.  Gå till `HKEY_CURRENT_USER\Software\Microsoft\Office\11,0\Common\DRM` och lägg till en ny nyckel med namnet `Inaktivering`.
3.  Under inaktiveringsnyckeln lägger du till följande nya **värde** där du ersätter *din licenseringsserver* med namnet på RMS-servern:
    `http://`*din licenseringsserver*`/_wmcs/licensing`
4.  Sedan högerklickar du på posten och väljer **Ändra**. Ange värdet som ska peka på inaktiveringstjänsten:
    `http://`*din licenseringsserver*`/_wmcs/inaktivera`

| ![](images/Cc747549.note(WS.10).gif)Obs!                             |
|---------------------------------------------------------------------------------------------------|
| Den här nyckeln kan ha flera värden när flera RMS-servrar i företaget är i inaktiverat tillstånd. |
