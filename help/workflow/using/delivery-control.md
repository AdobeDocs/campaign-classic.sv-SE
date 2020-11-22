---
solution: Campaign Classic
product: campaign
title: Leveranskontroll
description: Läs mer om arbetsflödesaktiviteten Leveranskontroll
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# Leveranskontroll{#delivery-control}

Med en åtgärd av typen **Leveranskontroll** kan du starta, pausa eller stoppa en leverans.

Detta kan vara leveransen som anges i övergången, en leverans som valts uttryckligen eller en leverans som beräknas av ett skript. For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

Om du väljer **[!UICONTROL Start]** det här alternativet utför aktiviteten alla steg som krävs för att starta leveransen (målberäkning, förberedelse av innehåll, leverans). Om några av dessa steg redan har utförts av en tidigare arbetsflödesaktivitet, kommer de inte att utföras igen. Om måluppskattningen till exempel redan utfördes av en **[!UICONTROL Delivery]** typaktivitet (se [Leverans](../../workflow/using/delivery.md)), kommer aktiviteten att starta de återstående stegen (förberedelse och leverans av **[!UICONTROL Act on the delivery]** innehåll).

Följande alternativ är tillgängliga:

* **[!UICONTROL Generate an outbound transition]**

   Skapar en utgående övergång som ska aktiveras i slutet av körningen. Du kan välja om du vill hämta målet för den utgående leveransen eller inte.

* **[!UICONTROL Processing errors]**

   Se [Bearbetningsfel](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## Indataparametrar {#input-parameters}

* deliveryId

Leverans-ID, om den valda åtgärden är **[!UICONTROL Specified in the transition]**.
