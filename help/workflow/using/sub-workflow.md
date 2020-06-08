---
title: Delarbetsflöde
seo-title: Delarbetsflöde
description: Delarbetsflöde
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---


# Delarbetsflöde{#sub-workflow}

Med den här **[!UICONTROL Sub-workflow]** aktiviteten kan du aktivera körningen av ett annat arbetsflöde och återställa resultatet. Med den här aktiviteten kan du använda komplexa arbetsflöden med ett förenklat gränssnitt.

Du kan anropa flera delarbetsflöden i ett enda arbetsflöde. Delarbetsflöden körs synkront.

I exemplet nedan anropar ett&quot;master&quot;-arbetsflöde ett delarbetsflöde med jumps. Mer information om grafiska objekt av typen hoppskrivningar finns i [det här avsnittet](../../workflow/using/jump--start-point-and-end-point-.md).

1. Skapa ett arbetsflöde som du vill använda som ett underarbetsflöde i ett annat arbetsflöde.
1. Infoga en **[!UICONTROL Jump (end point)]** aktivitet med prioriteten 1 i början av arbetsflödet. Om du har flera&quot;slutpunktshopp&quot; använder Adobe Campaign&quot;slutpunktshoppet&quot; med det lägsta talet.
1. Infoga en **[!UICONTROL Jump (start point)]** aktivitet med prioritet 2 i slutet av arbetsflödet. Om du har flera&quot;startpunktshopp&quot; använder Adobe Campaign&quot;startpunkten&quot; med det högsta talet.

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >Om delarbetsflödesaktiviteten refererar till ett arbetsflöde med flera **[!UICONTROL Jump]** aktiviteter körs delarbetsflödet mellan &quot;slutpunktstypen&quot; och det lägsta talet och &quot;startpunktstypen&quot; med det högsta talet.
   >
   >För att delarbetsflödet ska kunna köras på rätt sätt får du bara ha en &quot;slutpunktstyp&quot; som hoppar med det lägsta talet och bara en &quot;startpunktstyp&quot; som hoppar med det högsta talet.

1. Slutför och spara det här delarbetsflödet.
1. Skapa ett huvudarbetsflöde.
1. Infoga en **[!UICONTROL Sub-workflow]** aktivitet och öppna den.
1. Välj det arbetsflöde som du vill använda i **[!UICONTROL Workflow template]** listrutan.

   ![](assets/subworkflow_selection.png)

1. Du kan också lägga till ett konfigurationsskript för att ändra det refererade arbetsflödet.
1. Klicka på **[!UICONTROL Ok]**. En utgående övergång skapas automatiskt med aktivitetsetiketten från det valda arbetsflödet. **[!UICONTROL Jump (start point)]**

   ![](assets/subworkflow_outbound.png)

1. Kör arbetsflödet.

När arbetsflödet som anropades som ett underarbetsflöde har fortfarande **[!UICONTROL Being edited]** status, vilket innebär följande:

* Du kan inte högerklicka på övergångarna för att visa målet.
* Antalet mellanliggande populationer kan inte visas.
* Loggarna sammanställs i huvudarbetsflödet och kallas bara för delarbetsflöde.

Det här arbetsflödet är i själva verket bara en mall. Ett nytt delarbetsflöde som är baserat på den här mallen skapas när det anropas från huvudarbetsflödet.

## Indataparametrar (valfritt) {#input-parameters--optional-}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar den population som frågan riktar sig till. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

* targetSchema: Det här värdet är arbetstabellens schema. Den här parametern är giltig för alla övergångar med **[!UICONTROL tableName]** och **[!UICONTROL schema]**.
