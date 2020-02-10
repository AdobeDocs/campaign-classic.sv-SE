---
title: Leveranskontroll
seo-title: Leveranskontroll
description: Leveranskontroll
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Leveranskontroll{#delivery-control}

Med en åtgärd av typen **Leveranskontroll** kan du starta, pausa eller stoppa en leverans.

Detta kan vara den leverans som anges i övergången, en leverans som valts uttryckligen eller en leverans som beräknas av ett skript. Mer information finns i [Leverans](../../workflow/using/delivery.md).

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
