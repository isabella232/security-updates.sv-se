---
TOCTitle: 'RMS-servernycklar'
Title: 'RMS-servernycklar'
ms:assetid: '5f4100a1-9aa5-42af-85c8-4bc691022f06'
ms:contentKeyID: 18124744
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720280(v=WS.10)'
---

RMS-servernycklar
=================

Varje RMS-server har ett nyckelpar som består av två 1024-bitars RSA-nycklar.

Serverns offentliga nyckel används till att kryptera innehållsnyckeln i en publiceringslicens. På så sätt kan innehållsnyckeln endast hämtas från RMS-servern, där användarlicenser utfärdas mot publiceringslicensen. Serverlicensieringscertifikatet innehåller serverns offentliga nyckel.

Serverns privata nyckel används för att signera alla certifikat och licenser som utfärdas av servern.

Skydd av serverns privata nyckel
--------------------------------

Som standard skapas och sparas serverns privata nyckel i RMS-databasen i krypterad form vid etableringen. Alternativt kan du under etableringen ange en CSP (cryptographic service provider) som redan är installerad på servern.

Du kan använda CSP på två olika sätt:

-   Välj bland CSP-program som ingår i standardinstallationen på servern.
    eller
-   Använd CSP-program från tredjepartsleverantörer som du installerat på servern.

| ![](images/Cc720280.note(WS.10).gif)Obs!                                  |
|--------------------------------------------------------------------------------------------------------|
| Om du vill använda en HSM (Hardware Security Module) måste du välja ett CSP-program som stödjer denna. |

Om du väljer att skydda serverns privata nyckel med hjälp av ett CSP-program sparas namnet på providern och namnet på den nyckelbehållare som finns i konfigurationsdatabasen.
