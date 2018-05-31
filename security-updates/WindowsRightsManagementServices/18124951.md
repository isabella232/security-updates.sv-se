---
TOCTitle: Distribuera listor över återkallade certifikat
Title: Distribuera listor över återkallade certifikat
ms:assetid: 'e331338b-66d4-45e4-8d3f-acccf2302ac4'
ms:contentKeyID: 18124951
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747702(v=WS.10)'
---

Distribuera listor över återkallade certifikat
==============================================

Du måste distribuera listor över återkallade certifikat om du vill implementera återkallning. I listor över återkallade certifikat definieras innehåll, program, användare eller andra principer som har återkallats. Du kan distribuera både interna listor över återkallade certifikat och listor från Microsoft.

Distribuera interna listor över återkallade certifikat
------------------------------------------------------

Om du vill använda en principmall för rättigheter med en lista över återkallade certifikat måste du göra listan tillgänglig för klientdatorerna i organisationen. Information om hur du skapar listor över återkallade certifikat finns i ”Implementera återkallning” tidigare i det här avsnittet.

Följ dessa steg om du vill distribuera en lista över återkallade certifikat i organisationen:

1.  Kopiera filen med listan över återkallade certifikat till en offentlig webbserver. Eftersom det skyddade innehållet kan användas även utanför organisationen bör den aktuella platsen vara tillgänglig för alla användare, både de som arbetar i och de som arbetar utanför nätverket.
    Det kan ta tid att distribuera filen med listan över återkallade certifikat till klientdatorerna. Det är därför möjligt att användare inte har listan över återkallade certifikat på sin klientdator när de försöker öppna ett dokument som kräver den listan. Om listan inte finns på klientdatorn kan den hämtas med det RMS-aktiverade programmet från den plats som anges i användarlicensen.
    Den bästa lösningen är att skapa ett skript som automatiskt signerar och kopierar listan över återkallade certifikat till webbplatsen varje dag. Det garanterar att användarna inte hindras från att använda innehållet på grund av en inaktuell lista över återkallade certifikat. Ett exempel på ett sådant skript finns i ”Använda verktyget Revocation List Signing” tidigare i det här avsnittet.
2.  Ange ett uppdateringsintervall för organisationens lista över återkallade certifikat i principmallen för rättigheter. Intervallet måste vara större än noll. Det anger att användandet av listan inte är valfritt. Om du avser att endast uppdatera listan sporadiskt, t.ex. enbart i händelse av säkerhetsfel, kan du ange ett långt uppdateringsintervall och sedan låta listan över återkallade certifikat distribueras till klientdatorerna vid behov med skript eller principinställningar. Information hur du anger uppdateringsintervall finns i ”Definiera principer för återkallning” tidigare i det här avsnittet. Mer information om hur du konfigurerar principmallar för rättigheter finns i ”Skapa och ändra principmallar för rättigheter” senare i det här avsnittet.
3.  Ange URL:en till den plats där listan över återkallade certifikat finns i principmallen för rättigheter.
4.  Du kan också distribuera listan över återkallade certifikat till klientdatorer med en automatiserad metod, t.ex. en grupprincip eller SMS (Systems Management Server).

Distribuera listor över återkallade certifikat från Microsoft
-------------------------------------------------------------

Om det ska gå att använda en lista över återkallade certifikat från Microsoft på en RMS-klient måste du distribuera listan till klientdatorerna. I det här avsnittet beskrivs hur du distribuerar en lista över återkallade certifikat från Microsoft i följande situationer:

-   Organisationen vill distribuera en intern lista över återkallade certifikat och en lista från Microsoft.
-   Organisationen vill enbart distribuera en lista över återkallade certifikat från Microsoft.

När en lista över återkallade certifikat publiceras av Microsoft kan du hämta den från följande platser:

-   RMS-servrar kan hämta listan över återkallade certifikat genom att använda Windows Update.
-   Microsofts lista över återkallade certifikat kan även hämtas från Microsoft Download Center om RMS-servern inte är ansluten till Internet.

Om du hämtar paketet till en RMS-server sparas det i mappen %systemdrive%\\Program\\Windows Rights Management Services Revocation List. Om du hämtar paketet till en annan typ av dator kan du välja var du vill spara paketet. Paketet innehåller en körbar fil, CRL\_Update.exe, som du använder till att installera alla listor över återkallade klientcertifikat i klientens licensarkiv, och en fil med listan över återkallade certifikat, Msrl.xml, som du kopierar till en webbplats eller till en offentlig delad mapp.

**Så här distribuerar du en intern lista över återkallade certifikat och en återkallningslista från Microsoft**
1.  Om du vill distribuera en intern lista över återkallade certifikat följer du instruktionerna i ”[Distribuera listor över återkallade certifikat](https://technet.microsoft.com/e331338b-66d4-45e4-8d3f-acccf2302ac4)” tidigare i det här avsnittet.

2.  Hämta paketet med listan över återkallade certifikat från Microsoft och distribuera den till alla klientdatorer i organisationen med en metod som t.ex. en grupprincip eller SMS (Systems Management Server). Du kan också välja att kopiera poster från Microsofts lista över återkallade certifikat till den interna listan och sedan enbart distribuera den interna listan.

| ![](images/Cc747702.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft är en enhet i förtroendekedjan för alla certifikat och licenser som utfärdas med RMS. Därför gäller en lista över återkallade certifikat som har utfärdats av Microsoft för samtliga begäran om bindning från en användarlicens som är baserad på en principmall för rättigheter som kräver den interna listan. Dessutom är Microsofts lista registrerad på klientdatorn. |

**Så här distribuerar du enbart en lista över återkallade certifikat från Microsoft**
1.  Hämta paketet med listan över återkallade certifikat från Microsoft.

2.  Ändra alla befintliga principmallar för rättigheter så att de kräver återkallning eller skapa en principmall för rättigheter som kräver återkallning om det inte finns någon principmall. Använd Microsofts offentliga nyckel när du anger villkoren för återkallning.

3.  Ange ett mycket stort tal för uppdateringsintervallet, t.ex. 50 000. Det garanterar att listan över återkallade certifikat som publiceras av Microsoft aldrig upphör att gälla. Därmed behöver inte de användarlicenser som du distribuerar någon ny version av listan över återkallade certifikat från Microsoft om det inte finns någon lista tillgänglig.

4.  Kopiera filen med listan över återkallade certifikat till en offentlig webbserver. Eftersom det skyddade innehållet kan användas även utanför organisationen bör den aktuella platsen vara tillgänglig för alla användare, både de som arbetar i och de som arbetar utanför nätverket.

5.  Det kan ta tid att distribuera filen med listan över återkallade certifikat till klientdatorerna. Därför bör du göra listan tillgänglig på en plats som är tillgänglig för användarna. Det är alltså möjligt att en användare inte har listan över återkallade certifikat på sin dator när han eller hon försöker öppna ett dokument med en publiceringslicens som kräver återkallning. Om inte listan finns på klientdatorn kan den hämtas från den angivna platsen med det RMS-aktiverade programmet.

6.  Ange URL:en till den plats där listan över återkallade certifikat finns i principmallen för rättigheter. Mer information om hur du konfigurerar principmallar för rättigheter finns i ”[Skapa och ändra principmallar för rättigheter](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)” senare i det här avsnittet.

7.  Du kan också distribuera paketet med listan över återkallade certifikat till klientdatorer med en metod som exempelvis en grupprincip eller SMS (Systems Management Server). Användarna kan sedan öppna RMS-skyddat innehåll som kräver listor över återkallade certifikat även när de inte är anslutna till nätverket.
