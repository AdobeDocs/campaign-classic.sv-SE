---
product: campaign
title: Loggfiler
description: Loggfiler
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 2%

---

# Loggfiler{#log-files}



Loggfilerna är ordnade enligt följande:

![](assets/d_ncs_directory.png)

Varje **nlserver** i skapas en loggfil som sparas i följande katalog: **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

The **nlserver syslogd** sparas loggarna på disken. Den här modulen liknar Unix **syslog daemon**, men har anpassats för kompatibilitet mellan Unix och Windows. De andra Adobe Campaign-modulerna sparar inte sina loggar på disken utan delegerar uppgiften till **syslogd** genom att skicka UDP-paket.

Som standard har Adobe Campaign-plattformen **syslogd** som är installerad på den, men det går att använda en annan **syslog daemon**. Den här modulen skapar loggfilerna i **logg** katalog.

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
| mta.log | loggar för mta-modul |
| mtachild.log | Bearbetningsloggar för meddelandeleverans |
| wfserver.log | Loggar för arbetsflödesservermodulen |
| runwf.log | Körningsloggar för arbetsflöde |
| inMail.log | Logg för studsmoduler |
| logins.log | Loggar alla inloggningsförsök till Adobe Campaign (vare sig de lyckas eller inte) |

>[!IMPORTANT]
>
>The **redir** katalogen finns bara på omdirigeringsservrar. The **url** underkatalogen innehåller matchningarna för de URL:er som ska omdirigeras samt underkatalogen **logg** innehåller spårningsloggarna. Om du vill generera spårningsloggar **trackinglogd** modulen måste köras.

För optimering av prestanda och lagring delas filen logins.log upp i flera filer, en varje dag (logins.yy-mm-dd.log) med högst 365 filer. Antalet dagar kan ändras i serverConf.xml, under syslogd (**maxNumberOfLoginsFiles** ). Läs dokumentationen på [serverkonfigurationsfil](../../installation/using/the-server-configuration-file.md#syslogd).

Som standard är loggarna begränsade till två 10 MB-filer per modul och per instans. Den andra filen anropas: **`<modulename>`_2.log**. Loggarna är därför begränsade till 2&#42;10 MB per modul och per instans.

Du kan dock behålla större filer. Om du vill aktivera det här ändrar du värdet för **maxFileSizeMb=&quot;10&quot;** i **syslogd** nod på **conf/serverConf.xml** -fil. Detta värde representerar den största tillåtna storleken i MB för en loggfil.

Om du vill behålla fler detaljnivåer i loggarna kan du starta Adobe Campaign-modulerna med **-verbose** parameter:

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**
