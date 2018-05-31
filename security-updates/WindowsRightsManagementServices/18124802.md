---
TOCTitle: Problem med överensstämmelse mellan FIPS och RMS
Title: Problem med överensstämmelse mellan FIPS och RMS
ms:assetid: '720bdace-dcd8-431e-b0fa-01193782fe0b'
ms:contentKeyID: 18124802
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747551(v=WS.10)'
---

Problem med överensstämmelse mellan FIPS och RMS
================================================

Rights Management Services (RMS) version 1.0 Service Pack 1 (SP1) är utformat för att fungera effektivt inom organisationer med behov av FIPS-godkända krypteringsfunktioner.

FIPS 140-1 (Federal Information Processing Standard 140-1) och efterföljaren FIPS 140-2 är amerikanska standarder som riktmärker implementering av krypteringsprogramvara. Där anges hur man på bästa sätt implementerar krypteringsalgoritmer, hanterar nyckelmaterial och databuffrar samt arbetar med operativsystemet.

RMS kan implementeras som en del av ett FIPS-system som en metod att skydda konfidentiella data.

-   FIPS-godkända CSP:er (cryptographic service providers) begränsar funktionaliteten till: **TLS\_RSA\_WITH\_3DES\_EDE\_CBC\_SHA**. Med den här begränsningen tvingas den säkra kanalen att kommunicera endast genom det starkare TLS 1.0-protokollet (Transport Layer Security). Du kan behöva konfigurera Internet Explorer till att fungera med TLS, men många webbservrar från tredje part fungerar inte med TLS. Mer information om det här problemet kan du få i Knowledge Base-artikel nr 811834 på [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=43614).

Skydda den privata RMS-nyckeln med någon av Microsofts två standard-CSP:er om du ska använda det programvarubaserade standardskyddet. De CSP:erna har genomgått FIPS 140-1- eller FIPS 140-2-testning, enligt amerikanska myndighetskrav. Även om det inte är ett krav är det nödvändigt för kunder med höga krav på säkerhet att använda HSM (hardware security module) från till exempel nCipher eller IBM som skydd för privata RMS-servernycklar på en högre nivå. Om du använder HSM måste du välja rätt CSP. Du kan behöva starta om systemet. Du kan få mer information i artikel nr. 830690 på [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=44138).

När du implementerar ditt RMS-system bör du göra följande val:

-   Följ NSA:s riktlinjer för FIPS-godkänd kryptering i Windows.
-   Aktivera lokal säkerhetspolicy för FIPS-godkänd kryptering.
-   Distribuera RMS SP1-klienter och -servrar i ovanstående miljö.
-   Aktivera TLS-protokollet (Transport Layer Security) i Internet Information Services (IIS) på RMS-servern.
-   Aktivera TLS-protokollet (Transport Layer Security) i Internet Explorer på klienterna.
-   Aktivera SQL TDS-protokollet (Tabular Data Stream) som används i TLS/SSL Security Provider i Windows mellan SQL-klienter och SQL Server på databasservern.
-   Konfigurera SQL så att TSL/SSL krävs
