---
product: campaign
title: Hantera tidszoner
description: Hantera tidszoner
feature: Workflows
hide: true
hidefromtoc: true
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 2%

---

# Hantera tidszoner{#managing-time-zones}



Med Adobe Campaign kan du hantera tidsförskjutningar mellan olika länder som berörs av samma instans. Den använda konfigurationen konfigureras när instansen skapas.

Mer information om hur du konfigurerar tidszoner i Adobe Campaign finns i [Installationshandboken för Campaign Classic v7](../../installation/using/time-zone-management.md).

I ett arbetsflöde kan du anpassa scheman för aktivitetskörning och länka en specifik tidszon till en aktivitet eller till hela arbetsflödet. Den här konfigurationen kan vara användbar vid import av filen eller inom ramen för leveransplanering.

## Körningsplanering {#execution-scheduling}

Du kan schemalägga körningen av aktiviteter med schemaläggaren (se [Schemaläggaren](scheduler.md)). Du kan också använda de schemaläggningsalternativ som är tillgängliga i aktiviteterna som erbjuder den här funktionen. Dessa aktiviteter erbjuder en **[!UICONTROL Schedule]**-flik: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]** osv.

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

Om värdet **[!UICONTROL By default]** har valts används arbetsflödets tidszon eller, i annat fall, programserverns tidszon.

## Länka en tidszon till en aktivitet {#linking-a-time-zone-to-an-activity}

På fliken **[!UICONTROL Advanced]** i arbetsflödesaktiviteterna kan du välja dess tidszon. Även om arbetsflödenas tidszon för det mesta räcker, kan det vara nödvändigt att överlagra den om och om igen för en viss aktivitet, till exempel dataimport, för att länka datum till rätt tidszon.
