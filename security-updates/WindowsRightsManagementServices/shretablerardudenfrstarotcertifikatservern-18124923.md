---
TOCTitle: Så här etablerar du den första rotcertifikatservern
Title: Så här etablerar du den första rotcertifikatservern
ms:assetid: 'debc42f3-74ff-4c99-b7a4-4921fccdabc2'
ms:contentKeyID: 18124923
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747768(v=WS.10)'
---

Så här etablerar du den första rotcertifikatservern
===================================================

Du måste vara inloggad lokalt på administrationswebbplatsen med ett domänanvändarkonto som tillhör administratörsgruppen på den aktuella datorn för att kunna utföra den här processen. Medlemmar av gruppen Domänadministratörer kan också utföra processen. Om du använder en SQL Server-fjärrdatabas måste kontot dessutom ha behörighet att skapa databaser i SQL Server. Av säkerhetsskäl bör du använda **Kör som** när du utför processen.

Klicka på **Start**, peka på **Alla program**, peka på **Windows RMS** och klicka sedan på **Administration av Windows RMS** om du vill öppna sidan **Global administration**.

På varje server kan du bara etablera RMS på en webbplats. Om du vill etablera RMS på en annan webbplats än standardwebbplatsen använder du Internet Information Services Manager och lägger till webbplatsen innan du påbörjar etableringsprocessen. Stäng sidan **Global administration** om den webbplats du vill etablera inte visas i listan över webbplatser. Lägg till webbplatsen och starta sedan etableringen igen.

Om du distribuerar RMS i en miljö där Active Directory-domänens funktionalitetsnivå har angetts till enhetligt läge i Microsoft Windows 2000 är det inte säkert att Windows RMS kan läsa attributet **memberOf** för Active Directory-objekt vid försök att expandera gruppmedlemskap. RMS-tjänstkontot måste använda ett domänkonto som tillhör gruppen Åtkomst till äldre operativsystem (före Windows 2000) i skogen för att det ska gå att läsa attributet **memberOf** i RMS.

Tänk på att registrera den anpassade URL:en för klustret, om du anger en sådan, i DNS (Domain Name System) och kontrollera att den fungerar. Kontrollera att URL:en är tillgänglig både från Internet och inifrån organisationen om det är en Internet-aktiverad distribution. Du måste ange HTTPS för kluster-URL:en om du har aktiverat SSL för webbtjänstfiler.

Etablera den första rotcertifikatservern
----------------------------------------

#### Så här etablerar du den första rotcertifikatservern

1.  Öppna sidan **Global administration** efter att har installerat RMS på den server som ska vara den första rotcertifikatservern i en Active Directory-skog.

2.  Klicka på **Etablera RMS på den här webbplatsen** bredvid den webbplats där du vill etablera RMS. Du kan välja standardwebbplatsen eller en annan webbplats som du skapar i IIS (Internet Information Services).

    | ![](images/Cc747768.Warning(WS.10).gif)Varning!                                                                                                                                                                                        |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Det går inte att köra ytterligare webbplatser eller webbtjänster på den server där RMS är installerat. Om du gör det kan det leda till att flera program och tjänster körs under samma konto som RMS, vilket kan kompromettera säkerheten för de privata nycklarna. |

