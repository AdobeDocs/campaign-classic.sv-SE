---
product: campaign
title: Använd kontexten i dina rapporter
description: Lär dig använda kontexten i dina rapporter
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Reporting, Monitoring
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# Använd kontexten i dina rapporter{#using-the-context}



När du vill representera data i form av **[!UICONTROL tables]** eller **[!UICONTROL charts]** kan den hämtas från två källor: en ny fråga (se [Definiera ett direktfilter på data](#defining-a-direct-filter-on-data)) eller rapportsammanhanget (se [Använd kontextdata](#using-context-data)).

## Definiera ett direktfilter på data {#defining-a-direct-filter-on-data}

### Filtrera data {#filtering-data}

Använda **[!UICONTROL Query]** typaktivitet är inte obligatoriskt när du skapar en rapport. Data kan filtreras direkt i de tabeller och diagram som rapporten består av.

Detta gör att du kan välja vilka data som ska visas i rapporten direkt via **[!UICONTROL Page]** rapportens aktivitet.

Klicka på **[!UICONTROL Filter data...]** i **[!UICONTROL Data]** tab: this link allows you access the expressions editor to define a query on the data to be analyzed.

![](assets/reporting_filter_data_from_page.png)

### Exempel: använd ett filter i ett diagram {#example--use-a-filter-in-a-chart}

I följande exempel vill vi att diagrammet bara ska visa mottagarprofiler som bor i Frankrike och som har köpt något under året.

Om du vill definiera det här filtret placerar du en sida i diagrammet och redigerar den. Klicka på **[!UICONTROL Filter data]** och skapa det filter som matchar de data som du vill visa. Mer information om hur du skapar frågor i Adobe Campaign finns i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Här vill vi visa uppdelningen efter ort för de valda mottagarna.

![](assets/reporting_graph_with_2vars.png)

Återgivningen ser ut så här:

![](assets/reporting_graph_with_2vars_preview.png)

### Exempel: använd ett filter i en pivottabell {#example--use-a-filter-in-a-pivot-table}

I det här exemplet kan du bara visa icke-parisiska kunder i pivottabellen, utan att använda en annan fråga i förväg.

Använd följande steg:

1. Placera en sida i diagrammet och redigera den.
1. Skapa en pivottabell.
1. Gå till **[!UICONTROL Data]** och välj den kub som ska användas.
1. Klicka på **[!UICONTROL Filter data...]** och definiera följande fråga för att ta bort Adobe från listan över företag.

   ![](assets/s_ncs_advuser_report_display_03.png)

Endast mottagare som uppfyller filtervillkoren visas i rapporten.

![](assets/s_ncs_advuser_report_display_04.png)

## Använd kontextdata {#using-context-data}

Representera data i form av en **[!UICONTROL table]** eller en **[!UICONTROL chart]** kan data hämtas från rapportkontexten.

På sidan som innehåller tabellen eller diagrammet, **[!UICONTROL Data]** kan du välja datakälla.

![](assets/s_ncs_advuser_report_datasource_3.png)

* The **[!UICONTROL New query]** kan du skapa en fråga för datainsamling. Mer information finns i [Definiera ett direktfilter på data](#defining-a-direct-filter-on-data).
* The **[!UICONTROL Context data]** kan du använda indata: rapportens kontext sammanfaller med informationen i den inkommande övergången på sidan som innehåller diagrammet eller tabellen. Det här sammanhanget kan t.ex. innehålla data som samlats in via en **[!UICONTROL Query]** aktivitet som placerats före **[!UICONTROL Page]** och för vilken du måste ange tabellen och fälten som rapporten gäller.

Bygg till exempel följande fråga för mottagarna i en frågeruta:

![](assets/s_ncs_advuser_report_datasource_2.png)

Ange sedan datakällan i rapporten, i det här fallet: **[!UICONTROL Data from the context]**.

Dataplatsen härleds automatiskt. Om det behövs kan du tvinga fram datasökvägen.

![](assets/s_ncs_advuser_report_datasource_4.png)

När du väljer vilka data som statistiken ska gälla, sammanfaller de tillgängliga fälten med de data som anges i frågan.

![](assets/s_ncs_advuser_report_datasource_1.png)
