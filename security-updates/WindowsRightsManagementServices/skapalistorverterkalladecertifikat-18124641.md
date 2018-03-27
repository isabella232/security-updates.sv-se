---
TOCTitle: Skapa listor över återkallade certifikat
Title: Skapa listor över återkallade certifikat
ms:assetid: '1ef75199-3344-4225-84de-a863a777696a'
ms:contentKeyID: 18124641
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720208(v=WS.10)'
---

Skapa listor över återkallade certifikat
========================================

När du implementerar återkallning måste du distribuera en lista över återkallade certifikat, vilket är ett XML-dokument där XrML-kod (eXtensible Rights Markup Language) används och där de enheter som inte längre ska ha åtkomst till rättighetsskyddat innehåll räknas upp. Listor över återkallade certifikat måste ha en giltig tidsstämpel och vara korrekt signerade med verktyget Revocation List Signing (RLsigner.exe) som ingår i RMS.

> [!IMPORTANT]  
> För att kunna signera listan över återkallade certifikat med hjälp av RLsigner.exe måste du spara listan i form av en unicode-fil. |

Exempel på en lista över återkallade certifikat
-----------------------------------------------

I det här avsnittet presenteras ett exempel på en komplett lista över återkallade certifikat, som visar var och en av de möjliga metoderna för återkallning. Du kan använda det här exemplet som en modell för hur du skapar egna listor över återkallade certifikat.

En lista över återkallade certifikat är en XML-fil som använder XrML-kod.

BODY-elementet innehåller fyra underordnade element:

-   **ISSUEDTIME**. Innehåller datum och tid för när listan över återkallade certifikat utfärdades. Det här elementet infogas i filen med verktyget RLsigner.exe. I exemplet nedan ingår elementet endast för att visa den övergripande strukturen i filen.
-   **DESCRIPTOR**. Innehåller data som identifierar filen som en lista över återkallade certifikat.
-   **ISSUER**. Innehåller data som identifierar den enhet som utfärdade listan över återkallade certifikat.
-   **REVOCATIONLIST**. Innehåller underordnade REVOKE-element som anger vilka enheter som återkallas med listan.

Nedan visas ett exempel på en lista över återkallade certifikat.

> [!IMPORTANT]  
>  Elementen ISSUEDTIME, PUBLICKEY och SIGNATURE kan utelämnas eftersom de infogas eller skrivs över av RLsigner.exe.

   ```
        <?xml version="1.0" ?> 
            <XrML xml:space=”preserve” version=”1.2”>
                <BODY type="LICENSE" version="3.0">
            <ISSUEDTIME>...</ISSUEDTIME> 
            <DESCRIPTOR>
            <OBJECT type="Revocation-List">
                <ID type="MS-GUID">{d6373cba-01f1-4f32-ac58-260f580af0f8}</ID>
            </OBJECT>
            </DESCRIPTOR>
            <ISSUER>
            <OBJECT type="Revocation-List">
                <ID type="acsii-tag">External revocation authority</ID>
                <NAME>Revocation list name</NAME>
                <ADDRESS type="URL">https://somedomain.com/revocation_list_file</ADDRESS>
            </OBJECT>
            <PUBLICKEY>...</PUBLICKEY>
            </ISSUER>
            <REVOCATIONLIST>
            <REVOKE>...<\REVOKE>
            <REVOKE>...<\REVOKE>
            </REVOCATIONLIST>
            <SIGNATURE>...</SIGNATURE>
        </XrML>
   ```

> [!CAUTION]  
> När du anger URL-sökväg till listan över återkallade certifikat kan du inte längre ange en UNC-sökväg i SP1 eller RMS med SP2. Du måste ange en URL-sökväg. 

När du har definierat REVOKE-elementen är listan över återkallade certifikat klar att signeras.

Använda elementet REVOKE
------------------------

I den lista över återkallade certifikat som anges i avsnittet "Exempel på en lista över återkallade certifikat" anger varje REVOKE-element en enhet som ska återkallas. Starttaggen har kategori- och typattribut som definierar vad som återkallas och enligt vilka identifieringskriterier detta sker. Olika REVOKE-element har olika underordnade element beroende på vilken åtgärd som anges av kategori- och typattributen.

Mer information om att ange REVOKE-element finns i följande exempel:

