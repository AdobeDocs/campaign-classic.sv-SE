---
solution: Campaign Classic
product: campaign
title: Förutsättningar för att migrera till Adobe Campaign 7
description: Förutsättningar för att migrera till Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---


# Förutsättningar för att migrera till Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Innan du kör en migrering bör du läsa avsnittet [Innan du startar migreringen](../../migration/using/before-starting-migration.md) och [konfigurerar plattformen](../../migration/using/configuring-your-platform.md) .

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
