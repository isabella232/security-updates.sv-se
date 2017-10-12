---
TOCTitle: Lägga till servrar i en befintlig installation
Title: Lägga till servrar i en befintlig installation
ms:assetid: '7f3598ff-cd19-4daa-aa65-877f7f95a8ec'
ms:contentKeyID: 18124786
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747648(v=WS.10)'
---

Lägga till servrar i en befintlig installation
==============================================

Du kan lägga till fler servrar i RMS-installationen om det behövs för att möta ett ökat behov eller för att ersätta servrar som måste tas ur drift. Varje RMS-installation måste innehålla minst en rotcertifikatserver, men den kan även innehålla flera rotcertifikatservrar i ett kluster. Varje RMS-installation kan också innehålla enskilda licensieringsservrar eller kluster med licensieringsservrar.

Du kan lägga till servrar i en RMS-installation med någon av följande metoder:

-   Lägga till en eller flera RMS-servrar i ett rotcertifikatkluster.
-   Lägga till en ny fristående licensieringsserver.
-   Lägga till en eller flera RMS-servrar i ett licensieringskluster.

**Lägga till rotcertifikatservrar**

I de flesta fall är det lämpligast att lägga till en eller flera RMS-servrar i ett rotcertifikatkluster när du vill öka tillgängligheten och redundansen i distributionen. Ett rotcertifikatkluster består av en eller flera rotcertifikatservrar. Till skillnad från licensieringsservrar, som enbart tillhandahåller licensierings- och publiceringstjänster, tillhandahåller rotcertifikatservrar alla RMS-tjänster.

Under installationen och etableringen kan du välja att lägga till en server i ett kluster. När du gör det konfigureras den nya RMS-servern automatiskt som medlem av ett kluster. Stegvisa instruktioner för hur du installerar och etablerar en RMS-server som ska läggas till rotcertifikatklustret finns i”[Så här installerar du RMS med Service Pack 1](https://technet.microsoft.com/dab20175-a690-43f8-b943-768d289daa0d)” och ”[Så här lägger du till en server i ett kluster](https://technet.microsoft.com/db635238-5528-4bec-9cc6-8244e2b3d733)” senare i det här avsnittet.

Utöver etableringen måste du även konfigurera program- och maskinvara för att hantera kluster och belastningsutjämning första gången du skapar ett kluster, om detta är aktuellt. Om du redan har implementerat ett kluster måste du först konfigurera program- eller maskinvarubaserad belastningsutjämning så att dessa tjänster fungerar med den nya medlemmen i klustret.

**Lägga till licensieringsservrar**

Till skillnad från rotcertifikatservrar, som tillhandahåller alla RMS-tjänster, tillhandahåller licensieringsservrar enbart licensierings- och publiceringstjänster.

Licensieringsservrar är inte obligatoriska och används normalt till att lösa specifika licensieringskrav, exempelvis för:

-   Hantering av specifika RM-krav inom vissa avdelningar. Exempelvis kan en viss grupp i organisationen ha säkerhetskrav som skiljer sig från resten av organisationen, och den gruppen kan därför vilja ha fullständig kontroll över implementeringen av licensiering i den aktuella gruppen. Eftersom en skog endast kan innehålla en rotcertifikatserver är det inte alltid lämpligt att konfigurera en separat rotcertifikatserver. I stället kan du välja att konfigurera en separat licensieringsserver eller ett licensieringskluster som enbart används för den aktuella gruppen. Du kan sedan konfigurera rättighetsprinciper som enbart gäller för den aktuella licensieringsservern eller det aktuella licensieringsklustret.
-   Hantering av rättigheter för externa affärspartner som en del av ett extranät, där det krävs en fullständig delning och spårning av resurser för olika affärspartner. Mer information finns i ”[Konfigurera en extranät-URL](https://technet.microsoft.com/88fec9ff-c96c-4d20-8856-0485e7507572)” senare i det här avsnittet.
-   Belastningsutjämning av licensieringsuppgifter från rotcertifikatservern. Det här kan ge prestandafördelar i organisationer där enbart en enskild rotcertifikatserver används (i de fall inget rotcertifikatkluster används).

I de flesta fall bör du lägga till RMS-servrar i rotcertifikatklustret så att du kan konfigurera redundans och belastningsutjämning mellan alla servrar i distributionen. Även om licensieringsservrar också kan användas för avlastning vid bearbetning av licensierings- och publiceringsbegäran kan de inte belastningsutjämnas med rotcertifikatklustret. Om det inte finns något specifikt behov av att distribuera separata licensieringsservrar är det bättre att belastningsutjämna alla RMS-servrar genom att göra dem till medlemmar av rotcertifikatklustret.

Stegvisa instruktioner om hur du installerar och etablerar en RMS-licensieringsserver finns i ”[Så här installerar du RMS med Service Pack 1](https://technet.microsoft.com/dab20175-a690-43f8-b943-768d289daa0d)” och ”[Så här etablerar du en licensieringsserver](https://technet.microsoft.com/4d67b898-0ba9-4eef-ab7d-ee0ca55a688e)” senare i det här avsnittet.
