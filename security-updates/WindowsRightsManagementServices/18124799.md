---
TOCTitle: Återkalla serverlicensieringscertifikat
Title: Återkalla serverlicensieringscertifikat
ms:assetid: '8020861d-d196-4431-8282-044675ef5616'
ms:contentKeyID: 18124799
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747578(v=WS.10)'
---

Återkalla serverlicensieringscertifikat
=======================================

En organisation kan behöva återkalla ett serverlicensieringscertifikat på grund av oförutsedda problem som leder till att RMS-servern komprometteras. En privat nyckel som inte förvaras i en HSM (Hardware Security Module) går att stjäla. Serverlicensieringscertifikat och servernycklar i en organisation kan komprometteras vid en attack från utomstående som tar kontroll över servern, eller av en anställd med skadligt uppsåt som kopierar eller tar bort certifikatet eller nyckeln. Återkallning är ett sätt att minimera skadan och att begränsa effekterna av användare med skadligt uppsåt.

Som standard kan alla licenser och certifikat återkallas av den enhet som utfärdade licensen eller certifikatet. Eftersom RMS-servrar används till att utfärda licenser och certifikat som är associerade med organisationens skyddade innehåll kan du alltid återkalla dem vid behov. Om en licensieringsserver komprometteras kan du återkalla det aktuella serverlicensieringscertifikatet. När du återkallar ett serverlicensieringscertifikat blir alla certifikat och licenser som utfärdats med det ogiltiga. Instruktioner om hur du återkallar licenser och certifikat finns i ”[Implementera återkallning](https://technet.microsoft.com/4735f060-7197-4ae2-830a-f91bcc4de30a)” tidigare i det här avsnittet.

För rotcertifikatklustret krävs dock ett speciellt förfarande. Rotcertifikatklustrets serverlicensieringscertifikat har utfärdats av Microsofts registreringstjänst och som standard kan bara Microsofts registreringstjänst återkalla detta serverlicensieringscertifikat.

Microsoft kan bara återkalla serverlicensieringscertifikatet för en rotcertifikatserver om du har ett domslut om att detta ska göras och du tillhandahåller domstolen den offentliga nyckeln. När Microsoft meddelas att en dom har avkunnats inkluderas serverlicensieringscertifikatet i listan över återkallade certifikat och listan distribueras. Du kan begära ett domslut från rätten om något av följande gäller för det serverlicensieringscertifikat som ska återkallas:

-   Ni äger servern och den privata nyckeln har komprometterats.
-   Ni äger innehållet som publiceras av servern och publiceringen gör intrång i ert copyrightskydd.

Följ stegen som beskrivs i ”[Distribuera listor över återkallade certifikat](https://technet.microsoft.com/e331338b-66d4-45e4-8d3f-acccf2302ac4)” tidigare i det här avsnittet om du vill hämta och distribuera listor över återkallade certifikat från Microsoft som innehåller det återkallade serverlicensieringscertifikatet för en rotcertifikatserver.

När du etablerar rotcertifikatservern kan du ange en offentlig nyckel med behörighet att återkalla rotcertifikatklustrets serverlicensieringscertifikat. Den offentliga nyckeln kan antingen tillhöra organisationen eller en tredje part. En lista över återkallade certifikat som har signerats med motsvarande privat nyckel kan användas till att återkalla serverlicensieringscertifikatet.

Du återkallar serverlicensieringscertifikatet för en rotcertifikatserver genom att skapa en lista över återkallade certifikat som innehåller det aktuella serverlicensieringscertifikatet, signera listan med organisationens privata nyckel eller en tredje parts privata nyckel och sedan distribuera listan till alla användare. Instruktioner finns i ”Distribuera interna listor över återkallade certifikat” i ”[Distribuera listor över återkallade certifikat](https://technet.microsoft.com/e331338b-66d4-45e4-8d3f-acccf2302ac4)” tidigare i det här avsnittet.

Använd följande parametrar om du återkallar ett serverlicensieringscertifikat med en lista över återkallade certifikat:

-   **GUID**. Ett serverlicensieringscertifikat kan återkallas baserat på sitt globalt unika ID (GUID). Information om hur du använder den här parametern i en lista över återkallade certifikat finns i ”Återkalla certifikat och licenser baserat på GUID” i ”[Skapa listor över återkallade certifikat](https://technet.microsoft.com/1ef75199-3344-4225-84de-a863a777696a)” tidigare i det här avsnittet.
-   **Hashvärde**. Ett serverlicensieringscertifikat kan återkallas baserat på SHA-1-hashvärdet för de Unicode-tecken som ingår i certifikatets "BODY"-tagg. Information om hur du använder den här parametern i en lista över återkallade certifikat finns i ”Återkalla certifikat och licenser baserat på hashvärde” i ”[Skapa listor över återkallade certifikat](https://technet.microsoft.com/1ef75199-3344-4225-84de-a863a777696a)” tidigare i det här avsnittet.

Om du vill hämta serverlicensieringscertifikatet för en RMS-installation måste du skicka en fråga till RMS-konfigurationsdatabasen. I följande steg beskrivs hur du hämtar den informationen från en SQL-konfigurationsdatabas och sparar den i en fil som kan läsas i en webbläsare:

1.  Öppna frågeanalysatorn i SQL och anslut sedan till rotcertifikatserverns konfigurationsdatabas.
2.  Klicka på **Results in Text** på **Query**-menyn.
3.  Klicka på **Options** på **Tools**-menyn och öppna dialogrutan **Options**. Klicka på fliken **Results** och ange **Maximum characters per column** till **8192**.
4.  Skriv in följande frågesträng i dialogrutan Query:
        
```
    select DRMS_XrML_Certificate.s_certificate from DRMS_XrML_Certificate, DRMS_LicensorCertificate, DRMS_ClusterConfiguration where DRMS_ClusterConfiguration.CurrentLicensorCertID = DRMS_LicensorCertificate.i_CertID and DRMS_LicensorCertificate.i_CertificateID = DRMS_XrML_Certificate.i_CertificateID
```

1.  Kopiera resultatet från fönstret **Results** och klistra in det i en textredigerare, t.ex. Anteckningar. Spara resultatet i en fil med filnamnstillägget .xml.

Mer information om hur du använder den här informationen i en lista över återkallade certifikat finns i ”[Skapa listor över återkallade certifikat](https://technet.microsoft.com/1ef75199-3344-4225-84de-a863a777696a)” tidigare i det här avsnittet.

När serverlicensieringscertifikatets information har sparats som en XML-fil kan du extrahera den offentliga nyckeln från filen på följande sätt:

1.  Öppna XML-filen som innehåller serverlicensieringscertifikatet i en XML- eller textredigerare.
2.  Under avsnittet &lt;ISSUEDPRINCIPALS&gt; kopierar du elementet &lt;PUBLICKEY&gt;.
3.  Spara informationen i en fil som du kan skicka till domstol, eller placera den i en intern lista över återkallade certifikat.

När rotcertifikatklustrets serverlicensieringscertifikat har återkallats blir alla certifikat och licenser som har utfärdats med RMS-installationen ogiltiga för allt innehåll som kräver en lista över återkallade certifikat. Det innehållet går då inte att komma åt. Den här processen påverkas inte av vilken typ av licens användaren har. Du måste göra något av följande innan du implementerar listan över återkallade certifikat om du vill behålla innehåll som har publicerats med den server vars licens återkallas:

-   Spara innehållet utan RMS-skydd.
-   Publicera innehållet på nytt utan något krav på att en lista över återkallade certifikat ska användas.

I båda dessa scenarion - återkallning från Microsoft och återkallning från tredje part - gäller listan över återkallade certifikat för alla begäran om bindning, eftersom den har signerats med en privat nyckel för en enhet i användarlicensens förtroendekedja. Därför kommer alla begäran om bindning från licenser som har utfärdats med den aktuella RMS-installationen med det återkallade serverlicensieringscertifikatet att misslyckas.

> [!NOTE]  
> Microsoft återkallar bara serverlicensieringscertifikat när man åläggs av en behörig myndighet att göra detta.
