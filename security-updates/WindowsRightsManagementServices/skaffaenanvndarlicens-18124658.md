---
TOCTitle: Skaffa en användarlicens
Title: Skaffa en användarlicens
ms:assetid: '0b6cde34-418a-4dee-9d27-b65b93b535ac'
ms:contentKeyID: 18124658
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720194(v=WS.10)'
---

Skaffa en användarlicens
========================

Användare måste hämta användarlicenser från RMS-licensieringstjänsten för att kunna använda RMS-skyddat innehåll. I följande illustration beskrivs hur det går till när användare begär och erhåller en användarlicens.

![](images/Cc720194.37b8d28c-9749-4e81-bc6a-22692fefb8b6(WS.10).gif "process för att förvärva en användarlicens")

Begäran om en användarlicens går till på följande sätt:

1.  Användaren tar emot en skyddad fil via en vanlig distributionskanal och öppnar den sedan med ett RMS-aktiverat program. Om användaren inte har något rättighetskontocertifikat på den aktuella datorn eller enheten måste han eller hon skaffa ett.
2.  Det RMS-aktiverade programmet skickar en begäran om en användarlicens till den server som utfärdat publiceringslicensen för det skyddade innehållet. Begäran innehåller användarens rättighetskontocertifikat (som innehåller användarens offentliga nyckel) och publiceringslicensen (som innehåller innehållets symmetriska nyckel).
    En publiceringslicens som utfärdas av ett klientlicensieringscertifikat innehåller URL:en för den server som utfärdat certifikatet. I detta fall skickas en begäran om en användarlicens till den server som utfärdat klientlicensieringscertifikatet och inte till den dator som utfärdat publiceringslicensen.
3.  Licensieringsservern validerar att användaren autentiserats, kontrollerar att denne är angiven i publiceringslicensen och skapar sedan en användarlicens. Servern validerar användarens kontocertifikat och kontrollerar sedan vilka rättigheter användaren har beviljats, antingen direkt eller som medlem av en grupp som beviljats rättigheter.
    Servern dekrypterar den symmetriska innehållsnyckeln med serverns privata nyckel, krypterar den på nytt med mottagarens offentliga nyckel och lägger till den i användarlicensen. På detta sätt säkerställs att endast den avsedda användaren kan dekryptera innehållsnyckeln och det skyddade innehållet.
    Eventuella relevanta villkor för användarlicensen, t.ex. exkludering av en program- eller Windows-version, läggs till på servern. De här villkoren tillämpas av klienten när användarlicensen binds till det RMS-skyddade innehållet.
4.  När valideringen är klar lämnar licensieringsservern ut användarlicensen till användarens klientdator.
