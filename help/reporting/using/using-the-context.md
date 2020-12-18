---
solution: Campaign Classic
product: campaign
title: Använda sammanhanget
description: Använda sammanhanget
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 2%

---


# Använda sammanhanget{#using-the-context}

När du vill representera data i formatet **[!UICONTROL tables]** eller **[!UICONTROL charts]** kan de hämtas från två källor: en ny fråga (se [Definiera ett direktfilter på data](#defining-a-direct-filter-on-data)) eller rapportkontexten (se [Använda kontextdata](#using-context-data)).

## Definiera ett direktfilter på data {#defining-a-direct-filter-on-data}

### Filtrera data {#filtering-data}

Det är inte obligatoriskt att använda en **[!UICONTROL Query]**-typaktivitet när du skapar en rapport. Data kan filtreras direkt i de tabeller och diagram som rapporten består av.

Detta gör att du kan välja vilka data som ska visas i rapporten direkt via aktiviteten **[!UICONTROL Page]** i rapporten.

Det gör du genom att klicka på länken **[!UICONTROL Filter data...]** på fliken **[!UICONTROL Data]**: Med den här länken kan du komma åt uttrycksredigeraren för att definiera en fråga för de data som ska analyseras.

![](assets/reporting_filter_data_from_page.png)

### Exempel: använda ett filter i ett diagram {#example--use-a-filter-in-a-chart}

I följande exempel vill vi att diagrammet bara ska visa mottagarprofiler som bor i Frankrike och som har köpt något under året.

Om du vill definiera det här filtret placerar du en sida i diagrammet och redigerar den. Klicka på länken **[!UICONTROL Filter data]** och skapa ett filter som matchar de data som du vill visa. Mer information om hur du skapar frågor i Adobe Campaign finns i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

Här vill vi visa uppdelningen efter ort för valda mottagare.

![](assets/reporting_graph_with_2vars.png)

Återgivningen ser ut så här:

![](assets/reporting_graph_with_2vars_preview.png)

### Exempel: använda ett filter i en pivottabell {#example--use-a-filter-in-a-pivot-table}

I det här exemplet kan du bara visa icke-parisiska kunder i pivottabellen, utan att använda en annan fråga i förväg.

Använd följande steg:

1. Placera en sida i diagrammet och redigera den.
1. Skapa en pivottabell.
1. Gå till fliken **[!UICONTROL Data]** och välj den kub som ska användas.
1. Klicka på länken **[!UICONTROL Filter data...]** och definiera följande fråga för att ta bort Adobe från listan över företag.

   ![](assets/s_ncs_advuser_report_display_03.png)

Endast mottagare som uppfyller filtervillkoren visas i rapporten.

![](assets/s_ncs_advuser_report_display_04.png)

## Använda kontextdata {#using-context-data}

För att representera data i form av en **[!UICONTROL table]** eller en **[!UICONTROL chart]** kan data hämtas från rapportkontexten.

På sidan som innehåller tabellen eller diagrammet kan du välja datakälla på fliken **[!UICONTROL Data]**.

![](assets/s_ncs_advuser_report_datasource_3.png)

* Med alternativet **[!UICONTROL New query]** kan du skapa en fråga för att samla in data. Mer information finns i [Definiera ett direktfilter på data](#defining-a-direct-filter-on-data).
* Med alternativet **[!UICONTROL Context data]** kan du använda indata: rapportens sammanhang sammanfaller med informationen i den inkommande övergången på sidan som innehåller diagrammet eller tabellen. Den här kontexten kan till exempel innehålla data som samlats in via en **[!UICONTROL Query]**-aktivitet som placerats före **[!UICONTROL Page]**-aktiviteten och för vilken du måste ange tabellen och fälten som rapporten gäller.

Bygg till exempel följande fråga för mottagarna i en frågeruta:

![](assets/s_ncs_advuser_report_datasource_2.png)

Ange sedan datakällan i rapporten, i det här fallet: **[!UICONTROL Data from the context]**.

Dataplatsen härleds automatiskt. Om det behövs kan du tvinga fram datasökvägen.

![](assets/s_ncs_advuser_report_datasource_4.png)

När du väljer vilka data som statistiken ska gälla, sammanfaller de tillgängliga fälten med de data som anges i frågan.

![](assets/s_ncs_advuser_report_datasource_1.png)

