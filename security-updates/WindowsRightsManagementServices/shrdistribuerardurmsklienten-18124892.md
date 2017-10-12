---
TOCTitle: 'Så här distribuerar du RMS-klienten'
Title: 'Så här distribuerar du RMS-klienten'
ms:assetid: 'c84f1724-cf71-4385-9003-ff68bc23c927'
ms:contentKeyID: 18124892
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747749(v=WS.10)'
---

Så här distribuerar du RMS-klienten
===================================

Om du använder Microsoft Windows XP eller Microsoft Windows 2000 måste Rights Management Services-klienten (RMS) installeras innan du kan använda RMS-funktioner, t.ex. Information Rights Management i Microsoft® Office System 2003 och Rights Management Add-on for Internet Explorer. RMS-klienten är inbyggd i Windows Vista®.

Många organisationer väljer att kontrollera distributionen av klientprogramvara i organisationen. Det går att använda antingen Systems Management Server (SMS) eller grupprinciper till att distribuera RMS-klienten med Service Pack 2 (SP2).

Innan du påbörjar distributionen kan du läsa på [http://go.microsoft.com/fwlink/?LinkId=67736](http://go.microsoft.com/fwlink/?linkid=67736) om hämtning av RMS-klienten.

| ![](images/Cc747749.Important(WS.10).gif)Viktigt!                   |
|--------------------------------------------------------------------------------------------------|
| RMS-klienten har integrerats i Windows Vista. Därför behövs inte längre en separat installation. |

Extrahera installationsfilerna
------------------------------

När du har hämtat filen WindowsRightsManagementServicesSP2-KB917275-Client-ENU.exe måste du extrahera Microsoft® Windows® Installer-filerna från det körbara paketet.

Du kan använda följande kommandorad från kommandotolken:

`WindowsRightsManagementServicesSP2-KB917275-Client-ENU.exe /x <path>`

där &lt;sökväg&gt; är målmappen där du vill att de extraherade filerna ska läggas.

Om du använder det kommandot extraheras följande filer till den angivna målmappen:

-   Bootstrap.exe
    Det här är en wrapperfil som används av den körbara filen vid installationen av de andra filerna i paketet. Den används inte när du installerar RMS SP2-klienten med SMS eller en grupprincip.
-   MSDrmClient.msi
    Det här är installationsfilen för RMS SP2-klienten. Vid installationen avinstalleras tidigare versioner av RMS-klienten på datorn. Det här programmet ska installeras på klientdatorerna först.
-   RMClientBackCompat.msi
    Det här är installationsfilen som identifierar den nya RMS med SP2-klienten för RMS-aktiverade program (t.ex. Microsoft Office Professional 2003 eller 2007 Microsoft Office System) som är beroende av den tidigare versionen av RMS-klienten, så att RMS med SP2-klienten kan användas i stället. Det här programmet bör installeras på klientdatorerna när installationen av MSDrmClient.msi är slutförd.

| ![](images/Cc747749.note(WS.10).gif)Obs!                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Vilken installationsmetod du än väljer ska du se till att båda Windows Installer-filerna installeras utan fel. Om ett fel inträffar som förhindrar installation av MSDrmClient.msi ska du inte installera RMClientBackCompat.msi. |

Distribuera RMS-klienten genom en obevakad installation
-------------------------------------------------------

Det är valfritt att extrahera filerna för att installera Windows Installer-filerna. Du kan även distribuera RMS-klienten med en metod för obevakad installation. Du kan använda följande kommandorad från kommandotolken:

`WindowsRightsManagementServicesSP2-KB917275-Client-ENU.exe -override 1 /I MsDrmClient.msi REBOOT=ReallySuppress /q -override 2 /I RmClientBackCompat.msi REBOOT=ReallySuppress /q`

Kommandot startar den obevakade installationen av RMS-klienten.

| ![](images/Cc747749.note(WS.10).gif)Obs!                                                                                                          |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Eftersom det är en obevakad installation meddelar installationsprogrammet inte att installationen är klar. Obevakade installationer körs vanligen i en batch- eller skriptfil. |

Distribuera RMS-klienten med SMS
--------------------------------

**Så här distribuerar du RMS-klienten med hjälp av SMS**
1.  Öppna administratörskonsolen i SMS.

2.  Expandera den platsdatabas som du vill använda.

3.  Högerklicka på **Paket** i den vänstra fönsterrutan. Välj **Nytt** och klicka sedan på **Paket från-definition**.

4.  Skapa paket från filerna MSDRMClient.msi och RMClientBackCompat.msi. Paketen ska ha följande egenskaper:

    **Allmänt**:

    -   Som **Kommandorad** anger du följande:
        `msiexec.exe /q ALLUSERS=2 /m MSIDGHOG /i "<file_name>.msi"`
        | ![](images/Cc747749.note(WS.10).gif)Obs!                                                                     |
        |-------------------------------------------------------------------------------------------------------------------------------------------|
        | MSIDGHOG är ett slumpvis valt värde. Byt ut &lt;filnamn&gt; mot namnet på Windows-installationsfilen som installeras med det här paketet. |

    -   Vid **Kör** väljer du alternativet **Dold**.
    -   Vid **Efter körning** väljer du alternativet **Ingen åtgärd krävs**.
    -   Vid **Kategori** väljer du **Administrationsprogram**.

    **Krav:**

    -   Vid **Beräknat diskutrymme** skriver du **445 kB**.
    -   Vid **Maximal körtid** väljer du **Okänd**.
    -   Markera kryssrutan vid \#\#**Det här programmet kan köras på alla plattformar**.

    **Miljö:**

    -   Vid **Programmet kan köra** väljer du alternativet **Oavsett om någon användare är inloggad**.
    -   Vid **Körningsläge** väljer du alternativet **Kör med administratörsrättigheter**.
    -   Vid **Enhetsläge** väljer du alternativet **Körs med UNC-namn**.

    **Avancerat:**

    -   Avmarkera kryssrutan vid \#\#**Kör ett annat program först**.
    -   Avmarkera kryssrutan vid \#\#**Suppress program notification** under \#\#**When the program is assigned to a computer**.
    -   Avmarkera kryssrutan vid \#\#**Disable this program on computers where it is advertised**.

5.  Ställ in **Behörighetskonton och distributionspunkter** så att de stämmer med din organisation.

6.  Skapa en \#\#avisering till rätt samling\#\#. Vi rekommenderar att du använder programmet \#\#**Per-system unattended** i en SMS-distribution.

7.  Schemalägg aviseringen enligt behoven i din organisation.

Distribuera RMS-klienten med grupprinciper
------------------------------------------

Du kan använda funktionen för installation och underhåll av programvara i Grupprincip när du distribuerar RMS-klienten till måldatorer.

Grupprincip är den metod som rekommenderas för att aktivt hantera distributionen av RMS-klienter i små till medelstora organisationer eller till dem som inte redan använder en lösning för uppdateringshantering, t.ex. Systems Management Server 2003.

När du använder grupprinciper till att distribuera ett program kan du tilldela programmet till datorer. Programmet har installerats när datorn startar och är tillgängligt för alla användare som loggar in på datorn. Mer information om grupprinciper finns i Designing a Group Policy Infrastructure (<http://go.microsoft.com/fwlink/?linkid=24328>). I den här processen förutsätts det att du använder konsolen Grupprinciphantering (GPMC). Om du vill hämta GPMC går du till Group Policy Management Console with Service Pack 1 (<http://go.microsoft.com/fwlink/?linkid=21813>).

Här följer en snabbguide för administratörer som inte är bekanta med programvarudistribution som bygger på grupprinciper. Du kan ändra de här stegen så att de stämmer överens med behoven i din organisation.

**Så här distribuerar du RMS-klienten med hjälp av grupprinciper**
1.  Öppna MMC-snapin-modulen **Active Directory - användare och datorer** på en domänkontrollant.

2.  Skapa en ny organisationsenhet (OU) eller välj en befintlig.

    Om du väljer att skapa en ny OU ska du lägga till de datorer där du vill installera RMS-klienten.

3.  Högerklicka på OU:n och välj **Egenskaper**.

4.  Välj fliken **Grupprincip**.

5.  Klicka på **Nytt** om du vill skapa ett nytt grupprincipobjekt (GPO).

6.  Klicka på **Redigera** för att redigera det nya GPO:t.

7.  I konsolträdet expanderar du **Datorkonfiguration** och **Programvaruinställningar**. Sedan väljer du Programvaruinstallation.

8.  Högerklicka i informationsfönstret, klicka på **Nytt** och sedan på **Paket**.

9.  Lägg till en sökväg till filen MSDRMclient.msi till en delad nätverksmapp som klientdatorerna har åtkomst till.

10. Klicka på **OK** så tilldelas paketet.

11. Upprepa steg 5 till 10 om du vill skapa ett GPO som används till att installera filen RMClientBackCompat.msi.

| ![](images/Cc747749.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                            |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| De här stegen är avsedda för användare som inte är vana att använda grupprinciper. Om du är erfaren grupprincipadministratör kan du gå efter din egen procedur när du distribuerar MSDrmClient.msi-paketet. De här stegen gäller för domänkontrollanter där Windows Server 2003 körs – processen och terminologin kan se annorlunda ut på en Windows 2000-domän. |

Uppgradera från en tidigare version
-----------------------------------

        ```
| ![](images/Cc747749.note(WS.10).gif)Obs!                       |
|---------------------------------------------------------------------------------------------|
| Skriptet fungerar inte i Windows Vista eftersom RMS-klienten är inbyggd i operativsystemet. |
