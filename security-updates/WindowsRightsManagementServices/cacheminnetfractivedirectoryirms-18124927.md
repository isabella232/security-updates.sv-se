---
TOCTitle: Cacheminnet för Active Directory i RMS
Title: Cacheminnet för Active Directory i RMS
ms:assetid: 'c721a2eb-2fe9-4346-b426-3cc169b97265'
ms:contentKeyID: 18124927
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747662(v=WS.10)'
---

Cacheminnet för Active Directory i RMS
======================================

Varje RMS-rotcertifikatserver, RMS-kluster och licensieringsserver har ett lokalt cacheminne för Active Directory som innehåller resultatet av frågor om gruppmedlemskap som ställs till den globala katalogen i Active Directory. Utöver det cacheminne som finns på varje server finns ett delat cacheminne för varje kluster som sparas i katalogtjänstdatabasen. Avsikten med dessa cacheminnen är att minska antalet frågor som skickas till den globala katalogen och att minska svarstiden för licensieringsbegäran.

När en användare begär en användarlicens måste den server som svarar bedöma om användaren har beviljats de nödvändiga rättigheterna i publiceringslicensen. I det enklaste fallet anges namnet på användaren som begär en licens direkt i publiceringslicensen. I många fall ger den person som skapar information rättigheter till en grupp i stället för enskilda användare.

Om publiceringslicensen inte innehåller användarens namn utan i stället ger rättigheter till en grupp, måste servern ta reda på vilka grupper användaren är medlem av för att kunna avgöra om användaren tillhör en grupp som har beviljats rättigheter. För att ta reda på detta skickar servern en LDAP-fråga till den globala katalogen.

På RMS-servrar sparas resultatet av alla frågor om gruppmedlemskap både i det lokala cacheminnet för Active Directory och i klustrets katalogtjänstdatabas. Servrarna kan sedan hämta information om gruppmedlemskap från dessa cacheminnen, vilket minskar antalet frågor de måste skicka till den globala katalogen. Som standard skickas frågan till den server som finns närmast, men du kan konfigurera registernyckeln GC och ange vilka servrar som frågor ska skickas till. Mer information om den här inställningen finns i ”Ändra registerinställningar för anslutningspool” i ”Använda en RMS-server”.

När en server ska ta kontrollera gruppmedlemskap kontrollerar den först cacheminnet för att se om där finns information om gruppmedlemskap för den användare som sparats där. Om så inte är fallet kontrollerar servern klustrets katalogtjänstdatabas. Om informationen om gruppmedlemskap inte sparas i denna databas skickar servern frågan till den globala katalogen.

För användare och grupper sparas följande Active Directory-attribut i cacheminnet:

-   mail
-   ProxyAddresses (endast SMTP e-postadresser)
-   objectSID
-   sidHistory
-   memberOf (GUID för grupper som användaren eller gruppen är medlem av)

Posterna i det lokala cacheminnet för Active Directory tidsstämplas. Registerinställningarna anger giltighetstiden för poster i cacheminnet och hur många poster som kan sparas i det. De här inställningarna kan påverka servrarnas prestanda. Mer information finns i ”Ändra cacheinställningar för Active Directory” i ”Använda en RMS-server”.
