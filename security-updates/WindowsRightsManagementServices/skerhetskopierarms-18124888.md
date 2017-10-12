---
TOCTitle: Säkerhetskopiera RMS
Title: Säkerhetskopiera RMS
ms:assetid: 'c29894da-ee00-428c-8d48-80d8e5a83678'
ms:contentKeyID: 18124888
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747746(v=WS.10)'
---

Säkerhetskopiera RMS
====================

Säkerhetskopiera alla relevanta komponenter nedan innan du konfigurerar infrastrukturen och installerar RMS:

-   Om du ska lägga konfigurationsdatabasen och loggningsdatabasen i en befintlig SQL Server-databas säkerhetskopierar du alla databaser och serverinställningar. Kom ihåg att säkerhetskopiera tidigare konfigurations- och loggningsdatabaser om du uppgraderar en tidigare version av RMS eller installerar om RMS.
-   Säkerhetskopiera systemtillståndet för den server där RMS ska installeras. I den säkerhetskopian sparas registernycklarna och värden som innehåller den information du behöver för att återställa servern om det är nödvändigt.
-   Använd snapin-modulen för certifikat och exportera alla certifikat till en fil. Snapin-modulen för certifikat används också för säkerhetskopiering av data för privata RMS-nycklar till en PKCS \#12-fil som krypteras med ett lösenord. Om du uppgraderar eller installerar om RMS och har valt att skydda den privata RMS-nyckeln med den programvarubaserade standardkrypteringen, krypterades och lagrades nyckeln under säkerhetskopieringen av konfigurationsdatabasen.
-   Om du skyddar den privata nyckeln med en HSM (Hardware Security Module) bör du säkerhetskopiera HSM-konfigurationen med en metod som rekommenderas av tillverkaren.

Säkerhetskopiorna ska sparas på en säker lagringsplats tillsammans med det lösenord som användes vid kryptering av de privata nycklarna.
