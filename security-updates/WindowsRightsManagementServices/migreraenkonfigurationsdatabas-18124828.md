---
TOCTitle: Migrera en konfigurationsdatabas
Title: Migrera en konfigurationsdatabas
ms:assetid: '980e3e94-7d28-40dd-ad01-d34eb3c8d8e6'
ms:contentKeyID: 18124828
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747607(v=WS.10)'
---

Migrera en konfigurationsdatabas
================================

Det finns lägen då en databasserver måste återkallas. Det gäller exempelvis vid maskinvaruuppgradering av en RMS-databasserver. Innan du kan återkalla databasservern måste du flytta konfigurationsdatabasen till en annan databasserver. För att skydda data i konfigurationsdatabasen, däribland de nyckelpar som finns där, bör du planera och genomföra migreringen noga.

Du rekommenderas att skapa ett CNAME-alias för RMS-databasservern och sedan konfigurera RMS så att aliaset tillämpas. På så sätt slipper du ändra databasserverns namn manuellt i RMS-konfigurationsdatabasen om servernamnet skulle ändras. När du använder ett CNAME-alias behöver du endast uppdatera aliasposten.

Innan du inleder migreringen av konfigurationsdatabasen bör du kontrollera att du har tillgång till följande information:

-   Det kontonamn och lösenord som användes för att etablera servrarna i det RMS-kluster som använder databasen.
-   Det lösenord till den privata RMS-nyckeln som angavs vid etableringen (om en programbaserad CSP (Cryptographic Service Provider) används för att lagra den privata RMS-nyckeln). Om du använder en HSM (Hardware Security Module) för att lagra den privata RMS-nyckeln kan du hoppa över det här steget.

| ![](images/Cc747607.note(WS.10).gif)Obs!                                                                                                                                     |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| När du migrerar konfigurationsdatabasen krävs inget nytt serverlicensieringscertifikat eller ny privat servernyckel, eftersom inställningarna från den ursprungliga konfigurationsdatabasen sparas i RMS. |

