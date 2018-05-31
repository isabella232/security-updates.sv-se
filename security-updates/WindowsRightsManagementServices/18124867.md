---
TOCTitle: 'Vanliga frågor om RMS: Certifikat, nycklar och kryptering'
Title: 'Vanliga frågor om RMS: Certifikat, nycklar och kryptering'
ms:assetid: 'ad8cc088-1dea-44c2-be68-9091129f0f12'
ms:contentKeyID: 18124867
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747725(v=WS.10)'
---

Vanliga frågor om RMS: Certifikat, nycklar och kryptering
=========================================================

Vanliga frågor om RMS-certifikat, nycklar och kryptering
--------------------------------------------------------

-   [Vilka krypteringsalgoritmer används i RMS?](#bkmk_10)
-   [Använder RMS FIPS-certifierad kryptering?](#bkmk_11)
-   [Hanteras användarlicenser annorlunda för att medlemmarna ska kunna utvärderas dynamiskt när det gäller publiceringslicenser eller mallar som beviljar rättigheter till en distributionslista i stället för till enskilda användare?](#bkmk_12)
-   [När RMS används från en informationskiosk utfärdas ett temporärt rättighetskontocertifikat. Hur skiljer sig ett temporärt rättighetskontocertifikat från ett vanligt rättighetskontocertifikat? Hur känner RMS av att en informationskiosk används?](#bkmk_13)
-   [När används temporära rättighetskontocertifikat?](#bkmk_14)
-   [Utfärdas X.509v3-certifikat i RMS?](#bkmk_15)
-   [Var lagras XrML-certifikat?](#bkmk_16)
-   [Var lagras datorns privata/offentliga nyckelpar?](#bkmk_17)
-   [Var lagras klientens privata/offentliga nyckelpar?](#bkmk_18)
-   [AES är en symmetrisk algoritm. Hur skickas nycklarna på ett säkert sätt mellan servern och användaren?](#bkmk_19)

<span id="BKMK_10"></span>
#### Vilka krypteringsalgoritmer används i RMS?

I RMS används 2048-bitars RSA-nycklar för RMS-servern och 1024-bitars RSA-nycklar för användarens och datorns nyckelpar.

<span id="BKMK_11"></span>
#### Använder RMS FIPS-certifierad kryptering?

I RMS med Service Pack 1 och senare används FIPS-certifierad AES-kryptering för lockboxar som genererats i RMS-klientprogrammet när klienten är installerad på en dator där Windows XP eller Windows Server 2003 körs. Om RMS-klienten är installerad på en dator där Windows 2000 körs installeras inte något FIPS-certifierat AES-bibliotek, så de lockboxarna är inte FIPS-kompatibla.

<span id="BKMK_12"></span>
#### Hanteras användarlicenser annorlunda för att medlemmarna ska kunna utvärderas dynamiskt när det gäller publiceringslicenser eller mallar som beviljar rättigheter till en distributionslista i stället för till enskilda användare?

Användarlicenser utfärdas alltid till enskilda användare. Om en publiceringslicens eller mall namnger en grupp utvärderas gruppmedlemskapet i RMS när användarlicensen utfärdas. Om användaren som begär licensen är medlem i den namngivna gruppen utfärdas användarlicensen till användarens identitet.

<span id="BKMK_13"></span>
#### När RMS används från en informationskiosk utfärdas ett temporärt rättighetskontocertifikat. Hur skiljer sig ett temporärt rättighetskontocertifikat från ett vanligt rättighetskontocertifikat? Hur känner RMS av att en informationskiosk används?

I det RMS-aktiverade programmet avgörs om RMS-klienten ska begära ett temporärt eller vanligt rättighetskontocertifikat för användaren. Det finns ingen identifieringsmetod för den här situationen. Microsoft Office 2003 är ett exempel på ett RMS-aktiverat program där användaren kan välja lämpligt rättighetskontocertifikat.

Den största skillnaden mellan ett temporärt rättighetskontocertifikat och ett vanligt är en säkerhetsidentifierare för användare samt hur giltighetstiden anges. Temporära rättighetskontocertifikat har ingen säkerhetsidentifierare för användare och giltighetstiden anges i antal minuter. Giltighetstiden för ett temporärt rättighetskontocertifikat är som standard 15 minuter. Ett standardrättighetskontocertifikat innehåller en säkerhetsidentifierare för användare och giltighetstiden anges i antal dagar. Giltighetstiden för ett standardrättighetskontocertifikat är normalt 365 dagar.

<span id="BKMK_14"></span>
#### När används temporära rättighetskontocertifikat?

Temporära rättighetskontocertifikat gör det möjligt för användare att använda RMS-skyddat innehåll på datorer som uppfyller något av följande krav:

-   En dator som inte är medlem i samma skog som den RMS-installation som rättighetskontocertifikatet erhölls från.
-   En dator som inte är medlem i samma skog som användarkontot finns i.
-   Användaren kommer kanske inte att använda samma dator vid ett senare tillfälle.

Datorer som uppfyller de här kraven kan exempelvis finnas på flygplatsterminaler, offentliga bibliotek och Internet-kaféer.

<span id="BKMK_15"></span>
#### Utfärdas X.509v3-certifikat i RMS?

Nej. XrML-certifikaten som utfärdas i RMS är avsedda att representera användare och ett principuttryck som inte omfattas av X.509v3-certifikat.

<span id="BKMK_16"></span>
#### Var lagras XrML-certifikat?

I ett RMS-system används följande certifikat och licenser som sparas i XrML på klientdatorn.

-   Datorcertifikat
    Filnamn: Filen CERT-Machine.drm
    Plats: %USERPROFILE%\\Local Settings\\Application Data\\Microsoft\\DRM\\
-   Rättighetskontocertifikat
    Prefix för filnamn: GIC
    Plats: %USERPROFILE%\\Local Settings\\Application Data\\Microsoft\\DRM
-   Klientlicensieringscertifikat
    Prefix för filnamn: CLC
    Plats: %USERPROFILE%\\Local Settings\\Application Data\\Microsoft\\DRM
-   Användarlicens
    Prefix för filnamn: EUL
    Plats: %USERPROFILE%\\Local Settings\\Application Data\\Microsoft\\DRM

| ![](images/Cc747725.note(WS.10).gif)Obs!                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------|
| Ett användarkonto har ett enda datorcertifikat, en GIC-fil och en CLC-fil, men flera EUL-filer för varje del av innehållet som används. |

| ![](images/Cc747725.note(WS.10).gif)Obs!                           |
|-------------------------------------------------------------------------------------------------|
| För RMS-klienten i Windows Vista® gäller platsen %USERPROFILE%\\AppData\\Local\\Microsoft\\DRM. |

<span id="BKMK_17"></span>
#### Var lagras datorns privata/offentliga nyckelpar?

Datorns privata nyckel lagras säkert och skyddas av krypteringsnycklar som är kopplade till användarens inloggningsinformation och datorkonfiguration.

<span id="BKMK_18"></span>
#### Var lagras klientens privata/offentliga nyckelpar?

Nyckelparet för ett användarkonto lagras i rättighetskontocertifikatet.

<span id="BKMK_19"></span>
#### AES är en symmetrisk algoritm. Hur skickas nycklarna på ett säkert sätt mellan servern och användaren?

Både symmetriska och privata/offentliga nycklar används i systemet. Innehållet krypteras med en symmetrisk nyckel men de andra nycklarna i systemet (för användare, datorer och servrar) är offentliga/privata RSA-nycklar. Den symmetriska innehållsnyckeln krypteras alltid i de olika licenserna – antingen till RMS-serverns offentliga RSA-nyckel i publiceringslicensen eller till användarens offentliga RSA-nyckel i användarlicensen.
