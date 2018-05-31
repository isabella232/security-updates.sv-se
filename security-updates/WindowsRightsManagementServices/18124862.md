---
TOCTitle: Så här registrerar du en rotcertifikatserver manuellt
Title: Så här registrerar du en rotcertifikatserver manuellt
ms:assetid: 'aecdebb5-b28b-4b58-937a-392bb6ce9643'
ms:contentKeyID: 18124862
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747727(v=WS.10)'
---

Så här registrerar du en rotcertifikatserver manuellt
=====================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda Kör som när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Om du använder offlineregistrering måste du kontrollera att RMS-klienter inte försöker ansluta till RMS-servern för att få licenser innan registreringen har ägt rum. Om klienter försöker ansluta till en RMS-server som inte är registrerad hamnar webbtjänsterna i ett feltillstånd som gör dem obrukbara. Om du inte kan hindra klienter från att försöka ansluta till RMS-servern bör du som standard återställa IIS efter att ha slutfört registreringen för att ta bort eventuella feltillstånd som kan ha genererats.

Om du har valt offlineregistrering och ansluter till Internet med en dator med förbättrad säkerhetskonfiguration för webbläsaren, exempelvis en dator där Windows Server 2003 eller Windows XP Service Pack 2 körs, och begär ett serverlicensieringscertifikat så måste du lägga till URL:en till registreringstjänstens webbplats i zonen Tillförlitliga platser. Annars kan inte serverlicensieringscertifikatet hämtas. URL:en är https://activation.drm.microsoft.com.

Om du använder processen för offlineregistrering ser du till att den dator du använder till att skicka registreringsbegäran till Microsofts registreringstjänst har certifikatet GTE Cyber Trust Root CA installerat i certifikatarkivet. Den här certifikatutfärdaren är betrodd som standard på datorer där Windows Server 2003 körs. Om datorn körs med en annan version av Windows kan du ange den här certifikatutfärdaren som betrodd genom att installera de senaste certifikatuppdateringarna från Windows Update.

Registrera en rotcertifikatserver manuellt
------------------------------------------

#### Så här registrerar du en rotcertifikatserver manuellt

1.  När du har installerat RMS på den server du vill använda som rotcertifikatserver öppnar du sidan **Global administration** och klickar på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill importera ett licensieringscertifikatet för rotservern.

2.  Klicka på **Registrera** i området **Klusterresurser**. Dialogrutan **Registrera** öppnas.

3.  Välj alternativet **Offline** och klicka på knappen **Exportera**. Dialogrutan **Filhämtning** visas.

4.  Klicka på **Spara**. Dialogrutan **Spara som** visas.

    | ![](images/Cc747727.note(WS.10).gif)Obs!                                                                                      |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Klicka inte på **Öppna** i dialogrutan **Filhämtning**. Om du klickar på **Öppna** visas ett felmeddelande och filen med registreringsbegäran sparas inte. |

5.  Klicka på **Spara** så exporteras registreringsbegäran till en fil. Som standard sparas filen på skrivbordet med namnet *servernamn*EnrollRequest.xml, där *servernamn* ersätts med namnet på den RMS-server du använder. Du kan spara filen på en annan plats genom att välja den platsen i listan **Spara i**. Du kan också använda ett annat filnamn än standardfilnamnet genom att ange det i **Filnamn**.

6.  När du har sparat filen med registreringsbegäran visas dialogrutan **Hämtningen är slutförd**. Du kan visa XML-koden i filen genom att klicka på **Öppna**, men gör inga ändringar i filen. Om du vill öppna mappen som filen sparats i klickar du på **Öppna mapp**. Klicka på **Stäng** när du klar med att kontrollera filen och dess placering.

7.  Överför filen med registreringsbegäran från servern till en dator som kan anslutas till Internet och gå sedan till [webbplatsen för registreringstjänsten]().

8.  Följ instruktionerna på webbplatsen för att få ett serverlicensieringscertifikat.

9.  Överför serverlicensieringscertifikatet tillbaka till rotcertifikatservern.

10. Klicka på **Registrera** i området **Klusterresurser**. Dialogrutan **Registrera** öppnas.

11. I dialogrutan **Registrera** klickar du på knappen **Bläddra** och bläddrar till det serverlicensieringscertifikat du hämtade, och klickar sedan på knappen **Importera**.

12. Bekräfta att du vill importera certifikatet genom att klicka på **Ja**.

13. Området **Klusterresurser** uppdateras så att serverlicensieringscertifikatet visas.
