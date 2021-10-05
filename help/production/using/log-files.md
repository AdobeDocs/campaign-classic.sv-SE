---
product: campaign
title: Loggfiler
description: Loggfiler
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---

# Loggfiler{#log-files}

![](../../assets/v7-only.svg)

Loggfilerna är ordnade enligt följande:

![](assets/d_ncs_directory.png)

Varje **nlserver**-modul genererar en loggfil som har sparats i följande katalog: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

Modulen **nlserver syslogd** sparar loggarna på disken. Den här modulen liknar Unix **syslog daemon**, men har anpassats för kompatibilitet mellan Unix och Windows. De andra Adobe Campaign-modulerna sparar inte sina loggar på disken. de delegerar den här aktiviteten till modulen **syslogd** genom att skicka UDP-paket.

Som standard har Adobe Campaign-plattformen **syslogd**-modulen installerad, men det går att använda en annan **syslog-daemon**. Den här modulen skapar loggfilerna i katalogen **log**.

Loggarna för moduler med flera instanser lagras i följande katalog: **`<installation directory>`/var/default/log/**. Samma loggfil delas av alla instanser (t.ex. **web.log**).

Loggarna för de andra modulerna lagras i en undermapp som heter efter instansen. Varje instans har sina egna loggfiler.

Loggfiler med flera instanser visas i följande tabell:

| Fil | Beskrivning |
|---|---|
| web.log | Loggar för webbmodulen (klientkonsol, rapporter, SOAP API osv.) |
| webmdl.log | Loggar från omdirigeringsmodulen |
| watchdog.log | Loggar från Adobe Campaign processövervakningsmodul |
| trackinglogd.log | Spårningsloggar |

Loggfilerna för en instans visas i följande tabell:

| Fil | Beskrivning |
|---|---|
| mta.log | loggar för mta-modulen |
| mtachild.log | Bearbetningsloggar för meddelandeleverans |
| wfserver.log | Loggar för arbetsflödesservermodulen |
| runwf.log | Körningsloggar för arbetsflöde |
| inMail.log | Logg för studsande e-postmodul |
| logins.log | Loggar alla inloggningsförsök till Adobe Campaign (vare sig de lyckas eller inte) |

>[!IMPORTANT]
>
>Katalogen **redir** finns bara på omdirigeringsservrar. Underkatalogen **url** innehåller matchningar för de URL:er som ska omdirigeras, och underkatalogen **log** innehåller spårningsloggarna. Om du vill generera spårningsloggar måste modulen **trackinglogd** köras.

För optimering av prestanda och lagring delas filen logins.log upp i flera filer, en varje dag (logins.yy-mm-dd.log) med högst 365 filer. Antalet dagar kan ändras i serverConf.xml under syslogd (**maxNumberOfLoginsFiles** option). Se dokumentationen för [serverkonfigurationsfilen](../../installation/using/the-server-configuration-file.md#syslogd).

Som standard är loggarna begränsade till två 10 MB-filer per modul och per instans. Den andra filen anropas: **`<modulename>`_2.log**. Storleken på loggarna är därför begränsad till 2*10 MB per modul och per instans.

Du kan dock behålla större filer. Om du vill aktivera det här ändrar du värdet för **maxFileSizeMb=&quot;10&quot;** i **syslogd**-noden för **conf/serverConf.xml**-filen. Detta värde representerar den största tillåtna storleken i MB för en loggfil.

Om du vill behålla fler detaljnivåer i loggarna kan du starta Adobe Campaign-modulerna med parametern **-verbose**:

**nlserver start  `<MODULE>`@`<INSTANCE>` -verbose**
