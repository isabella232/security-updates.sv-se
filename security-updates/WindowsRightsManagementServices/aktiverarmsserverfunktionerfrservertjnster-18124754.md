---
TOCTitle: 'Aktivera RMS-serverfunktioner för servertjänster'
Title: 'Aktivera RMS-serverfunktioner för servertjänster'
ms:assetid: '6288323c-0638-41b6-bef8-67a7c9433424'
ms:contentKeyID: 18124754
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747593(v=WS.10)'
---

Aktivera RMS-serverfunktioner för servertjänster
================================================

RMS kan också tillhandahålla rättighetskontocertifikat och använda licenser för RMS-aktiverade serverprogram. Det finns några saker som du bör tänka på när du konfigurerar servertjänster:

-   I DACL-listor på RMS-pipelines används de säkraste inställningarna som standard. Du måste modifiera DACL-listan när du använder RMS-servertjänster.
-   Om RMS-klienten är installerad på en Windows Server 2003-baserad server och Internet Explorer Enhanced Security Configuration har aktiverats, måste du lägga till URL-sökvägen till RMS-kluster i Internet Explorers zon för betrodda platser.
-   Många servertjänster använder avancerade funktioner i Active Directorys katalogtjänster som bara är tillgängliga om alla Active Directory-domänkontrollanter körs med Windows Server 2003. Om du använder några servertjänster (t.ex. Microsoft Office SharePoint Server 2007 eller Microsoft Exchange Server 2007) rekommenderar vi att alla domänkontrollanter körs med Windows Server 2003 och att funktionalitetsnivåerna för både Active Directory-domän och -skog är på Windows Server 2003-nivå.

Standard-DACL-listan (discretionary access control list) för servercertifieringens pipeline
-------------------------------------------------------------------------------------------

Program som Microsoft Office SharePoint Server 2007 eller Microsoft Exchange Server 2007 är RMS-aktiverade för att kunna begära användarlicenser åt användare. I en standard-RMS-installation begränsas DACL-listan för RMS-servercertifieringens pipeline, vilket innebär att ett program inte kan erhålla certifikat och licenser för användarna. Men om de här datorerna utrustas med ett RMS-aktiverat program kan du låta dem bli en del av RMS-systemet genom att konfigurera DACL-listor för RMS-servercertifieringens pipeline.

RMS-aktiverade serverprogram ansluts till RMS-certifieringstjänsten med hjälp av filen ServerCertification.asmx.

När filerna skapas i RMS har deras DACL-listor angetts till att bara tillåta åtkomst för systemprocesser. Vi rekommenderar att du skapar en Active Directory-säkerhetsgrupp för servertjänster och fyller i gruppen med Active Directory-objekt för de datorer som begär användarlicenser för sina användare.

När du har skapat gruppen kan du modifiera DACL för filen ServerCertification.asmx så att gruppen får behörigheterna Läs& Kör för den här tjänsten. Du måste också lägga till RMS-tjänstgruppen till DACL-listan med både Läs- & körrättigheter.

| ![](images/Cc747593.note(WS.10).gif)Obs!                                                         |
|-------------------------------------------------------------------------------------------------------------------------------|
| Om det finns mer än en RMS-server i klustret måste DACL för filen ServerCertification.asmx ändras på varje server i klustret. |

För Microsoft Exchange Server 2007 måste Active Directory-datorobjekten för varje Exchange Bridgehead-server läggas till i servertjänstgruppen. Om det inte sker kommer Exchange Bridgehead-servern inte att kunna begära licenser för de användare som får e-postmeddelandet.

För Office SharePoint Server 2007 måste du lägga till Active Directory-datorobjekt för den server där Office SharePoint Server 2007 körs i servertjänstgruppen. Om Office SharePoint Server 2007-servern har konfigurerats till att använda standardservern i Active Directory, måste du lägga till RMS-tjänstgruppen och den grupp som skapats för servertjänster i filen ServiceLocater.asmx och tillåta Läs- & körrättigheter.

| ![](images/Cc747593.Important(WS.10).gif)Viktigt!                                                                                                                                |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Internet Information Services (IIS) måste startas om när DACL har ändrats för ServerCertification.asmx och ServiceLocater.asmx. Du återställer IIS genom att köra kommandot **iisreset** från kommandotolken. |
