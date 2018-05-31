---
TOCTitle: 'Planera för externa RMS-användare'
Title: 'Planera för externa RMS-användare'
ms:assetid: '107e1338-4dcf-4ed5-a49d-e875cc883db1'
ms:contentKeyID: 18124629
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720190(v=WS.10)'
---

Planera för externa RMS-användare
=================================

I det här avsnittet beskrivs topologier som du kan implementera så att externa användare ska kunna använda RMS-skyddat innehåll från organisationen via Internet.

Du kan distribuera RMS-kluster för användning både internt och externt genom att använda något av följande alternativ:

-   Ange en URL som går att komma åt via Internet som sökväg till rotcertifikatklustret. Kontrollera att den URL:en identifieras i intranätet till RMS-servrar för samma kluster. När du gör det fungerar URL:en för den publiceringslicens som användardatorerna använder vid licensförvärv både i intranätet och via Internet.
-   Konfigurera ett separat RMS-kluster som används enbart för Internet-publicering. Det innehåll som behöver licensieras från Internet publiceras i det här klustret. Om innehållet måste vara tillgängligt både internt och externt ska det publiceras på båda platserna. Användarna måste dessutom ha åtkomst till Internet-servern.

Tillåta externa användare
-------------------------

Du kan inkludera externa användare i RMS-installationen genom att skapa interna konton för de användarna och bevilja dem åtkomst till företagsnätverket via ett virtuellt privat nätverk (VPN). Kontot kan ha en intern e-postlåda och en e-postadress som går till en extern e-postlåda.

Om du använder en intern e-postlåda måste interna utgivare ange den e-postadress som är associerad med den interna e-postlådan (inte den e-postadress som den externa användaren har utanför er organisation) när de publicerar RMS-skyddat innehåll. Om du använder en extern e-postlåda måste interna utgivare komma ihåg att ange kontots externa e-postadress när de publicerar RMS-skyddat innehåll.

Du kan skapa en separat Active Directory-skog för partnerkonton om du vill upprätthålla nätverkssäkerhet även när externa användare beviljas nätverksåtkomst. Med den här topologin kan du skapa ett separat rotcertifikatkluster för den del av RMS-systemet som är tillgänglig via Internet. Det här gör det möjligt för externa användare att ta emot RMS-datorcertifikat och rättighetskontocertifikat från det rotcertifikatkluster som är tillgängligt via Internet första gången de får tillgång till RMS-skyddat innehåll.

Om du bestämmer dig för att implementera en separat skog med partnerkonton för externa medarbetare måste RMS installeras i den skogen. Sedan kan du använda RMS-funktionen för betrodd publiceringsdomän till att etablera ett förtroendeförhållande mellan de två RMS-servrarna. Du måste också göra så att de externa DNS-registren identifierar den externa kluster-URL:en i RMS-installationen i den skog som du skapar åt de externa medarbetarna. När du har skapat ett sådant förtroendeförhållande kan den externa RMS-servern utfärda användarlicenser för allt innehåll som skapas i det interna RMS-systemet och vice versa.

Ett alternativ till att konfigurera en RMS-server i den externa skogen är att använda en server, t.ex. en ISA-server, till att filtrera den ingående trafiken och dirigera RMS-proxylicensbegäran till den interna RMS-servern.

Använda externa certifikat
--------------------------

Du kan bevilja externa användare åtkomst till RMS-skyddat innehåll genom att konfigurera en separat RMS-licensieringsserver som är tillgänglig via Internet, publicera innehållet från licensieringsservern och sedan ange förtroenderelationer på servern.

Den del av RMS-distributionen som är tillgänglig via Internet är en separat licensieringsserver som enbart används för åtkomst via Internet. Servern är en del av samma kluster som de interna licensieringsservrarna och den använder samma databas och samma URL, men det är den enda server som accepterar inkommande Internet-trafik.

När externa användare begär användarlicenser från den här RMS-licensieringsservern används rättighetskontocertifikat från en annan RMS-certifieringstjänst som den här licensieringsservern måste ha förtroende för.

#### Skapa förtroende för Passport-baserade rättighetskontocertifikat

Organisationen kan välja att skapa förtroende för rättighetskontocertifikat som är baserade på Microsoft .NET Passport-inloggningsinformation. Med sådana kontocertifikat krävs att användare hämtar rättighetskontocertifikat direkt från Microsofts certifieringstjänst på Internet.

I den här modellen tar externa användare emot RMS-datorcertifikat och rättighetskontocertifikat från Microsoft. När innehållet publiceras måste de externa användarnas Microsoft .NET Passport-konto anges som mottagare i publiceringslicensen.

Microsoft® .NET Passport-kontot måste matcha det .NET Passport-konto som användes när användaren hämtade rättighetskontocertifikatet från Microsoft. Utgivaren måste ange det kontot när mottagare läggs till i det RMS-aktiverade programmet. Om inte kontona matchar kommer inte användaren åt innehållet.

#### Skapa förtroende för andra externa certifikat

Om de externa användarnas företag också använder en RMS-distribution kan du välja att upprätta ett förtroende med det företaget. Det gör du genom att be företaget att exportera sitt RMS-serverlicensieringscertifikat och skicka det till dig. Du kan sedan importera certifikatet med hjälp av konsolen för RMS-administration för den licensieringsserver som är tillgänglig från Internet.
