---
product: campaign
title: Leveranskontroll
description: Läs mer om arbetsflödesaktiviteten Leveranskontroll
feature: Workflows
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---

# Leveranskontroll{#delivery-control}

![](../../assets/v7-only.svg)

A **Leveranskontroll**-type kan du starta, pausa eller stoppa en leverans.

Detta kan vara leveransen som anges i övergången, en leverans som valts uttryckligen eller en leverans som beräknas av ett skript. Mer information finns i [Leverans](delivery.md).

![](assets/edit_diffusion_act.png)

Om du väljer **[!UICONTROL Start]** kommer aktiviteten att utföra alla steg som krävs för att starta leveransen (målberäkning, förberedelse av innehåll, leverans). Om några av dessa steg redan har utförts av en tidigare arbetsflödesaktivitet, kommer de inte att utföras igen. Om måluppskattningen till exempel redan utfördes av en **[!UICONTROL Delivery]** typaktivitet (se [Leverans](delivery.md)), **[!UICONTROL Act on the delivery]** kommer att starta de återstående stegen (förberedelse och leverans av innehåll).

Följande alternativ är tillgängliga:

* **[!UICONTROL Generate an outbound transition]**

   Skapar en utgående övergång som ska aktiveras i slutet av körningen. Du kan välja om du vill hämta målet för den utgående leveransen eller inte.

* **[!UICONTROL Processing errors]**

   Se [Bearbetningsfel](monitoring-workflow-execution.md#processing-errors).

## Indataparametrar {#input-parameters}

* deliveryId

Leverans-ID, om den valda åtgärden är **[!UICONTROL Specified in the transition]**.
