---
TOCTitle: Ta servrar ur drift
Title: Ta servrar ur drift
ms:assetid: '52005e2e-9563-4ba0-906c-3cc76f9c378f'
ms:contentKeyID: 18124735
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747568(v=WS.10)'
---

Ta servrar ur drift
===================

Det kan finnas tillfällen när du behöver ta en RMS-server ur drift, t.ex. vid följande situationer:

-   Det uppstår problem med utrustningen eller vid uppgraderingar som gör att vissa servrar måste ersättas.
-   Det sker en minskning i licensierings- och publiceringstrafik som resulterar i att vissa servrar inaktiveras.
-   Juridiska krav gör att servrar måste tas bort från en viss plats, vilket i sin tur leder till att ett helt kluster måste tas ur drift.
-   Det sker en sammanslagning eller försäljning av avdelningar eller andra delar av en organisation där en del tillgångar tillfaller den nya ägaren.
-   Det sker en sammanslagning av två organisationer som båda kör RMS, vilket gör båda RMS-installationerna överproportionerade.

Innan du tar en server ur drift bör du säkerhetskopiera alla RMS-databaser som används på servern. Det gäller särskilt konfigurationsdatabasen. Mer information om hur du säkerhetskopierar databaser finns i ”Säkerhetskopiera och återställa systemet för RMS” i avsnittet ”Planera en RMS-distribution”. .

När du har säkerhetskopierat databaserna kan du ta servern ur drift. Vilka åtgärder som bör vidtas innan du tar en RMS-server ur drift beror på serverns roll och RMS-installationens topologi:

-   **Ta en server i ett kluster ur drift**. Om den RMS-server som du vill ta ur drift finns i ett kluster där andra RMS-servrar fortfarande är aktiva och behövs måste du ta bort etableringen av RMS och avinstallera det från den server som du vill ta ur drift. Därefter tar du bort servern från klustret och arkiverar databaserna.
    | ![](images/Cc747568.note(WS.10).gif)Obs!                                                                                   |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Du behöver bara ta bort etableringen av servrar i rotcertifikatklustret innan du avinstallerar RMS . Denna process krävs inte för licensieringsservrar. |

-   **Ta en fristående server ur drift**. Gör så här om den RMS-server du vill ta ur drift och ersätta med en ny är fristående (d.v.s. inte ingår i ett kluster med flera servrar): Ta bort etableringen av RMS, avinstallera den befintliga RMS-servern och ta sedan bort den från nätverket. Sedan installerar du och etablerar RMS på den nya servern på en gång. Konfigurera den nya RMS-servern till att använda samma URL och konfigurationsdatabas som den RMS-server du tog ur drift. Tänk på att användarna inte kan använda något innehåll som har publicerats med den gamla servern förrän den nya servern har installerats och etablerats.
    | ![](images/Cc747568.Important(WS.10).gif)Viktigt!                                                                                                                                                                                  |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Om den RMS-server som du ersätter har en HSM (Hardware Security Module) måste du överföra säkerhetsmiljön till den nya servern innan du installerar och etablerar RMS på servern. Instruktioner om hur du gör det finns i dokumentationen som medföljde HSM:en. |

-   **Ersätta en RMS-installation med en annan befintlig RMS-installation**. I vissa fall kan du behöva ta en RMS-installation ur drift och ersätta den med en annan befintlig RMS-installation, t.ex. vid en sammanslagning av två företag som båda använder RMS.

När du tar bort och avinstallerar en server tas den bort ur tabellen ClusterServer i konfigurationsdatabasen, och databasen för katalogtjänster tas bort från SQL Server. Instruktioner för hur du inaktiverar och avinstallerar RMS finns i ”[Så här tar du bort RMS](https://technet.microsoft.com/9fa63daa-5fb9-4afd-8371-b38248619857)” och ”[Så här avinstallerar du RMS](https://technet.microsoft.com/885e3b4f-ea32-466f-9f7f-d8440b0f7c28)” senare i det här avsnittet.
