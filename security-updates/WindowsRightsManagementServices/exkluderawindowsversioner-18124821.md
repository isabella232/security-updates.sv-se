---
TOCTitle: 'Exkludera Windows-versioner'
Title: 'Exkludera Windows-versioner'
ms:assetid: '8b8a184d-ac0e-4a43-822c-d2fae2faf484'
ms:contentKeyID: 18124821
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747590(v=WS.10)'
---

Exkludera Windows-versioner
===========================

Klienten med Microsoft® Windows® RMS (Rights Management Services) 1.0 kan användas på datorer med Microsoft Windows 98 Second Edition eller Windows Millennium Edition. De operativsystemen har dock inte funktioner för NTLM-verifiering. Av den anledningen kan det vara bra att hindra användare från att använda rättighetsskyddat innehåll från datorer med ett av dessa operativsystem, och att öka skyddet av innehållet genom att begära att användarna använder en senare Windows-version än Windows Millennium Edition.

När du anger en exkluderingsprincip som exkluderar användare baserat på Windows-version, placeras ett villkor i alla användarlicenser som förhindrar att de används på klientdatorer där Windows 98 Second Edition eller Windows Millennium Edition körs. Du måste aktivera exkludering av Windows-version på sidan **Exkluderingsprinciper** på administrationswebbplatsen för varje kluster där funktionen ska användas.
