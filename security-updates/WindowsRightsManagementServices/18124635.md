---
TOCTitle: Programvarukrav för RMS
Title: Programvarukrav för RMS
ms:assetid: '17faf2ad-2366-4a92-98a5-766e20a0f741'
ms:contentKeyID: 18124635
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc720201(v=WS.10)'
---

Programvarukrav för RMS
=======================

Programvarukraven för körning av RMS-servrar visas i följande tabell.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Programvara</th>
<th style="border:1px solid black;" >Krav</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Operativsystem</td>
<td style="border:1px solid black;">Alla utgåvor av Microsoft Windows Server® 2003, utom Web Edition.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Filsystem</td>
<td style="border:1px solid black;">Filsystemet NTFS rekommenderas.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Operativsystemkomponenter</td>
<td style="border:1px solid black;"><ul>
<li>Message Queuing (även kallat MSMQ) med Active Directory®-integration av katalogtjänster aktiverat.<br />
<br />
</li>
<li>Internet Information Services (IIS) med ASP.NET aktiverat.<br />
<br />
</li>
<li>Microsoft .NET Framework 1.1<br />
<br />
</li>
</ul></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Active Directory®-katalogtjänster</td>
<td style="border:1px solid black;">RMS måste installeras inom en Active Directory-domän där domänkontrollanterna körs med Windows Server 2000 med Service Pack 3 (SP3) eller senare. Alla användare och grupper som använder och publicerar innehåll med RMS måste ha en e-postadress som är konfigurerad i Active Directory.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Databasserver</td>
<td style="border:1px solid black;">RMS behöver en databas och lagrade procedurer för att utföra åtgärder. Du kan använda Microsoft SQL Server 2000 med SP3a eller senare, eller Microsoft SQL Server 2005. Vid testning eller andra distributioner till enskilda datorer kan du använda Microsoft SQL Server Desktop Engine (MSDE 2000) med SP3 eller Microsoft SQL Server 2005 Express Edition.</td>
</tr>
</tbody>
</table>
  
Om du distribuerar RMS i en miljö där det finns flera Active Directory-skogar måste du använda universella grupper för Active Directory så att gruppmedlemskap replikeras till alla globala kataloger. För att du ska kunna skapa universella grupper måste domänens funktionalitetsnivå ha angetts till minst enhetligt läge i Windows 2000 och funktionalitetsnivån för skog ska höjas till Windows Server 2003.
  
Vi rekommenderar att MSDE 2000 eller Microsoft SQL Server 2005 Express Edition enbart används för hantering av RMS-databaser i testmiljö, eftersom MSDE 2000 och Microsoft SQL Server 2005 Express Edition inte har funktioner för nätverksgränssnitt. Dessutom anger villkoren för användning av MSDE 2000 och Microsoft SQL Server 2005 Express Edition att du inte får använda SQL Server-klientverktygen till att ändra en MSDE 2000- eller Microsoft SQL Server 2005 Express Edition-databas. Den här begränsningen gör att det inte går att visa loggningsinformation och att ändra data som lagras i konfigurationsdatabasen.
  
Om du inte har ASP.NET version 1.1 installerad på servern varierar installationsprocessen beroende på om du kör 32-bitarsversionen eller 64-bitarsversionen av Windows Server 2003.
  
Om du kör 32-bitarsversionen av Windows Server 2003 följer du stegen nedan för att installera och aktivera ASP.NET version 1.1:
  
1.  Öppna **Lägg till eller ta bort program** på **Kontrollpanelen** och klicka sedan på **Lägg till/ta bort Windows-komponenter**.  
2.  Klicka på **Programserver** och sedan på **Information**.  
3.  I guiden Windows-komponenter väljer du **ASP.NET**.  
4.  Om ASP.NET 1.1 är installerat men inte tillåtet som ett IIS-webbtjänsttillägg:  
    -   Öppna Internet Information Services Manager.  
    -   Klicka på **IIS-webbtjänsttillägg,** välj ASP.NET v1.1.4322 och klicka sedan på **Tillåt**.
  
Om du kör 64-bitarsversionen av Windows Server 2003 följer du stegen nedan för att installera och aktivera ASP.NET version 1.1:
  
1.  Installera .NET Framework 1.1 så installeras ASP.NET 1.1. Du kan hämta Microsoft .NET Framework Version 1.1 Redistributable Package från Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkID=69985](http://go.microsoft.com/fwlink/?linkid=69985)).  
2.  Öppna Internet Information Services Manager.  
3.  Klicka på IIS-webbtjänsttillägg, välj ASP.NET v1.1.4322 och klicka sedan på Tillåt.
  
Om du kör RMS på en 64-bitarsversion av Windows Server 2003 måste du använda följande steg när du aktiverar IIS så att det fungerar med RMS:
  
1.  Klicka på **Start** och sedan på **Kör**.  
2.  I **Öppna** anger du följande kommando och trycker sedan på RETUR:
  
**"cscript %SystemDrive%\\inetpub\\AdminScripts\\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 1"**
  
RMS är inte utvecklat för .NET Framework version 2.0. Även om en sida vid sida-installation kan göras måste du se till att ASP.NET konfigureras för användning av ASP.NET v1.1.4322. Du kan se till att en sida vid sida-installation fungerar på två sätt:
  
-   Installera .NET Framework version 2.0 innan du installerar RMS-servern.  
-   Återställ ASP.NET-versionen till version 1.1.4322 på standardwebbplatsen i IIS genom att köra följande kommando:
  
**"%SystemRoot%\\Microsoft.NET\\Framework\\v1.1.4322\\aspnet\_regiis -s w3svc/1/root"**
  
Mer information om Active Directory, Message Queuing och IIS finns i Hjälp- och supportcenter i Windows Server 2003.
  
| ![](images/Cc720201.Caution(WS.10).gif)Varning!                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| RMS kan etableras på standardwebbplatsen eller på någon annan webbplats som du har definierat tidigare i IIS. Av säkerhetsskäl bör du inte köra några ytterligare webbplatser eller webbtjänster på den aktuella servern. Om du gör det kan det leda till att flera program och tjänster körs under samma konto som RMS (det gäller särskilt det lokala systemkontot), vilket kan kompromettera säkerheten för de privata nycklarna. Etablera inte RMS-servern på samma webbplats som Microsoft Office SharePoint Server 2007. Det går inte att använda RMS med Kerberos-autentisering. När RMS-serven etableras på en webbplats inaktiveras Kerberos-autentisering för den aktuella servern. Om RMS inte konfigureras för användning av ASP.NET v1.1.4322 loggas ingen information i loggningsdatabasen och förlust av data uppstår. |
  
Se även  
-------
  
####  
  
[Planera databasserver-infrastrukturen](https://technet.microsoft.com/b12354bd-3143-4d1f-b5aa-450c4550653c)
