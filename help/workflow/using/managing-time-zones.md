---
product: campaign
title: Hantera tidszoner
description: Hantera tidszoner
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 4%

---

# Hantera tidszoner{#managing-time-zones}



Med Adobe Campaign kan du hantera tidsförskjutningar mellan olika länder som berörs av samma instans. Den använda konfigurationen konfigureras när instansen skapas.

Mer information om hur du konfigurerar tidszoner i Adobe Campaign finns i [Installationshandbok för Campaign Classic v7](../../installation/using/time-zone-management.md).

I ett arbetsflöde kan du anpassa scheman för aktivitetskörning och länka en specifik tidszon till en aktivitet eller till hela arbetsflödet. Den här konfigurationen kan vara användbar vid import av filen eller inom ramen för leveransplanering.

## Körningsplanering {#execution-scheduling}

Du kan schemalägga körningen av uppgifter med hjälp av schemaläggaren (se [Schemaläggare](scheduler.md)). Du kan också använda de schemaläggningsalternativ som är tillgängliga i aktiviteterna som erbjuder den här funktionen. Dessa aktiviteter erbjuder **[!UICONTROL Schedule]** tab: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**, osv.

För alla schemalagda aktiviteter, dvs. alla aktiviteter med schemaläggningsalternativ, kan du välja vilken tidszon som ska användas. Tidszonen väljs via **[!UICONTROL Advanced]** flik för den berörda aktiviteten:

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

Om **[!UICONTROL By default]** värdet är markerat används arbetsflödets tidszon eller, i annat fall, programserverns tidszon.

## Länka en tidszon till en aktivitet {#linking-a-time-zone-to-an-activity}

The **[!UICONTROL Advanced]** -fliken i arbetsflödesaktiviteterna där du kan välja dess tidszon. Även om arbetsflödenas tidszon för det mesta räcker, kan det vara nödvändigt att överlagra den om och om igen för en viss aktivitet, till exempel dataimport, för att länka datum till rätt tidszon.
