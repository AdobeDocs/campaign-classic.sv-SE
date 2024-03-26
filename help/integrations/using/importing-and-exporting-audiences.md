---
product: campaign
title: Importera och exportera målgrupper
description: Importera och exportera målgrupper
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Importera och exportera målgrupper{#importing-and-exporting-audiences}



## Importera en målgrupp {#importing-an-audience}

Du kan importera målgrupper/segment från Audience Manager eller People core service till Adobe Campaign via mottagarlistorna.

1. Gå till **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** i Adobe Campaign Explorer.
1. Välj **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. Klicka på **[!UICONTROL Select a shared audience]** om du vill gå till en lista över delade målgrupper/segment som är tillgängliga från andra Adobe Experience Cloud-lösningar.
1. Välj en målgrupp och bekräfta. Publiken fylls i automatiskt.

   Observera att för att kunna importera delade målgrupper bör du tilldelas **[!UICONTROL Audience library]** i Admin Console och vara administratör i Audience Manager. Mer information finns i [Dokumentation till Admin Console](https://helpx.adobe.com/se/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Välj AMC-datakällan på menyn **[!UICONTROL AMC Data source]** för att definiera den typ av data som förväntas.

   ![](assets/aam_import_audience_2.png)

1. Spara publiken.

Publiken importeras via ett tekniskt arbetsflöde. Den importerade listan innehåller element som kan förenas med hjälp av AMC-datakällan. Elementen som inte känns igen av Adobe Campaign importeras inte.

Det tar 24-36 timmar att synkronisera importprocessen när segment importeras direkt från personbastjänsten eller Audience Manager. Efter den här perioden kan du hitta och använda din nya målgrupp i Adobe Campaign.

>[!NOTE]
>
>Om du importerar målgrupper från Adobe Analytics till Adobe Campaign måste dessa målgrupper först delas i People Core Service eller Audience Manager. Den här processen tar 12-24 timmar, vilket måste läggas till i synkroniseringen av 24-36 timmar med Campaign.
>
>I det specifika fallet kan tidsramen för målgruppsdelning vara upp till 60 timmar. Mer information om Adobe Analytics målgruppsdelning i tjänsten People Core och Audience Manager finns i [Adobe Analytics-dokumentation](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html).

Publiken ersätts helt och hållet varje gång den synkroniseras. Endast segment kan importeras. Detaljerade data som nyckelvärdepar, egenskaper och regler stöds inte.

## Exportera en målgrupp {#exporting-an-audience}

Du kan exportera en målgrupp från Adobe Campaign till Audience Manager eller People core service med hjälp av ett arbetsflöde. Processerna för att skapa och använda ett arbetsflöde beskrivs i [det här dokumentet](../../workflow/using/building-a-workflow.md). De exporterade målgrupperna sparas som segment i bastjänsten Folk:

1. Skapa ett nytt arbetsflöde för målinriktning.
1. Använd olika aktiviteter för att ange en uppsättning mottagare som mål.
1. Dra och släpp en **[!UICONTROL Update shared audience]** och sedan öppna den.

   ![](assets/aam_export_example.png)

1. Definiera den målgrupp som du vill exportera via **[!UICONTROL Select a shared audience]** alternativ. I det fönster som öppnas kan du välja en befintlig målgrupp eller skapa en ny.

   Om du väljer en befintlig målgrupp läggs endast de nya posterna till i målgruppen.

   Om du vill exportera mottagarlistan till en ny målgrupp fyller du i **[!UICONTROL Segment name]** klicka sedan på **[!UICONTROL Create]** innan du väljer den nya målgruppen.

   Slutför åtgärden genom att klicka på bocksymbolen längst upp till höger i fönstret och sedan på **[!UICONTROL OK]** -knappen.

1. Välj **[!UICONTROL AMC Data source]** för att ange den förväntade datatypen. Schemat bestäms automatiskt.

   ![](assets/aam_export_audience_activity.png)

1. Spara publiken.

Publiken exporteras sedan. Det finns två utgående övergångar för aktiviteten Spara målgrupp. Huvudövergången innehåller de mottagare som exporterades. Den extra övergången innehåller de mottagare som inte kunde mappas med ett besökar-ID eller deklarerat ID.

Synkronisering mellan Adobe Campaign och People Core Service tar 24-36 timmar. Efter den här perioden kan du hitta din nya målgrupp i bastjänsten People och återanvända den i andra Adobe Experience Cloud-lösningar. Mer information om hur du använder en delad Adobe Campaign-målgrupp i Adobe People-bastjänsten finns i [dokumentation](https://experienceleague.adobe.com/docs/core-services/interface/audiences/t-audience-create.html).

>[!NOTE]
>
>För att posterna ska kunna stämmas av måste de ha ett Adobe Experience Cloud-ID (&quot;besökar-ID&quot; eller&quot;deklarerat ID&quot;). Posterna som inte har något Adobe Experience Cloud-ID ignoreras vid export och import av målgrupper.
