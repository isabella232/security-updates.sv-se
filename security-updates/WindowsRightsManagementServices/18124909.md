---
TOCTitle: Så här importerar och använder du RMS Management Pack
Title: Så här importerar och använder du RMS Management Pack
ms:assetid: 'd9a73ef0-2f81-48c2-97cc-deb7bf477389'
ms:contentKeyID: 18124909
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747688(v=WS.10)'
---

Så här importerar och använder du RMS Management Pack
=====================================================

Importera och använda RMS Management Pack
-----------------------------------------

#### Så här importerar och använder du RMS Management Pack

1.  Kopiera RMS Management Pack (RMS\_MOMPack.akm) från mappen %ProgramFiles%\\Windows Rights Management Services\\Tools till MOM-servern (Microsoft Operations Manager).

2.  Öppna MOM-administratörskonsolen och importera sedan RMS Management Pack genom att följa instruktionerna nedan:

    1.  Expandera objektet **Rules** i trädet i MOM-administratörskonsolen och högerklicka sedan på objektet **Processing Rule Groups**.
    2.  Klicka på **Import Management Pack** på snabbmenyn. Dialogrutan **Import Management Pack** visas.
    3.  Klicka på **Browse** och välj sedan RMS\_MOMPack.akm.

3.  Ange om du vill sammanfoga (Merge) eller ersätta (Replace). Mer information om alternativ för sammanfogning och ersättning finns i Exporting and Importing Management Packs på Microsofts webbplats (http://www.microsoft.com/).

    Klicka på **Replace**. När du väljer att ersätta skriver det Management Pack som du importerar över befintliga grupper med bearbetningsregler. Inga användarkommentar bevaras. Om du vill sammanfoga ett Management Pack med ett befintligt Management Pack gör du det i en testmiljö och använder sedan alternativet **Replace** när du distribuerar det i produktionsmiljön.

4.  Klicka på **Import** när detta nya Management Pack ska importeras.

5.  Markera objektet **Configuration** i **MOM-administratörskonsolen** och klicka sedan på mappen **Agent Managers**.

6.  Högerklicka på namnet på den server dit du har importerat RMS Management Pack och välj sedan **Scan Managed Computers Now**.
