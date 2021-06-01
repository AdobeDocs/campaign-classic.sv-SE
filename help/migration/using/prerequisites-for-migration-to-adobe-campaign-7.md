---
product: campaign
title: Förhandskrav för att migrera till Adobe Campaign 7
description: Förhandskrav för att migrera till Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# Förhandskrav för att migrera till Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Läs mer i avsnitten [Innan du startar migreringen](../../migration/using/before-starting-migration.md) och [Konfigurera plattformen](../../migration/using/configuring-your-platform.md) innan du kör en migrering.

När du migrerar från v6.02 till Adobe Campaign v7 levereras inte alla filer som levereras i förväg.

Om ett klientfel uppstår måste du antingen uppdatera dina instrumentpaneler med den nya Adobe Campaign v7-koden eller manuellt kopiera följande filer från v6.02-instansen till v7-instansen:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
