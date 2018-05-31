---
TOCTitle: Övervakning med Microsoft Operations Manager
Title: Övervakning med Microsoft Operations Manager
ms:assetid: 'ce372598-7421-4f1f-b8eb-f62da26e85d1'
ms:contentKeyID: 18124900
ms:mtpsurl: 'https://technet.microsoft.com/sv-se/library/Cc747758(v=WS.10)'
---

Övervakning med Microsoft Operations Manager
============================================

I RMS finns ett Management Pack som du kan använda med Microsoft® Operations Manager (MOM). Med MOM övervakar du driften av organisationens servrar genom att:

-   Övervaka händelser som loggas av RMS i programhändelseloggen.
-   Markera händelser som kan tyda på att tjänster inte längre används och konfigurationsproblem, så att du snabbt och enkelt kan åtgärda och förebygga problem.
-   Få aviseringar om varningar och fel, t.ex. om att serverlicensieringscertifikatet snart upphör att gälla eller att det har uppstått ett webbtjänstfel.

RMS Management Pack (RMS\_MOMPack.akm) installeras med RMS i mappen %program%\\Windows Rights Management Services\\Tools.

I detta Management Pack finns nedanstående regeluppsättningar, som RMS-administratören kan använda till att hantera distributionen av RMS-servrar.

**RMS MOM Management Pack Rules**

1.  PMC Measure - Activation Proxy total failures
2.  PMC Measure - Activation Proxy Total time
3.  PMC Measure - Activation Total Processing Time
4.  PMC Measure - Activation Total Reqs
5.  PMC Measure - ActivationProxy total reqs
6.  PMC Measure - AD cache (DB cache) hits
7.  PMC Measure - AD cache (DB cache) misses
8.  PMC Measure - Average License Processing time
9.  Event - Configuration Info corruption
10. PMC Measure - Dead GC connections
11. PMC Measure - Enroll failures
12. Event - General Error
13. Event - Init Failure
14. Event - Licensor Cert has expired
15. Event - Licensor Cert Request Failure
16. Event - Logging service failure
17. PMC Measure - Max GC connections available
18. Event - Missing License Acq Point generation plugin
19. PMC Measure - MSMQ Queue length on all RM servers
20. Event - No GCs available
21. Event - Plugin Init Failure
22. Event - PrivateKey protection password changed
23. Event - RM Server Shut Down
24. Event - RM Server ShutDown Failure
25. Event - Server Startup Failure
26. PMC Measure - SubEnroll failures
27. Event - SuperUser privileged override power was invoked
28. PMC Threshold - Too Many GetLicensorCert failures
29. Event - Upcoming Licensor Cert Expiry - 1 Month
30. Event - Upcoming Licensor Cert expiry - 1 Week

Mer information om hur du distribuerar MOM Management Packs i organisationen finns på [Microsofts webbplats](http://www.microsoft.com/) (http://www.microsoft.com/).
