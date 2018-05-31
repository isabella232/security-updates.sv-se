---
TOCTitle: 'Skapa RMS-tjänstkontot'
Title: 'Skapa RMS-tjänstkontot'
ms:assetid: '6eb38729-f0f0-431a-bc8c-17102cf175d8'
ms:contentKeyID: 18124762
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747546(v=WS.10)'
---

Skapa RMS-tjänstkontot
======================

Under installationen av RMS skapas en säkerhetsgrupp som kallas **RMS-tjänstgrupp** på den lokala datorn, som beviljas rättigheter för alla resurser som krävs för att RMS ska fungera.

När du etablerar RMS på en server anger du ett användarkonto som ska användas som RMS-tjänstkonto. Det konto som du anger blir medlem av RMS-tjänstgruppen och beviljas därmed de behörigheter som omfattar den gruppen. Under normal drift körs RMS i de flesta fall under RMS-tjänstkontot.

| ![](images/Cc747546.note(WS.10).gif)Obs!                   |
|-----------------------------------------------------------------------------------------|
| RMS-tjänstkontot kan inte vara samma domänkonto som användes vid installationen av RMS. |

Av säkerhetsskäl bör du skapa ett specifikt användarkonto som används som tjänstkonto för RMS. Använd inte det kontot i något annat syfte. Dessutom bör du inte bevilja det kontot några ytterligare behörigheter.

| ![](images/Cc747546.Important(WS.10).gif)Viktigt!        |
|---------------------------------------------------------------------------------------|
| Det här speciella användarkontot måste skapas innan du installerar och etablerar RMS. |

Mer information om de behörigheter som beviljas RMS-tjänstgruppen och de konton RMS körs under finns i ”RMS säkerhetsmodell” i ”Tekniska referenser för RMS”.
