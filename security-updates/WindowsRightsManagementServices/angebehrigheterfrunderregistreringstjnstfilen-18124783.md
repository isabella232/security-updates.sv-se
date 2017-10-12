---
TOCTitle: Ange behörigheter för underregistreringstjänstfilen
Title: Ange behörigheter för underregistreringstjänstfilen
ms:assetid: '737bb69b-fe26-4057-9569-e632f7bbf295'
ms:contentKeyID: 18124783
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747627(v=WS.10)'
---

Ange behörigheter för underregistreringstjänstfilen
===================================================

Underregistreringstjänsten körs på rotcertifikatservern och registrerar en licensieringsserver under etableringen. Som standard ger underregistreringstjänsten bara åtkomst till det lokala systemkonto som används på rotcertifikatservern. Om du vill etablera en licensieringsserver måste du logga in på licensieringsservern med det kontot. Alternativt kan en lokal administratör på rotcertifikatservern ändra underregistreringstjänstfilens (SubEnrollService.asmx) DACL-lista och bevilja åtkomst till det användarkonto som används vid etableringen av licensieringsservern. SubEnrollService.asmx finns i den virtuella certifikatkatalogen på rotcertifikatservern.
