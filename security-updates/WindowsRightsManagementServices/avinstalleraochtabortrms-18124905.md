---
TOCTitle: Avinstallera och ta bort RMS
Title: Avinstallera och ta bort RMS
ms:assetid: 'cae1ed5b-f716-41f0-8e14-7cbfef405331'
ms:contentKeyID: 18124905
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747753(v=WS.10)'
---

Avinstallera och ta bort RMS
============================

I olika situationer kan du behöva ta bort RMS från en server. För en rotcertifikatserver är det första steget att ta bort RMS från servern. Det gör du genom att klicka på **Ta bort RMS från den här webbplatsen** på sidan **Global administration** för den server som du vill ta bort. Du behöver inte ta bort en licensieringsserver innan du avinstallerar RMS.

| ![](images/Cc747753.note(WS.10).gif)Obs!                                                                                                                                                                                                                                                                    |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| När den sista rotcertifikatservern i en Active Directory-skog tas bort tas tjänstens anslutningspunkt bort från Active Directory. Om du inte tar bort servern innan du avinstallerar RMS går det inte att etablera någon ny rotcertifikatserver i skogen förrän du manuellt tagit bort tjänstens anslutningspunkt från Active Directory. |

Därefter avinstallerar du RMS.

När du tar bort och avinstallerar RMS från en fristående server eller från den sista servern i ett kluster tas även katalogtjänstdatabasen bort. Konfigurations- och loggningsdatabaser tas inte bort. Men om du uppgraderar eller installerar om RMS på servern skrivs loggningsdatabasen över av en ny loggningsdatabas.

När du tar bort och avinstallerar RMS från en server i ett kluster tas inte klustrets konfigurations-, loggnings- och katalogtjänstdatabaser bort. Men konfigurationsdatabastabellen DRMS\_ClusterServer uppdateras så att det syns att servern har tagits bort ur klustret.

Mer information om hur du tar servrar ur drift och om de problem som kan uppstå när du gör det finns i ”[Ta servrar ur drift](https://technet.microsoft.com/52005e2e-9563-4ba0-906c-3cc76f9c378f)” tidigare i det här avsnittet.
