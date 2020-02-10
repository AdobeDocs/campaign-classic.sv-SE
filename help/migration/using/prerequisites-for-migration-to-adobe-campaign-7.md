---
title: Krav för migrering till Adobe Campaign 7
seo-title: Krav för migrering till Adobe Campaign 7
description: Krav för migrering till Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Krav för migrering till Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Innan du kör en migrering bör du läsa avsnittet [Innan du startar migreringen](../../migration/using/before-starting-migration.md) och [konfigurerar plattformen](../../migration/using/configuring-your-platform.md) .

När du migrerar från v6.02 till Adobe Campaign v7 levereras inte vissa filer som levererats tidigare.

Om ett klientfel uppstår måste du antingen uppdatera dina instrumentpaneler med den nya Adobe Campaign v7-koden eller manuellt kopiera följande filer från v6.02-instansen till v7-instansen:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