3.  Standardalternativet vid **Konfigurationsdatabas** är att skapa konfigurationsdatabasen på den lokala servern. För lokala databaser kan du använda en databasserver, t.ex. SQL Server 2000 med SP3 eller Microsoft SQL Server 2000 Desktop Engine (MSDE). Om du använder en fjärrdatabas eller kör databasservern på den lokala servern men databasserverförekomsten har ett annat namn än namnet på servern väljer du **Fjärrdatabas** och anger namnet på databasservern.

    | ![](images/Cc747768.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Vi rekommenderar att Microsoft SQL Server Desktop Engine enbart används för hantering av RMS-databaser i testmiljö, eftersom Microsoft SQL Server Desktop Engine inte har funktioner för nätverksgränssnitt. Dessutom anger villkoren för användning av Microsoft SQL Server Desktop Engine att du inte får använda SQL Server-klientverktygen till att ändra en Microsoft SQL Server Desktop Engine-databas. Den här begränsningen gör att det inte går att visa loggningsinformation och att ändra data som lagras i konfigurationsdatabasen. |

4.  I området **RMS-tjänstkonto** anger du det RMS-tjänstkonto som normalt används för de vanligaste åtgärderna i RMS. För en enskild serverinstallation kan du ange antingen det lokala systemkontot eller ett domänkonto. För alla andra typer av installationer måste du ange ett domänkonto. Ange kontonamnet för ett domänkonto i formatet *domännamn*\\*användarnamn* samt lösenordet.

    | ![](images/Cc747768.Warning(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                                                                                             |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Det lokala systemkontot ger åtkomst till de flesta resurserna i operativsystemet, vilket är allvarligt ur säkerhetssynpunkt. Undvik att använda det lokala systemkontot som RMS-tjänstkonto när det är möjligt. Skapa i stället ett specifikt domänkonto som du använder som RMS-tjänstkonto. Tilldela inte det kontot några andra behörigheter. RMS-tjänstkontot kan inte vara samma domänkonto som användes vid installationen av RMS. |

    | ![](images/Cc747768.Important(WS.10).gif)Viktigt!                                                                                                                                                                  |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Av säkerhetsskäl bör du skapa ett specifikt domänkonto som används som tjänstkonto för Windows RMS. Tilldela inte detta konto några andra behörigheter. RMS-tjänstkontot kan inte vara samma domänkonto som användes vid installationen av RMS. |

5.  Skriv in URL:en till den server eller det kluster som ska användas för klienter i det interna nätverket vid **Kluster-URL**. Som standard används servernamnet, t.ex. Kontocertifikat. Du kan ändra det vid behov, t.ex. genom att konfigurera en URL eller en belastningsfördelare för klustret. Du kan också välja mellan HTTP och HTTPS. Mer information om hur du konfigurerar en kluster-URL finns under **Obs!** i slutet av de här instruktionerna. Efter etableringen kan du konfigurera en extern kluster-URL från administrationssidorna som kan användas av klienter utanför det interna nätverket.

6.  Välj önskat skydd för serverns privata nyckel vid **Skydd och registrering av privata nycklar** genom att göra något av följande:

    -   **Använd det programvarubaserade standardskyddet för privata nycklar**. Om du väljer det här alternativet lagras den privata nyckeln i RMS-konfigurationsdatabasen. Du måste ange ett starkt lösenord för kryptering av nyckeln i databasen.

    | ![](images/Cc747768.Important(WS.10).gif)Viktigt!                                                                                                                                                                                                                                                                                                                                                                                                  |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Spara lösenordet i ett säkert arkiv för framtida användning. Spara en säkerhetskopia av konfigurationsdatabasen (som också skyddas med det aktuella lösenordet) i det säkra arkivet. Det gör det möjligt att återställa RMS om SQL Server-databasen skadas. Om du av någon anledning ändrar lösenordet gör du en ny säkerhetskopia av konfigurationsdatabasen som är länkad till det nya lösenordet och placerar sedan både lösenordet och säkerhetskopian i det säkra arkivet. |

    -   **Använda en CSP (Cryptographic Service Provider)**. Avmarkera kryssrutan **Använd det programvarubaserade standardskyddet för privata nycklar** om du vill använda en CSP eller en HSM (Hardware Security Module). Markera den CSP eller HSM som är installerad i listan **Välj din CSP (Cryptographic Service Provider)**.

    | ![](images/Cc747768.note(WS.10).gif)Obs!                                                              |
    |------------------------------------------------------------------------------------------------------------------------------------|
    | För RMS krävs att en fullständig RSA-provider (Rivest-Shamir-Adleman) används. Endast sådana providers ingår i listan över CSP:er. |

    | ![](images/Cc747768.note(WS.10).gif)Obs!                                                                                                                                                                                                       |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Du bör antingen använda det programvarubaserade standardskyddet för nycklar eller en HSM. Se till att det finns rutiner för nyckelhantering i organisationen (t.ex. för säkerhetskopiering och återställning) innan du använder någon annan programvarubaserad CSP med RMS. |

7.  Det här steget gäller bara om du valde en CSP. Gör något av följande om du vill ange vilket servernyckelpar som ska användas:

    -   Välj **Skapa ett nytt nyckelpar med privata/offentliga nycklar** vid en nyinstallation.
    -   Välj **Använd ett befintligt nyckelpar med privata/offentliga nycklar** vid återställning eller uppgradering av en befintlig RMS-server. Klicka på **Bläddra** under **Befintlig nyckelbehållare** och välj sedan nyckelbehållare för servernyckelparet.

    | ![](images/Cc747768.note(WS.10).gif)Obs!                        |
    |----------------------------------------------------------------------------------------------|
    | Microsofts Base-, Enhanced- och Strong-CSP:er delar alla samma plats för lagring av nycklar. |

    | ![](images/Cc747768.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                              |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Om du inte använder ett befintligt nyckelpar när du återställer eller uppgraderar en befintlig RMS-server måste alla befintliga RMS-klienter få sina licenslager rensade (d.v.s. användarlicenser och rättighetskontocertifikat tas bort). Därefter måste nya licenser skaffas från servern för hantering av RMS-skyddat innehåll. |

8.  I **Internet-anslutning för server** anger du om servern erhåller serverlicensieringscertifikat genom att anslutas till Internet.

    -   Välj **Online** om du vill ansluta dig automatiskt till Microsofts registreringstjänst och få ett serverlicensieringscertifikat under etableringsprocessen.
    -   Välj **Offline** om RMS-servern inte har en Internet-anslutning eller om du vill skaffa serverlicensieringscertifikatet manuellt och importera det till RMS-servern efter att etableringen har slutförts.

9.  Skriv in ett namn i **Namn på serverlicensieringscertifikat** som ska användas i serverlicensieringscertifikatet. Som standard är det serverns namn.

10. Markera kryssrutan **Datorn ansluter till Internet via en proxyserver** och ange sedan proxyserverns adress och portnummer om organisationen ansluter till Internet via en proxyserver.

    Välj autentiseringstyp och ange ett användarnamn och lösenord som kan autentiseras av proxyservern om den kräver autentisering. Du måste också ange en domän om du använder Windows-integrerad autentisering.

    | ![](images/Cc747768.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Den här inställningen kan ändras efter etableringen på sidan **Säkerhetsinställningar** på webbplatsen för RMS-administration. Dock är inte sidan tillgänglig förrän servern har registrerats med Microsofts registreringstjänst. Om din organisation kräver att du använder en proxyserver för anslutning till Internet och du inte har konfigurerat en proxyserver eftersom du valde **Offline** under **Internet-anslutning för server** kommer du inte att kunna ändra inställningarna för varken etableringsprocessen eller proxyservern förrän du har slutfört den manuella registreringsprocessen eller etablerat RMS på nytt. |

11. Skriv in e-postadressen till den administratör som ska kontaktas vid problem med etablering av andra servrar vid **Administrativ kontakt**. Du kan ändra e-postadressen efter etableringen.

12. Ange om en tredje part kan återkalla serverns serverlicensieringscertifikat i området **Återkallning**. Om du aktiverar det här alternativet skriver du in sökvägen till och filnamnet på filen med den offentliga nyckeln hos aktuell tredje part.

13. Klicka på **Skicka**.

    Genom att klicka på **Skicka** etablerar du tjänsten. Om du har valt onlineregistrering utförs även registreringsprocessen för rotcertifikatservern. Ett nyckelpar med privata/offentliga nycklar genereras i RMS, och den offentliga nyckeln skickas till Microsofts registreringstjänst. I Microsofts registreringstjänst skapas ett serverlicensieringscertifikat som returneras till konfigurationsdatabasen inom några minuter. Om du använder offlineregistrering måste du slutföra uppgiften som beskrivs i ”[Så här registrerar du en rotcertifikatserver manuellt](https://technet.microsoft.com/aecdebb5-b28b-4b58-937a-392bb6ce9643)” senare i det här avsnittet innan du kan konfigurera RMS-servern.

    | ![](images/Cc747768.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Den här servern är inte klar att användas förrän RMS-tjänstens anslutningspunkt har registrerats i Active Directory. Följ stegen i ”[Så här registrerar du en anslutningspunkt för tjänst](https://technet.microsoft.com/630cc3c3-9ed9-4423-8874-cbaceb43b353)” senare i det här avsnittet för att slutföra processen. |

Instruktioner om hur du etablerar fler rotcertifikatservrar och lägger till dem i klustret finns i ”[Så här lägger du till en server i ett kluster](https://technet.microsoft.com/db635238-5528-4bec-9cc6-8244e2b3d733)” senare i det här avsnittet.
