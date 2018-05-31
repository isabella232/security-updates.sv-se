---
TOCTitle: 'Vanliga frågor om RMS: Administration'
Title: 'Vanliga frågor om RMS: Administration'
ms:assetid: '43f77336-5e62-4405-9efb-55417a402d62'
ms:contentKeyID: 18124721
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747547(v=WS.10)'
---

Vanliga frågor om RMS: Administration
=====================================

Vanliga frågor om RMS-administration
------------------------------------

-   [Vilket är det bästa sättet att återkalla behörigheterna till dokument för en användare som lämnar en organisation?](#bkmk_1)
-   [Jag ska upprätta förtroende mellan två organisationer som ska utbyta RMS-innehåll. Måste XrML-licenscertifikatet som skickas till det betrodda företaget hanteras på något särskilt sätt?](#bkmk_2)
-   [Hur fungerar profiler för mobila användare i RMS?](#bkmk_3)
-   [Varför skulle en organisation vilja inaktivera RMS?](#bkmk_4)
-   [Hur går hela inaktiveringsprocessen till?](#bkmk_5)
-   [Kan man inaktivera en RMS-server så att endast vissa användare kan återställa dokument?](#bkmk_6)
-   [Vad betyder ”Servern kan inte komma åt tillämpningskatalogen”?](#bkmk_7)
-   [Kan jag använda spårning med RMS-servern?](#bkmk_8)
-   [Vad är tidsavvikelse och hur ska jag hantera det?](#bkmk_9)

<span id="BKMK_1"></span>
#### Vilket är det bästa sättet att återkalla behörigheterna till dokument för en användare som lämnar en organisation?

I allmänhet är det bäst att låta dokument vara licensierade till användargrupper som definieras i Active Directory i stället för till enskilda användarkonton. När en användare lämnar en organisation kan du ta bort användaren från Active Directory-gruppen. Användaren kan då inte läsa dokument som skickas till gruppen. Användaren kan dock fortfarande läsa dokument som har befintliga användarlicenser, om inte dokumentens rättigheter har konfigurerats så att användaren måste få en användarlicens varje gång dokumentet öppnas. Om den rättigheten inte har definierats är det enda sättet att hindra användaren från att öppna dokument med befintliga användarlicenser att radera användarens licensarkiv på hans/hennes dator.

<span id="BKMK_2"></span>
#### Jag ska upprätta förtroende mellan två organisationer som ska utbyta RMS-innehåll. Måste XrML-licenscertifikatet som skickas till det betrodda företaget hanteras på något särskilt sätt?

När du upprättar en betrodd användardomän eller publiceringsdomän väljer du att ge partnerorganisationen förtroende att ingå i rättighetshanteringssystemet. Du tar alltså en beräknad risk att din information inte komprometteras genom att du litar på den andra organisationen. Du bör be partnerorganisationen att skicka sitt RMS-serverlicensieringscertifikat via en autentiserad kanal, t.ex. S/MIME-e-post. Det minskar risken för att serverlicensieringscertifikatet ska manipuleras innan du importerar det i RMS-servern.

<span id="BKMK_3"></span>
#### Hur fungerar profiler för mobila användare i RMS?

Rättighetskontocertifikat (RAC) som används till att identifiera användare är datorspecifika. När mobila användarprofiler används skapas ett nytt rättighetskontocertifikat för användaren på en dator första gången RMS används på den datorn.

<span id="BKMK_4"></span>
#### Varför skulle en organisation vilja inaktivera RMS?

När du inaktiverar RMS tas RMS-servern bort ur infrastrukturen, vilket gör att användare kan spara rättighetsskyddat innehåll utan skydd. Det finns tre huvudsakliga anledningar till att organisationer väljer att göra detta:

-   Man vill förenkla arkitekturen, t.ex. när servrar konsolideras i ett kluster.
-   Man vill migrera en koncepttestad pilotmiljö till produktionsmiljö.
-   Man vill slå samman RMS-servrar, t.ex. efter ett företagsköp.

<span id="BKMK_5"></span>
#### Hur går hela inaktiveringsprocessen till?

Inaktiveringsprocessen startar du från RMS-rotklustret genom att starta inaktiveringstjänsten. När inaktiveringstjänsten har startats inaktiveras alla andra tjänster (exempelvis licensiering och certifiering). Sedan måste varje användares RMS-aktiverade program dirigeras så att de ansluts till inaktiveringstjänsten när en RMS-funktion används. Microsoft Office 2003 är ett exempel på ett RMS-aktiverat program. I Office 2003 dirigeras RMS-klienten till RMS-tjänsterna med hjälp av registernycklar. En specifik registernyckel identifierar inaktiveringstjänsten. När nyckeln har konfigurerats så att den dirigerar klienten till inaktiveringstjänsten beviljar RMS-klustret användarlicenser som ger användaren fullständiga behörigheter (läsa, skriva, kopiera, skriva ut, redigera osv.) till innehållet, oavsett om användaren ursprungligen hade dessa behörigheter eller inte. Användare uppmanas sedan att ta bort allt rättighetsskydd från alla dokument som de vill behålla när RMS-klustret inaktiveras fullständigt. När du är klar med det kan du koppla bort RMS-klustret helt.

Du bör säkerhetskopiera RMS-klustrets konfigurationsdatabas, ifall du skulle behöva återställa ett rättighetsskyddat dokument när klustret har tagits ur drift. Utan RMS-rotklustrets privata nyckel är det bara dokumentets skapare som kan öppna rättighetsskyddat innehåll när servern har tagits bort.

<span id="BKMK_6"></span>
#### Kan man inaktivera en RMS-server så att endast vissa användare kan återställa dokument?

Du kan använda en åtkomstkontrollista (ACL) till inaktiveringswebbtjänsten (decommission.asmx) för att kontrollera åtkomsten till inaktiveringstjänsten, så att endast vissa användare kan få tillgång till dekrypteringsnyckeln för rättighetsskyddat innehåll.

<span id="BKMK_7"></span>
#### Vad betyder ”Servern kan inte komma åt tillämpningskatalogen”?

Det här felet uppstår ibland när du försöker öppna webbplatsen Administration av RMS när du har installerat RMS. Om det felmeddelandet visas kan du inte konfigurera eller administrera RMS.

Felet uppstår vanligen när Internet Information Services (IIS) körs i IIS 5.0-isoleringsläge. Du kan lösa problemet genom att utföra följande procedur, så avaktiveras inställningen på servern. Sedan startar du om IIS.

**Så här avaktiverar du IIS 5.0-isoleringsläge**
1.  Logga in på RMS-servern som medlem i den lokala administratörsgruppen.

2.  Klicka på **Start**, peka på **Administrationsverktyg** och klicka på **Internet Information Services-hanteraren**.

3.  I **IIS Manager** expanderar du den lokala datorn, högerklickar på **Webbplatser** och klickar sedan på **Egenskaper**.

4.  Klicka på fliken **Tjänst**, avmarkera kryssrutan **Kör WWW-tjänsten i IIS 5.0-isoleringsläge** och klicka sedan på **OK**.

5.  Den här ändringen kräver att IIS-tjänsten startas om. Klicka på **Ja** när du uppmanas att starta om IIS-tjänsten.

<span id="BKMK_8"></span>
#### Kan jag använda spårning med RMS-servern?

Eftersom Rights Management Services är skapat med hjälp av Microsoft® .NET Framework kan du aktivera spårning för att spåra systemhändelser och felsöka problem.

Du implementerar spårning genom att ändra någon av filerna Web.config eller Machine.config. När du implementerar spårning i filen Machine.config utförs spårning av alla programvarukomponenter på datorn. Om du däremot implementerar spårning i filen Web.config spåras endast händelser som inträffar i webbtjänsterna.

**Så här aktiverar du spårning**
1.  Öppna någon av filerna Machine.config eller Web.config och lägg sedan till följande rader under avsnittet &lt;system.diagnostics&gt; i filen:

    ```
        <system.diagnostics>
        <switches>
        <add name="Microsoft Windows Rights Management Services-Global" value="4" />
        <add name="Microsoft Windows Rights Management Services-TimeStamps" value="1" /> 
        <add name="Microsoft Windows Rights Management Services-Indents" value="0" /> 
        </switches>
        <trace autoflush="false" indentsize="4"/>
        </system.diagnostics>
    ```
    
2.  Starta om IIS genom att köra IISRESET i kommandotolken.

3.  När du har samlat in de data som du behöver tar du bort dessa rader från den aktuella CONFIG-filen.

4.  Starta om IIS genom att köra IISRESET i kommandotolken.

> [!IMPORTANT]  
> När du använder spårning på en RMS-server kan det påverka serverns prestanda, t.ex. i form av fördröjningar vid hämtning av användarlicenser och utfärdande av rättighetskontocertifikat. Använd bara spårning i de specifika fall då du vill diagnostisera och felsöka fel som har uppstått.

<span id="BKMK_9"></span>
#### Vad är tidsavvikelse och hur ska jag hantera det?

Tidsavvikelse är när klocktiden på en dator skiljer sig från klocktiden på en annan dator. Detta är inget ovanligt (normalt handlar det om små avvikelser) och är inte konstigare än att armbandsuren hos två personer i ett och samma rum visar något olika tid. Tidsavvikelse kan orsaka problem när du anger en giltighetstid i en licens.

En giltighetstid i en licens anges enligt klockan på utgivarens dator. Tidsavvikelse kan orsaka problem vid två olika tillfällen under publicerings- och användningscyklerna:

-   När ett försök utförs från ett program att hämta en användarlicens med en publiceringslicens vars giltighetstid antingen har upphört att gälla eller inte har börjat gälla än, enligt RMS-serverns klocka. I det fallet misslyckas begäran. Det kan hända slutanvändare när de begär en användarlicens eller för program som försöker förlicensiera ett dokument (d.v.s. hämta en användarlicens för en användare).
-   Om licensens giltighetstid har upphört att gälla (eller inte har börjat gälla än) går det inte att använda användarlicensen. Annars är det bara de rättigheter som har upphört att gälla (eller som inte gäller än) som inte fungerar.

Om klockan på utgivarens dator t.ex. går 15 minuter efter klockan på användarens dator och utgivaren skapar en publiceringslicens som anger att innehållet upphör att gälla om 15 minuter, så får användaren en oanvändbar användarlicens från servern eftersom rättigheterna att visa innehållet redan har upphört att gälla.

Det finns ingen riktigt bra lösning på problem som orsakas av tidsavvikelse. En godtagbar lösning är att ange att en rättighets giltighetstid ska börja tidigare än den aktuella tiden, för användare med datorer vars klockor går efter klockan på din dator. Om möjligt kan du också förlänga licensens giltighetstid för användare med datorer vars klockor går före klockan på din dator. Du bör ha problemet med tidsavvikelser i åtanke, särskilt när du skapar licenser med korta giltighetstider.