-   [Återkalla enheter baserat på en offentlig nyckel](#bkmk_1)
-   [Återkalla certifikat och licenser baserat på GUID](#bkmk_2)
-   [Återkalla certifikat och licenser baserat på hashvärde](#bkmk_3)
-   [Återkalla certifikat och licenser baserat på utfärdarens offentliga nyckel](#bkmk_4)
-   [Återkalla certifikat och licenser baserat på utfärdar-ID](#bkmk_5)
-   [Återkalla innehåll baserat på innehålls-ID](#bkmk_6)
-   [Återkalla certifikat baserat på enhets-ID](#bkmk_10)
-   [Återkalla enheter baserat på Windows Live-ID](#bkmk_7)

<span id="BKMK_1"></span>
#### Återkalla enheter baserat på en offentlig nyckel

I det här exemplet återkallas en enhet baserat på den offentliga nyckeln. Innehållet i <PUBLICKEY>-taggen hämtas från noden <BODY><ISSUEDPRINCIPALS><PRINCIPAL><PUBLICKEY> i det certifikat som utfärdade nyckeln.

   ```
        <REVOKE category="principal" type="principal-key">
            <PUBLICKEY>
            <ALGORITHM>RSA-1024</ALGORITHM>
            <PARAMETER name="public exponent">
                <VALUE encoding="integer32">65537</VALUE>
            </PARAMETER>
            <PARAMETER name="modulus">
                <VALUE encoding="base64" size="1024">
    6Jn0kEAWU+1AFWtuUmBYL8Jza8tLhUv/BCmgcq/Pc08Au3DvXkH65s+0MEyZjM+71j3F1xaXUSst+wH2FjApkY1RxgL8VAKIuEvIy9hRrvY1YhJx/0Ite5fZeg2crUFrmoQgZzaJ50FvoakA2QMgZZgxoQmwiGE0y40cEJtIlE0=
                </VALUE>
            </PARAMETER>
            </PUBLICKEY>
        </REVOKE>
   ```

<span id="BKMK_2"></span>
#### Återkalla certifikat och licenser baserat på GUID

I det här exemplet återkallas ett certifikat eller en licens baserat på GUID (Globally Unique IDentifier). Det går inte att använda ett certifikat eller en licens med ett matchande GUID när den här listan över återkallade certifikat används. Innehållet i <ID>-taggen i det här exemplet är hämtat från noden <BODY><DESCRIPTOR><OBJECT><ID> i det certifikat eller den licens som återkallas. (Du kan även återkalla program med den här metoden genom att ange programmanifestets ID.)

   ```
        <REVOKE category="license" type="license-id">
            <OBJECT>
            <ID type="MS-GUID">{06BCB94D-43E5-419f-B180-AA9FD321ED7A}</ID>
            </OBJECT>
        </REVOKE>
   ```

#### Återkalla med programmanifest

Om du vill utföra återkallningar med programmanifest måste du antingen extrahera utfärdarens ID eller offentliga nyckel, licens-ID:t eller licenshashvärdet ur programmanifestet. Programmanifest är bas-64-kodade, så den informationen är inte tillgänglig i ren text. Med Rights Management Services Software Development Kit (SDK) kan du utveckla ett program med metoderna DRMConstructCertificateChain, DRMDeconstructCertificateChain och DRMDecode, som du kan använda till att avkoda programmanifestet och på så sätt få tillgång till den information som behövs.

Om du vill blockera vissa programs möjligheter att hantera rättighetsskyddat innehåll bör du överväga att använda programexkludering för att förhindra att användningslicenser tilldelas de programmen via RMS-klustret. Begränsningen för exkludering är att det inte kan hindra någon med en giltig användningslicens från att dekryptera rättighetsskyddat innehåll. Mer information om programexkludering finns i [Exkludera program](https://technet.microsoft.com/b68ae4b2-b9ba-44ae-90cb-c88df600ec86) tidigare i det här avsnittet.

<span id="BKMK_3"></span>
#### Återkalla certifikat och licenser baserat på hashvärde

I det här exemplet återkallas ett certifikat eller en licens baserat på hashvärdet. Innehållet i <VALUE>-taggen är SHA-1-hashvärdet för alla UNICODE-tecken mellan <BODY> och </BODY> i certifikatet eller licensen. Du hittar hashvärdet i avsnittet <SIGNATURE> i certifikatet eller licensen. (Du kan även återkalla program med den här metoden genom att ange programmanifestets hashvärde.)

   ```
        <REVOKE category="license" type="license-hash">
        <DIGEST>
          <ALGORITHM>SHA1</ALGORITHM>
          <VALUE encoding="base64" size="160">
            ABfB4mcEslVCMEZR9reACqXHCoQ=
          </VALUE>
        </DIGEST>
      </REVOKE>
   ```



#### Återkalla med programmanifest

Om du vill utföra återkallningar med programmanifest måste du antingen extrahera utfärdarens ID eller offentliga nyckel, licens-ID:t eller licenshashvärdet ur programmanifestet. Men programmanifest är bas-64-kodade, så den informationen är inte tillgänglig i ren text. Med Rights Management Services SDK kan du utveckla ett program med metoderna DRMConstructCertificateChain, DRMDeconstructCertificateChain och DRMDecode, som du kan använda till att avkoda programmanifestet och på så sätt få tillgång till den information som behövs.

Om du vill blockera vissa programs möjligheter att hantera rättighetsskyddat innehåll bör du överväga att använda programexkludering för att förhindra att användningslicenser tilldelas de programmen via RMS-klustret. Begränsningen för exkludering är att det inte kan hindra någon med en giltig användningslicens från att dekryptera RMS-skyddat innehåll. Mer information om programexkludering finns i [Exkludera program](https://technet.microsoft.com/b68ae4b2-b9ba-44ae-90cb-c88df600ec86) tidigare i det här avsnittet.

<span id="BKMK_4"></span>
#### Återkalla certifikat och licenser baserat på utfärdarens offentliga nyckel

I det här exemplet återkallas alla certifikat och licenser som har utfärdats av ägaren till den angivna offentliga nyckeln. Innehållet i <PUBLICKEY>-taggen hämtas från noden <BODY><ISSUER><PUBLICKEY> i de certifikat eller de licenser som återkallas.

   ```
        <REVOKE category="license" type="issuer-key">
            <PUBLICKEY>
            <ALGORITHM>RSA-1024</ALGORITHM>
            <PARAMETER name="public exponent">
                <VALUE encoding="integer32">65537</VALUE>
            </PARAMETER>
            <PARAMETER name="modulus">
                <VALUE encoding="base64" size="1024">
    AAn0kEAWU+1AFWtuUmBYL8Jza8tLhUv/BCmgcq/Pc08Au3DvXkH65s+0MEyZjM+71j3F1xaXUSst+wH2FjApkY1RxgL8VAKIuEvIy9hRrvY1YhJx/0Ite5fZeg2crUFrmoQgZzaJ50FvoakA2QMgZZgxoQmwiGE0y40cEJtIlE0=
                </VALUE>
            </PARAMETER>
            </PUBLICKEY>
        </REVOKE>
   ```

<span id="BKMK_5"></span>
#### Återkalla certifikat och licenser baserat på utfärdar-ID

I det här exemplet återkallas en uppsättning med certifikat eller licenser baserat på utfärdar-ID. Innehållet i <ID>-taggen är noden <BODY><ISSUER><OBJECT><ID> i de certifikat eller de licenser som återkallas.

   ```
        <REVOKE category="license" type="issuer-id">
        <OBJECT type="MS-DRM-Server">
          <ID type="MS-GUID">{2BE9E200-3040-41B9-8832-D4D0445EBBD6}</ID> 
        </OBJECT>
      </REVOKE>
   ```

> [!NOTE]  
> Kontrollera att det inte finns någon vagnretur mellan det globala unika ID:t (GUID) och den avslutande taggen när du anger ID-typ. Om en vagnretur av misstag har lagts till går det inte att tolka listan över återkallade certifikat i RMS-klienten.

<span id="BKMK_6"></span>
#### Återkalla innehåll baserat på innehålls-ID

I det här exemplet återkallas skyddat innehåll baserat på innehålls-ID. Den här metoden är att rekommendera när du återkallar innehåll, eftersom innehålls-ID:t är identiskt i alla licenser som skapas från en viss publiceringslicens. Värdet i noden <OBJECT> hittar du i noden <BODY><WORK><OBJECT> i en publiceringslicens eller en användningslicens för innehållet.

   ```
        <REVOKE category="content" type="content-id">
        <OBJECT type="Microsoft Office Document">
          <ID type="MS-GUID">{8702641D-3512-4AA4-A584-84C703A5B5C0}</ID>
        </OBJECT>
      </REVOKE>
   ```

> [!NOTE]  
> Kontrollera att det inte finns någon vagnretur mellan det globala unika ID:t (GUID) och den avslutande taggen när du anger ID-typ. Om en vagnretur av misstag har lagts till går det inte att tolka listan över återkallade certifikat i RMS-klienten.

<span id="BKMK_10"></span>
#### Återkalla enheter baserat på Windows-konto

I det här exemplet återkallas en användare eller aktiverande enhet baserat på Windows-kontot. Innehållet i elementet <OBJECT> hämtas från noden <BODY><ISSUEDPRINCIPALS><PRINCIPAL><OBJECT> i ett rättighetskontocertifikat eller en användarlicens.

   ```
        <REVOKE category="principal" type="principal-id">
        <OBJECT type="Group-Identity">
          <ID type="Windows">{Windows account SID}</ID> 
          <NAME>{E-mail address}</NAME> 
        </OBJECT>
      </REVOKE>
   ```

> [!NOTE]  
> Kontrollera att det inte finns någon vagnretur mellan Windows-kontots SID och den avslutande taggen när du anger ID-typen. Om en vagnretur av misstag har lagts till går det inte att tolka listan över återkallade certifikat i RMS-klienten.

<span id="BKMK_7"></span>
#### Återkalla enheter baserat på Windows Live-ID

I det här exemplet återkallas en användare eller aktiverande enhet baserat på Windows Live-ID. Innehållet i elementet <OBJECT> hämtas från noden <BODY><ISSUEDPRINCIPALS><PRINCIPAL><OBJECT> i ett rättighetskontocertifikat eller en användarlicens.

   ```
        <REVOKE category="principal" type="principal-id">
        <OBJECT type="Group-Identity">
          <ID type="Passport">{PUID}</ID> 
          <NAME>michael@contoso.com</NAME> 
        </OBJECT>
      </REVOKE>
   ```

> [!NOTE]  
> Kontrollera att det inte finns någon vagnretur mellan det unika enhets-ID:t (PUID) och den avslutande taggen när du anger ID-typen. Om en vagnretur av misstag har lagts till går det inte att tolka listan över återkallade certifikat i RMS-klienten.

<span id="BKMK_8"></span>
Infoga en signatur i en lista över återkallade certifikat
---------------------------------------------------------

När du har skapat en lista över återkallade certifikat måste du infoga en signatur i listan, vilket beskrivs i det här avsnittet. Du kan sedan göra listan tillgänglig för användare via den URL som du anger i den associerade principmallen för rättigheter.

Det första du gör när du vill infoga en signatur är att generera ett nyckelpar och en nyckelfil för listan över återkallade certifikat med hjälp av verktyget Sn.exe (Strong Name). Verktyget Sn.exe ingår i Microsoft .NET Framework SDK 1.1, som kan hämtas från Microsofts webbplats [http://go.microsoft.com/fwlink/?LinkId=104796](http://go.microsoft.com/fwlink/?linkid=104796).

För att kunna signera listan över återkallade certifikat med RLsigner.exe måste du spara den som en unicode-fil

**Gör så här om du vill använda Sn.exe både till att generera ett nytt nyckelpar och till att skriva det paret till en fil:**
1.  Skapa den privata nyckeln. Skriv följande kommando i kommandotolken och tryck sedan på RETUR:

    **sn -k** *privat\_nyckel***.snk**

    där *privat\_nyckel* är namnet på filen med den privata nyckeln.

2.  Använd Sn.exe för att extrahera den offentliga nyckeln från den nyckelparsfil som skapades i steg 1 och exportera den till en separat fil. Skriv följande kommando och tryck sedan på RETUR:

    **sn -p** *privat\_nyckel offentlig\_nyckel*

    där *privat\_nyckel* är namnet på filen med den privata nyckel som skapades i steg 1 och *offentlig\_nyckel* är namnet på den fil där den exporterade offentliga nyckeln sparas.

3.  Ändra filnamnstillägget för filen med den privata nyckeln (som skapades i steg 1) från .snk till .dat så att du kan använda den med RLsigner.exe.

4.  Infoga en signatur i listan över återkallade certifikat med hjälp av RLsigner.exe. Verktyget ingår i RMS. Som standard finns det i katalogen %systemdrive%\\Program Files\\Windows Rights Management Services\\Tools.

> [!NOTE]  
> RLsigner.exe kan inte användas med filnamn som innehåller mellanslag.

<span id="BKMK_9"></span>
Använda RLsigner.exe
--------------------

När du kör RLsigner.exe skapas först en signatur med hjälp av den privata nyckel som ingår i nyckelfilen. Därefter skapas en utdatafil som baseras på filen med listan över återkallade certifikat som du tillhandahöll.

> [!IMPORTANT]  
> Listan över återkallade certifikat måste ha sparats som en unicode-fil för att den ska kunna användas med RLsigner.exe.

Skriv in följande kommando på kommandoraden om du vill signera listan över återkallade certifikat med RLsigner.exe:

**rlsigner.exe** *indatafil* **{-f** *nyckelfil* **| -h** *behållarnamn* **CSP}** *utdatafil*

Använd följande information till att fylla i kommandots indataparametrar:

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Parameter</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;"><em>indatafil</em></td>
<td style="border:1px solid black;">Namnet på den XrML-kompatibla listan över återkallade certifikat som du har förberett</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><em>nyckelfil</em></td>
<td style="border:1px solid black;">Namnet på den fil som innehåller den offentliga och den privata nyckel som du har genererat</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><em>behållarnamn</em></td>
<td style="border:1px solid black;">Namn på nyckelbehållare</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><em>utdatafil</em></td>
<td style="border:1px solid black;">Namnet på den signerade fil med listan över återkallade certifikat som skapas av verktyget</td>
</tr>
</tbody>
</table>
  
> [!NOTE]  
> RLsigner.exe kan inte användas med filnamn som innehåller mellanslag.
  
I följande exempel beskrivs hur du använder RLsigner.exe från kommandoraden tillsammans med olika CSP:er (Cryptographic Service Providers):
  
-   Exempel på en kommandoradssyntax där en nyckelfil används:  
    **rlsigner.exe rl.xml -f nyckel.dat utdata.xml**  
-   Exempel på en kommandoradssyntax där en HSM används:  
    **rlsigner.exe rl.xml -f Container CSP utdata.xml**
  
I RLsigner.exe genereras grundläggande information om vad som har lyckats och vad som har gått fel i returkoden. I följande tabell beskrivs möjliga returkoder.
 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Returkod</th>
<th style="border:1px solid black;" >Beskrivning</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">0</td>
<td style="border:1px solid black;">Klart</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">-1</td>
<td style="border:1px solid black;">Det gick inte att läsa källfilen</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">-2</td>
<td style="border:1px solid black;">Det gick inte att läsa nyckelfilen</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">-3</td>
<td style="border:1px solid black;">Ogiltig nyckelfil</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">-4</td>
<td style="border:1px solid black;">Ogiltig källfil</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">-5</td>
<td style="border:1px solid black;">Det gick inte att skriva till utdatafilen</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">-6</td>
<td style="border:1px solid black;">Okänt fel</td>
</tr>
</tbody>
</table>
  
Om du vill kan du schemalägga signering av listor över återkallade certifikat baserat på det uppdateringsintervall som du har angett för servern.
  
Du kan automatisera signering av listor över återkallade certifikat med hjälp av ett skript. I följande VBScript-exempel anropas RLsigner.exe och resultaten skrivs till systemets händelselogg.
  
```VB
    const EVT_SUCCESS       = 0
    const EVT_ERROR         = 1
    const EVT_WARNING       = 2
    const EVT_INFORMATION   = 4
    const EVT_AUDIT_SUCCESS = 8
    const EVT_AUDIT_FAILURE = 16

    Dim WshShell, oExec

    Set WshShell = CreateObject( "WScript.Shell" )
    Set oExec = WshShell.Exec("rlsigner.exe input_file key_file output_file")
    Do While oExec.Status = 0
        WScript.Sleep 100
    Loop

    if WshShell.ExitCode <> 0 Then
        WshShell.LogEvent EVT_ERROR, "RLsigner failed with error """ + WshShell.ExitCode + """"
    else
        WshShell.LogEvent EVT_SUCCESS, "RLsigner completed successfully"
    end if
```
