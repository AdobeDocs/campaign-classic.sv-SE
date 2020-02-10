---
title: Hantera tidszoner
seo-title: Hantera tidszoner
description: Hantera tidszoner
seo-description: null
page-status-flag: never-activated
uuid: a253861a-fc15-406d-969d-33cfb4169839
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 8bcbcd23-9251-412a-ae72-11f15db74112
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Hantera tidszoner{#managing-time-zones}

Med Adobe Campaign kan ni hantera tidsförskjutningar mellan olika länder som berörs av samma instans. Den använda konfigurationen konfigureras när instansen skapas.

Mer information om hur du konfigurerar tidszoner i Adobe Campaign finns i det här [avsnittet](../../installation/using/time-zone-management.md).

I ett arbetsflöde kan du anpassa scheman för aktivitetskörning och länka en specifik tidszon till en aktivitet eller till hela arbetsflödet. Den här konfigurationen kan vara användbar vid import av filen eller inom ramen för leveransplanering.

## Körningsplanering {#execution-scheduling}

Du kan schemalägga körningen av aktiviteter med schemaläggaren (se [Schemaläggaren](../../workflow/using/scheduler.md)). Du kan också använda de schemaläggningsalternativ som är tillgängliga i aktiviteterna som erbjuder den här funktionen. De här aktiviteterna erbjuder en **[!UICONTROL Schedule]** flik: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]** etc.

För alla schemalagda aktiviteter, dvs. alla aktiviteter med schemaläggningsalternativ, kan du välja vilken tidszon som ska användas. Tidszonen väljs via fliken **[!UICONTROL Advanced]** för den aktuella aktiviteten:

![](assets/wf-timezone-in-a-box.png)

Möjliga värden är:

* Tidszon för server

   Använder tidszonen för Adobe Campaign-programservern.

* Användarens tidszon

   Använder tidszonen för den Adobe Campaign-operator som kör arbetsflödet.

* Tidszon för databas

   Använder tidszonen för databasservern som används.

* Särskilda tidszoner

   Använder den markerade tidszonen.

Om du väljer **[!UICONTROL By default]** värdet används arbetsflödets tidszon eller, i annat fall, programserverns tidszon.

## Länka en tidszon till en aktivitet {#linking-a-time-zone-to-an-activity}

På fliken **[!UICONTROL Advanced]** i arbetsflödesaktiviteterna kan du välja dess tidszon. Även om arbetsflödenas tidszon för det mesta räcker, kan det vara nödvändigt att överlagra den om och om igen för en viss aktivitet, till exempel dataimport, för att länka datum till rätt tidszon.
