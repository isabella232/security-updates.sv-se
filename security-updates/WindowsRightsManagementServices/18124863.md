---
TOCTitle: Så här förnyar du ett serverlicensieringscertifikat
Title: Så här förnyar du ett serverlicensieringscertifikat
ms:assetid: 'affce9cf-8b46-4293-8e1c-ee06f2ca6537'
ms:contentKeyID: 18124863
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747636(v=WS.10)'
---

Så här förnyar du ett serverlicensieringscertifikat
===================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

Om du har valt offlineförnyelse och ansluter till Internet med en dator med förbättrad säkerhetskonfiguration för webbläsaren, t.ex. en dator där Windows Server 2003 eller Windows XP Service Pack 2 körs, och begär ett serverlicensieringscertifikat, så måste du lägga till URL:en till registreringstjänstens webbplats i zonen Tillförlitliga platser. Annars kan inte serverlicensieringscertifikatet hämtas. URL:en är https://activation.drm.microsoft.com.

Om du använder processen för offlineregistrering ser du till att den dator du använder till att skicka registreringsbegäran till Microsofts registreringstjänst har certifikatet GTE Cyber Trust Root CA installerat i certifikatarkivet. Den här certifikatutfärdaren är betrodd som standard på datorer där Windows Server 2003 körs. Om datorn körs med en annan version av Windows kan du ange den här certifikatutfärdaren som betrodd genom att installera de senaste certifikatuppdateringarna från Windows Update.

Förnya ett serverlicensieringscertifikat
----------------------------------------

#### Så här förnyar du ett serverlicensieringscertifikat

1.  Öppna sidan **Global administration** och klicka på **Administrera RMS på den här webbplatsen** bredvid den webbplats där du vill förnya ett certifikat.

2.  Klicka på **Förnya** vid **Klusterresurser** på sidan **Administration**. Dialogrutan Förnya öppnas.

3.  Om servern är ansluten till Internet väljer du alternativet **Online** och klickar på **Förnya** så förnyas serverlicensieringscertifikatet automatiskt.

4.  Om servern inte är ansluten till Internet väljer du alternativet **Offline** och klickar sedan på knappen **Exportera**. Dialogrutan **Filhämtning** visas.

5.  Klicka på **Spara**. Dialogrutan **Spara som** visas.

    | ![](images/Cc747636.note(WS.10).gif)Obs!                                                                                      |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Klicka inte på **Öppna** i dialogrutan **Filhämtning**. Om du klickar på **Öppna** visas ett felmeddelande och filen med registreringsbegäran sparas inte. |

6.  Klicka på **Spara** så exporteras förnyelsebegäran till en fil. Som standard sparas filen på skrivbordet med namnet *servernamn*RenewalRequest.xml, där *servernamn* ersätts med namnet på den RMS-server du använder. Du kan spara filen på en annan plats genom att välja den platsen i listan Spara i. Du kan också använda ett annat filnamn än standardfilnamnet genom att ange det i **Filnamn**.

7.  När du har sparat filen med förnyelsebegäran visas dialogrutan **Hämtningen är slutförd**. Du kan visa XML-koden i filen genom att klicka på **Öppna**, men gör inga ändringar i filen. Om du vill öppna mappen som filen sparats i klickar du på **Öppna mapp**. Klicka på **Stäng** när du klar med att kontrollera filen och dess placering.

8.  Överför filen med förnyelsebegäran från servern till en dator som kan anslutas till Internet och gå sedan till [Registreringstjänsten]() Web site (https://go.microsoft.com/fwlink/?LinkId=25828).

9.  Följ instruktionerna på webbplatsen för att få ett serverlicensieringscertifikat.

10. Överför serverlicensieringscertifikatet tillbaka till rotcertifikatservern.

11. Klicka på **Förnya** i området **Klusterresurser**. Dialogrutan **Förnya** öppnas.

12. I dialogrutan **Förnya** klickar du på knappen **Bläddra** och bläddrar till det serverlicensieringscertifikat du hämtade och klickar sedan på knappen **Importera**.

13. Bekräfta att du vill importera certifikatet genom att klicka på **Ja**.

14. När serverlicensieringscertifikatet har förnyats uppdateras området **Klusterresurser** så att det nya förfallodatumet för serverlicensieringscertifikatet visas.

Mer information om hur du förnyar serverlicensieringscertifikat finns i ”[Hantera serverlicensieringscertifikat](https://technet.microsoft.com/549979ad-13ee-4abc-8281-3e002a5a9561)” tidigare i det här avsnittet.
