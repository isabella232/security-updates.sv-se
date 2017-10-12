---
TOCTitle: Registrera rotcertifikatservern
Title: Registrera rotcertifikatservern
ms:assetid: '3f69d25e-ecae-447f-b741-a819c8cf6227'
ms:contentKeyID: 18124714
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720250(v=WS.10)'
---

Registrera rotcertifikatservern
===============================

Varje RMS-installation måste innehålla minst en rotcertifikatserver, men den kan även innehålla flera rotcertifikatservrar i ett kluster. Den första rotcertifikatserver du installerar måste registreras via Microsofts registreringstjänst så att du får ett serverlicensieringscertifikat. Certifikatet utgör grunden för förtroendehierarkin i en RMS-implementering.

Du kan använda någon av följande metoder för att få ett serverlicensieringscertifikat. Välj vilken metod du vill använda när du anger etableringsinformationen för din RMS-server:

-   **Onlineregistrering**. Om rotcertifikatservern kan anslutas till Internet kan du få ett serverlicensieringscertifikat automatiskt under etableringen. Det här är standardmetoden.
-   **Offlineregistrering**. Om rotcertifikatservern inte är kopplad till Internet kan du registrera den manuellt när etableringsprocessen är slutförd. Om du vill göra det exporterar du en registreringsbegäran från servern till en fil som du kan överföra till en annan dator som har Internet-anslutning och skickar sedan begäran till Microsofts registreringstjänst. Du får då ett serverlicensieringscertifikat. Om du väljer offlineregistrering vid etableringen slutför RMS etableringsprocessen. Du kan dock inte använda RMS förrän serverlicensieringscertifikatet du får från den andra datorn har importerats. Mer information finns i ”[Så här registrerar du en rotcertifikatserver manuellt](https://technet.microsoft.com/aecdebb5-b28b-4b58-937a-392bb6ce9643)” senare i det här avsnittet.

Registreringsbegäran innehåller följande information:

-   Information om återkallning. Om RMS-installationen ska användas för standardåterkallning eller anpassad återkallning (från tredje part). Om Microsoft-återkallning från tredje part används inkluderas återkallningsrättighetens offentliga nyckel.
-   Certifikatets offentliga nyckel. Serverlicensieringscertifikatets offentliga nyckel. Den här offentliga nyckeln genereras på RMS-servern och skickas till Microsofts registreringstjänst, så att serverlicensieringscertifikatet hämtas.
-   SKU. Det officiella SKU-namnet för RMS.
-   Version. Versionsnumret för RMS-paketet.
-   URL. RMS-serverklustrets bas-URL.

När ett svar på registreringsbegäran skickas från Microsofts registreringstjänst lämnas följande information till RMS-servern i XML-format:

-   Serverlicensieringscertifikat.
-   Certifikatkedja av signeringsrättigheter.

Samma information överförs oavsett om RMS-rotcertifikatservern registreras med online- eller offlinemetoden. Ingen ytterligare information samlas in oavsett vilken av metoderna som används.

| ![](images/Cc720250.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Om du har valt offlineregistrering och ansluter till Internet med en dator med förbättrad säkerhetskonfiguration för webbläsaren, exempelvis en dator där Windows Server 2003 eller Windows XP Service Pack 2 körs, och begär ett serverlicensieringscertifikat, så måste du lägga till URL:en till registreringstjänstens webbplats i zonen Tillförlitliga platser. Annars kan inte serverlicensieringscertifikatet hämtas. URL:en är https://activation.drm.microsoft.com. Om du använder offlineregistrering måste du se till att datorn du använder till att skicka registreringsbegäran till Microsofts registreringstjänst har alla de senaste certifikatuppdateringarna installerade. SSL-certifikatet från Microsofts registreringstjänst är GTE Cyber Trust Root CA, som är betrott som standard på alla datorer där Windows Server 2003 körs. Om du använder offlineregistrering måste du kontrollera att RMS-klienter inte försöker ansluta till RMS-servern för att få licenser innan registreringen har ägt rum. Om försök görs att ansluta med en klient till en RMS-server som inte är registrerad kommer webbtjänsterna att hamna i ett felläge som gör att de inte kan användas. Om du inte kan hindra klienter från att försöka ansluta till RMS-servern bör du som standard återställa IIS efter att ha slutfört registreringen för att ta bort eventuella feltillstånd som kan ha genererats. |
