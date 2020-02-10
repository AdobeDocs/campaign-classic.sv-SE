---
title: Loggfiler
seo-title: Loggfiler
description: Loggfiler
seo-description: null
page-status-flag: never-activated
uuid: 266bc067-0218-4b3e-941c-dc5cd0b6a10d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: fac3e3ec-82a7-4087-ba88-2b28b0f69d1c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f018df9a2f7516b92f1f25a757065ef268136a5

---


# Loggfiler{#log-files}

Loggfilerna är ordnade enligt följande:

![](assets/d_ncs_directory.png)

Varje **lserver** -modul genererar en loggfil som sparats i följande katalog: **`<installation directory>`/var/`<instance>`/log/`<module>`.log **.

Loggarna sparas i **servermodulen** . Den här modulen liknar Unix **syslog daemon**, men har anpassats för kompatibilitet mellan Unix och Windows. De andra Adobe Campaign-modulerna sparar inte sina loggar på disken. de delegerar uppgiften till **systemmodulen** genom att skicka UDP-paket.

Som standard har Adobe Campaign-plattformen **syslogd** -modulen installerad, men det går att använda en annan **syslog-daemon**. Den här modulen skapar loggfilerna i **loggkatalogen** .

Loggarna för moduler med flera instanser lagras i följande katalog: **`<installation directory>`/var/default/log/**. Samma loggfil delas av alla instanser (t.ex.**web.log **).

Loggarna för de andra modulerna lagras i en undermapp som heter efter instansen. Varje instans har sina egna loggfiler.

Loggfiler med flera instanser visas i följande tabell:

| Fil | Beskrivning |
|---|---|
| web.log | Loggar för webbmodulen (klientkonsol, rapporter, SOAP API osv.) |
| webmdl.log | Loggar från omdirigeringsmodulen |
| watchdog.log | Loggar från processövervakningsmodulen i Adobe Campaign |
| trackinglogd.log | Spårningsloggar |

Loggfilerna för en instans visas i följande tabell:

| Fil | Beskrivning |
|---|---|
| mta.log | loggar för mta-modulen |
| mtachild.log | Bearbetningsloggar för meddelandeleverans |
| wfserver.log | Loggar för arbetsflödesservermodulen |
| runwf.log | Körningsloggar för arbetsflöde |
| inMail.log | Logg för studsande e-postmodul |
| inloggningar.log | Loggar alla inloggningsförsök till Adobe Campaign (lyckas eller inte) |

>[!CAUTION]
>
>Katalogen **redir** finns bara på omdirigeringsservrar. Underkatalogen **url** innehåller matchningar för de URL:er som ska omdirigeras och **loggen** för underkatalogen innehåller spårningsloggarna. Om du vill generera spårningsloggar måste **spårningsloggmodulen** köras.

För optimering av prestanda och lagring delas filen logins.log upp i flera filer, en varje dag (logins.yy-mm-dd.log) med högst 365 filer. Antalet dagar kan ändras i serverConf.xml under syslogd (**alternativet maxNumberOfLoginsFiles** ). Mer information finns i dokumentationen om [serverkonfigurationsfilen](../../installation/using/the-server-configuration-file.md#syslogd).

Som standard är loggarna begränsade till två 10 MB-filer per modul och per instans. Den andra filen anropas: **`<modulename>`_2.log **. Storleken på loggarna är därför begränsad till 2*10 MB per modul och per instans.

Du kan dock behålla större filer. Aktivera detta genom att ändra värdet för inställningen **maxFileSizeMb=&quot;10&quot;** i noden **syslogd** i **conf/serverConf.xml** . Detta värde representerar den största tillåtna storleken i MB för en loggfil.

Om du vill behålla fler detaljnivåer i loggarna kan du starta Adobe Campaign-modulerna med parametern **-verbose** :

**nlserver start`<MODULE>`@`<INSTANCE>`-verbose**