Du bör säkerhetskopiera RMS-databaserna innan du utför någon åtgärd på databasservern. Om du inte har möjlighet att säkerhetskopiera bör du i alla fall exportera serverlicensieringscertifikatet. Mer information om hur du gör det finns i avsnittet om hur du [Så här exporterar du ett serverlicensieringscertifikat till en fil](https://technet.microsoft.com/d683a629-71b3-4b11-932b-4ab0317334af). Om ett fel inträffar när du migrerar databaserna kan du importera serverlicensieringscertifikatet till en ny RMS-installation och använda innehåll som tidigare var rättighetsskyddat.

Så här migrerar du en konfigurationsdatabas:

-   Uppdatera RMS-konfigurationsdatabasen med namnet på den nya databasservern.
-   Uppdatera web.config-filer och register på samtliga servrar i RMS-klustret med det nya databasservernamnet

| ![](images/Cc747607.Important(WS.10).gif)Viktigt!                                                                             |
|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| För att du ska kunna följa de här anvisningarna krävs att du redan har kopierat RMS-databaserna till den nya databasserver som innehåller RMS-databaserna. |

Uppdatera RMS-konfigurationsdatabasen med det nya databasservernamnet
---------------------------------------------------------------------

Namnet på den databasserver som innehåller RMS-databaserna lagras i RMS-konfigurationsdatabasen. När du har migrerat databasfilerna till den nya databasservern måste du uppdatera RMS-konfigurationsdatabasen. Det gör du antingen med hjälp av RMS-konfigurationsredigeraren i RMS Administration Toolkit eller med hjälp av SQL Management Studio.

Så här uppdaterar du namnet på RMS-databasservern med hjälp av konfigurationsredigeraren för RMS:

**Så här uppdaterar du RMS-konfigurationsdatabasen med hjälp av konfigurationsredigeraren för RMS**
1.  Logga in på en RMS-server i klustret som medlem i databasrollen för systemadministratörer.

2.  Installera RMS Administration Toolkit från Microsoft Download Center ([http://go.microsoft.com/fwlink/?LinkId=98961](http://go.microsoft.com/fwlink/?linkid=98961)).

3.  Gå till %SystemDrive%:\\Program Files\\RMS SP2 Administration Toolkit\\RMSConfigEditor och dubbelklicka på **RMSCONFIGEDITOR.EXE**.

4.  I rutan **Server** skriver du in namnet på den nya server som innehåller RMS-konfigurationsdatabasen och klickar sedan på **Go**.

5.  I rutan **Database** klickar du på **DRMS\_Config\_***&lt;RMS-klusternamn&gt;***\_***&lt;Port&gt;*, där *&lt;RMS-klusternamn&gt;* är namnet på RMS-klustret och *&lt;Port&gt;* är den TCP-port där RMS kommunicerar. Klicka sedan på **Go**.

6.  Klicka på **DRMS\_ClusterPolicies**.

7.  Ändra värdet i kolumnen **PolicyData** på raden **LoggingDatabaseServer** i resultatfönstret och infoga det nya namnet på RMS-databasservern.

8.  Klicka på **Persist**.

9.  Ändra värdet i kolumnen **PolicyData** på raden **CertificationUserKeyStorageConnectionString** så att det motsvarar den nya databasservern. Värdet ska vara **data source=***&lt;nytt databasservernamn&gt;***;integrated** där *&lt;nytt databasservernamn&gt;* är namnet på den nya databasservern.

10. Klicka på **Persist**.

11. Upprepa steg 9–10 för värdet i kolumnen **PolicyData** på raden **DirectoryServicesCacheDatabase**.

12. Klicka på **DRMS\_PluginProperties** i vänster fönsterruta.

13. För **PropertyID** 101, med namnet **PERSISTENT\_STORAGE**, ändrar du värdet i kolumnen **PropertyValue** så att det motsvarar den nya databasservern. Värdet ska vara **data source=***&lt;nytt databasservernamn&gt;***;integrated** där *&lt;nytt databasservernamn&gt;* är namnet på den nya databasservern.

14. Klicka på **Persist**.

15. Stäng konfigurationsredigeraren för RMS.

Så här uppdaterar du RMS-konfigurationsdatabasen med hjälp av SQL Server Management Studio:

**Så här uppdaterar du RMS-konfigurationsdatabasen med hjälp av SQL Server Management Studio**
1.  Logga in på RMS-konfigurationsdatabasservern som lokal administratör eller med något annat användarkonto som ingår i den lokala administratörsgruppen.

2.  Klicka på **Start** och peka på **All Programs**. Peka på **Microsoft SQL Server 2005** och klicka på **SQL Server Management Studio**.

3.  På sidan **Connect to Server** kontrollerar du att namnet på den nya databasservern finns med i rutan **Server name**. Klicka sedan på **Connect**.

4.  Expandera **Databases**, expandera **DRMS\_Config\_***&lt;RMS-klusternamn&gt;***\_***&lt;Port&gt;* och expandera sedan **Tables**.

5.  Högerklicka på **DRMS\_ClusterPolicies** och klicka sedan på **Open Table**.

6.  Ändra värdet i kolumnen **PolicyData** på raden **LoggingDatabaseServer** i resultatfönstret och infoga det nya namnet på RMS-databasservern.

7.  Ändra värdet i kolumnen **PolicyData** på raden **CertificationUserKeyStorageConnectionString** så att det motsvarar den nya databasservern. Värdet ska vara **data source=***&lt;nytt databasservernamn&gt;***;integrated** där *&lt;nytt databasservernamn&gt;* är namnet på den nya databasservern.

8.  Upprepa steg 6–7 för värdet i kolumnen **PolicyData** på raden **DirectoryServicesCacheDatabase**.

9.  Högerklicka på **DRMS\_PluginProperties** och klicka sedan på **Open Table**.

10. För **PropertyID** 101, med namnet **PERSISTENT\_STORAGE**, ändrar du värdet i kolumnen **PropertyValue** så att det motsvarar den nya databasservern. Värdet ska vara **data source=***&lt;nytt databasservernamn&gt;***;integrated** där *&lt;nytt databasservernamn&gt;* är namnet på den nya databasservern.

11. Stäng Microsoft SQL Server Management Studio.

Konfigurera varje server i RMS-klustret innan du använder det nya databasservernamnet
-------------------------------------------------------------------------------------

För att kunna konfigurera servrarna i RMS-klustret och använda det nya databasservernamnet måste du uppdatera web.config-filerna och uppdatera tre registerposter. När du har gjort det aktiverar du ändringarna genom att starta om IIS (Internet Information Services).

Så här uppdaterar du web.config-filerna på servrarna i RMS-klustret:

**Så här uppdaterar du web.config-filerna på servrarna i RMS-klustret**
1.  Logga in på en server i RMS-klustret som medlem i den lokala administratörsgruppen.

2.  Gå till %Systemdrive%\\inetpub\\wwwroot\\\_wmcs\\admin.

3.  Dubbelklicka på **web.config**, välj alternativet **Select the program from a list** och klicka på **OK**.

4.  Klicka på **Notepad**, avmarkera **Always use the selected program to open this kind of file** och klicka på **OK**.

5.  Klicka på **Edit** och sedan på **Replace**.

6.  I rutan **Find what** skriver du in namnet på den databasserver som ska återkallas och som innehåller RMS-databaserna.

7.  I rutan **Replace with** skriver du in namnet på den nya databasservern som innehåller RMS-databaserna.

8.  Klicka på **Replace All** och sedan på **Cancel**.

9.  Klicka på **File** och sedan på **Save**.

10. Stäng Anteckningar.

11. Upprepa steg 2–9 för web.config-filerna i katalogerna %Systemdrive%\\inetpub\\wwwroot\\\_wmcs\\certification och %Systemdrive%\\inetpub\\wwwroot\\\_wmcs\\licensing.

12. Upprepa steg 1–11 för samtliga servrar i RMS-klustret.

Uppdatera slutligen registret på samtliga servrar i RMS-klustret med det nya databasservernamnet:

| ![](images/Cc747607.Caution(WS.10).gif)Varning!                                                                          |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| Felaktig redigering av registret kan skada systemet allvarligt. Säkerhetskopiera alla viktiga data på datorn innan du ändrar registerinställningarna. |

**Så här uppdaterar du registret på servrarna i RMS-klustret**
1.  Logga in på en server i RMS-klustret som medlem i den lokala administratörsgruppen.

2.  Klicka på **Start** och sedan på **Kör**.

3.  Skriv **regedit.exe** och klicka på **OK**.

4.  Gå till **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\DRMS\\1.0\\KeyProtection**.

5.  Ändra namnet på registerposten PASSWORDDERIVEDKEY\_*&lt;gammalt databasservernamn&gt;*\_DRMS\_CONFIG\_*&lt;RMS-klusternamn&gt;*\_*&lt;port&gt;* till:

    PASSWORDDERIVEDKEY\_*&lt;gammalt databasservernamn&gt;*\_DRMS\_CONFIG\_*&lt;RMS-klusternamn&gt;*\_*&lt;port&gt;*

    där:

    -   *&lt;nytt databasservernamn&gt;* är namnet på den gamla databasservern.
    -   *&lt;RMS-klusternamn&gt;* är namnet på RMS-klustret.
    -   *&lt;port&gt;* är den TCP-port som används för RMS-kommunikation.
    -   *&lt;nytt databasservernamn&gt;* är namnet på den nya databasservern.

6.  Gå till **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet001\\Services\\DRMS\_Logging\_&lt;RMS cluster name&gt;\_&lt;port&gt;\\Params**.

7.  Ändra registerposten **ConnectionString** så att datakällan överensstämmer med namnet på den nya databasservern.

8.  Upprepa steg 6–7 för **HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\DRMS\_Logging\_&lt;RMS cluster name&gt;\_&lt;port&gt;\\Params**.

9.  Skriv **IISRESET** i kommandotolken och tryck på RETUR.

10. Upprepa steg 1–9 för samtliga servrar i RMS-klustret.
