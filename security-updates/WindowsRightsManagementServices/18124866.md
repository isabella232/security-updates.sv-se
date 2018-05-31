---
TOCTitle: Problem vid etablering av RMS
Title: Problem vid etablering av RMS
ms:assetid: 'b0e6ef48-ab38-4426-be5b-811cf64c45c0'
ms:contentKeyID: 18124866
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747638(v=WS.10)'
---

Problem vid etablering av RMS
=============================

När du etablerar RMS konfigureras och fastställs de resursfiler och anslutningar mellan olika komponenter som RMS bygger på. Om ett fel uppstår medan RMS försöker konfigurera en resurs misslyckas etableringen och ett felmeddelande visas. Det här avsnittet tar upp de vanligaste orsakerna till sådana fel och ger dig hjälp med att felsöka oväntade situationer som förhindrar att RMS-etableringen slutförs.

Det går inte att etablera den första rotcertifikatservern
---------------------------------------------------------

Det kan hända att du inte kan etablera en rotcertifikatserver eftersom de korrekta etableringssidorna inte visas. Det här felet kan uppstå när du klickar på Etablera RMS på den här webbplatsen för att etablera den första rotcertifikatservern från sidan Global administration. I stället för etableringssidorna för en rotcertifikatserver visas etableringssidorna för en licensieringsserver.

Det här problemet uppstår när du inte tar bort etableringen av den sista rotcertifikatservern i den befintliga Active Directory-skogen innan du avinstallerar RMS, och du sedan försöker etablera en ny rotcertifikatserver. När den enda rotcertifikatservern i en Active Directory-skog tas bort, tas tjänstens anslutningspunkt bort från Active Directory. Om du inte tar bort etableringen av den sista rotcertifikatservern i skogen innan du avinstallerar RMS måste du ta bort tjänstens anslutningspunkt från Active Directory manuellt innan du kan etablera en rotcertifikatserver på nytt i den aktuella skogen.

Om etableringssidorna för en licensieringsserver visas när du försöker etablera den första rotcertifikatservern i en Active Directory-skog tar du bort tjänstens anslutningspunkt från Active Directory. Gör så här:

**Så här tar du bort RMS-tjänstens anslutningspunkt**
1.  Installera vid behov supportverktygen för Windows Server:

    För Windows Server 2003 kör du Suptools.msi som finns i mappen \\Support\\Tools på installations-CD:n.

    For Windows 2000 Server kör du Setup.exe som finns i mappen \\Support Tools på installations-CD:n.

2.  Logga in på domänkontrollanten i den domän som rotcertifikatservern tillhör med ett konto som är medlem i gruppen Domänadministratörer.

3.  Skriv in följande kommando på kommandoraden och tryck sedan på RETUR:

    **ldp**

4.  Klicka på **Anslutning** och klicka sedan på **Anslut**.

5.  Tryck på RETUR. Skriv inte in någon information.

6.  Klicka på **Anslutning** och klicka sedan på **Bind**.

7.  Tryck på RETUR. Skriv inte in någon information.

8.  Klicka på **Visa** och klicka sedan på **Träd**.

9.  Tryck på RETUR. Skriv inte in någon information.

    **dc=YourDomain,dc=com** visas i den vänstra fönsterrutan.

10. Expandera **dc=YourDomain,dc=com**.

11. Expandera **Konfiguration**.

12. Expandera **Tjänster**.

13. Ta bort **RightsManagementServices**.

eller

1.  Hämta och installera administrationsverktyget för RMS. Verktygslådan kan hämtas från [Microsofts webbplats](http://go.microsoft.com/fwlink/?linkid=33841).
2.  Öppna kommandotolken genom att klicka på **Start** och **Kör**. I dialogrutan **Kör** skriv **cmd** och klicka sedan på **OK**.
3.  Skriv följande kommando i kommandotolken:
    **ADSCPRegister.exeunregisterscp** &lt;*URLattAvregistrera*&gt;
4.  Byt ut &lt;*URLattAvregistrera*&gt; mot namnet på den URL som tillhör anslutningspunkten för RMS-tjänsten, t.ex. https://my\_domain/\_wmcs/Certification.

När du har utfört dessa steg kan du etablera rotcertifikatservern.

Det går inte att generera en SSPI-kontext
-----------------------------------------

Felmeddelandet ”Cannot generate SSPI context” kan visas under etableringen om RMS-tjänstkontot inte autentiserats vid registreringen av rotcertifikatservern hos Microsofts registreringstjänst.

Om det här felmeddelandet visas kontrollerar du att RMS-tjänstkontot är ett giltigt domänkonto. Om kontot är ett gruppkonto kontrollerar du att gruppmedlemskapet är aktuellt, att du kan matcha alla inkluderade konton i gruppen i domänen och att kontona har behörigheter till SQL-databaserna.
