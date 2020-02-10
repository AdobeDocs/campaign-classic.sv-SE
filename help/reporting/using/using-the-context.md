---
title: Använda kontexten
seo-title: Använda kontexten
description: Använda kontexten
seo-description: null
page-status-flag: never-activated
uuid: ac8c7068-d640-4934-b7f5-bc91b98eab4c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 72fe6df0-0271-48f9-bd6d-bb1ff25fbdf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Använda kontexten{#using-the-context}

När du vill representera data i form av **[!UICONTROL tables]** eller **[!UICONTROL charts]** kan den hämtas från två källor: en ny fråga (se [Definiera ett direktfilter på data](#defining-a-direct-filter-on-data)) eller rapportkontexten (se [Använda kontextdata](#using-context-data)).

## Definiera ett direktfilter på data {#defining-a-direct-filter-on-data}

### Filtrera data {#filtering-data}

Det är inte obligatoriskt att använda en **[!UICONTROL Query]** typaktivitet när du skapar en rapport. Data kan filtreras direkt i de tabeller och diagram som rapporten består av.

På så sätt kan du välja vilka data som ska visas i rapporten direkt via rapportens **[!UICONTROL Page]** aktivitet.

Det gör du genom att klicka på **[!UICONTROL Filter data...]** länken på **[!UICONTROL Data]** fliken: Med den här länken kan du komma åt uttrycksredigeraren för att definiera en fråga för de data som ska analyseras.

![](assets/reporting_filter_data_from_page.png)

### Exempel: använda ett filter i ett diagram {#example--use-a-filter-in-a-chart}

I följande exempel vill vi att diagrammet bara ska visa mottagarprofiler som bor i Frankrike och som har köpt något under året.

Om du vill definiera det här filtret placerar du en sida i diagrammet och redigerar den. Klicka på **[!UICONTROL Filter data]** länken och skapa ett filter som matchar de data som du vill visa. Mer information om hur du skapar frågor i Adobe Campaign finns i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

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
1. Gå till **[!UICONTROL Data]** fliken och välj den kub som ska användas.
1. Klicka på **[!UICONTROL Filter data...]** länken och definiera följande fråga för att ta bort Adobe från listan över företag.

   ![](assets/s_ncs_advuser_report_display_03.png)

Endast mottagare som uppfyller filtervillkoren visas i rapporten.

![](assets/s_ncs_advuser_report_display_04.png)

## Använda kontextdata {#using-context-data}

För att representera data i form av en **[!UICONTROL table]** eller en **[!UICONTROL chart]**, kan data hämtas från rapportkontexten.

På den sida som innehåller tabellen eller diagrammet kan du välja datakälla på fliken **[!UICONTROL Data]** .

![](assets/s_ncs_advuser_report_datasource_3.png)

* Med det här **[!UICONTROL New query]** alternativet kan du skapa en fråga för att samla in data. Mer information finns i [Definiera ett direktfilter på data](#defining-a-direct-filter-on-data).
* Med **[!UICONTROL Context data]** alternativet kan du använda indata: rapportens sammanhang sammanfaller med informationen i den inkommande övergången på sidan som innehåller diagrammet eller tabellen. Detta sammanhang kan till exempel innehålla data som samlats in via en **[!UICONTROL Query]** aktivitet som placerats före **[!UICONTROL Page]** aktiviteten och för vilken du måste ange tabellen och de fält som rapporten gäller.

Bygg till exempel följande fråga för mottagarna i en frågeruta:

![](assets/s_ncs_advuser_report_datasource_2.png)

Ange sedan datakällan i rapporten, i det här fallet: **[!UICONTROL Data from the context]**.

Dataplatsen härleds automatiskt. Om det behövs kan du tvinga fram datasökvägen.

![](assets/s_ncs_advuser_report_datasource_4.png)

När du väljer vilka data som statistiken ska gälla, sammanfaller de tillgängliga fälten med de data som anges i frågan.

![](assets/s_ncs_advuser_report_datasource_1.png)

