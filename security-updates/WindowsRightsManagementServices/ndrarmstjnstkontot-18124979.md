---
TOCTitle: 'Ändra RMS-tjänstkontot'
Title: 'Ändra RMS-tjänstkontot'
ms:assetid: 'f257d66d-b823-41e4-bcb7-7c90eb295238'
ms:contentKeyID: 18124979
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747736(v=WS.10)'
---

Ändra RMS-tjänstkontot
======================

Under installationen av RMS skapas RMS-tjänstgruppen på den lokala datorn och gruppen beviljas lämpliga behörigheter till alla resurser som krävs för att RMS ska fungera. Under etableringen av RMS på en server måste du ange ett domänkonto när du definierar RMS-tjänstkontot. RMS-tjänstkontot kan inte vara samma domänkonto som det du använde vid installationen av RMS. Det konto som du anger blir medlem av RMS-tjänstgruppen och beviljas de behörigheter som omfattar denna grupp. Vid rutindrift körs RMS med RMS-tjänstkontot.

Du kan när som helst ändra RMS-tjänstkonto. När du gör det tas det konto som tidigare användes bort automatiskt från RMS-tjänstgruppen och det nya kontot blir medlem i stället.

| ![](images/Cc747736.Important(WS.10).gif)Viktigt!                                                                                                                                                                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Av säkerhetsskäl bör du skapa ett specifikt användarkonto som används som RMS-tjänstkonto. Använd enbart detta konto som RMS-tjänstkonto. Använd det inte i något annat syfte. Dessutom bör du inte bevilja detta konto några ytterligare behörigheter. |

| ![](images/Cc747736.note(WS.10).gif)Obs!                                      |
|------------------------------------------------------------------------------------------------------------|
| RMS-tjänstkontot kan inte vara samma domänkonto som användes vid installationen av RMS med Service Pack 1. |
