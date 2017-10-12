---
TOCTitle: 'Steg 4: Synkronisera servern'
Title: 'Steg 4: Synkronisera servern'
ms:assetid: 'a5514e46-a50b-46a6-9e5b-33c87c5b7cef'
ms:contentKeyID: 18153026
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc708523(v=WS.10)'
---

Steg 4: Synkronisera servern
============================

När du har konfigurerat nätverksanslutningen kan du få del av uppdateringar. Som standard är WSUS konfigurerat att hämta kritiska uppdateringar och säkerhetsuppdateringar för alla Microsoft-produkter. Du måste *synkronisera* WSUS-servern för att få del av uppdateringarna.

Vid synkronisering kontaktar WSUS-servern Microsoft Update. När kontakten är etablerad kontrollerar WSUS om det har kommit några nya uppdateringar sedan den senaste synkroniseringen genomfördes. Eftersom det här är första gången du synkroniserar WSUS-servern är alla uppdateringar tillgängliga och kan godkännas för installation.

| ![](images/Cc708523.note(WS.10).gif)Obs!                                                                                                                                                                                                                       |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| I det här dokumentet beskrivs synkronisering med hjälp av standardinställningarna. I WSUS finns även alternativ som du kan använda om du vill minimera bandbredden vid synkronisering. Mer information finns i vitboken “Deploying Microsoft Server Windows Update Services” (på engelska). |

**Så här synkroniserar du WSUS-servern**
1.  Klicka på **Alternativ** och därefter på **Synkroniseringsalternativ** i WSUS-konsolens verktygsfält.

2.  Klicka på **Synkronisera nu** under **Aktiviteter**.

När synkroniseringen har slutförts klickar du på **Uppdateringar** i WSUS-konsolens verktygsfält. Då visas en lista över uppdateringarna.
