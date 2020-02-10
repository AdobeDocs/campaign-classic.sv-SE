---
title: Importera och exportera målgrupper
seo-title: Importera och exportera målgrupper
description: Importera och exportera målgrupper
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Importera och exportera målgrupper{#importing-and-exporting-audiences}

## Importera en målgrupp {#importing-an-audience}

Du kan importera målgrupper/segment från Audience Manager eller People core service till Adobe Campaign via mottagarlistorna.

1. Gå till noden **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** i Adobe Campaign Explorer.
1. Välj **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]** i åtgärdsfältet.

   ![](assets/aam_import_audience.png)

1. I det fönster som öppnas klickar du för **[!UICONTROL Select a shared audience]** att gå till listan över delade målgrupper/segment som är tillgängliga från andra Adobe Experience Cloud-lösningar.
1. Välj en målgrupp och bekräfta. Publiken fylls i automatiskt.

   Observera att om du ska kunna importera delade målgrupper bör du tilldelas produkten i Admin Console och vara administratör i Audience Manager. **[!UICONTROL Audience library]** Mer information finns i dokumentationen [till](https://helpx.adobe.com/enterprise/managing/user-guide.html)Admin Console.

   ![](assets/aam_import_audience_3.png)

1. Välj AMC-datakällan i **[!UICONTROL AMC Data source]** fältet för att definiera den typ av data som förväntas.

   ![](assets/aam_import_audience_2.png)

1. Spara publiken.

Publiken importeras via ett tekniskt arbetsflöde. Den importerade listan innehåller element som kan förenas med hjälp av AMC-datakällan. Elementen som inte känns igen av Adobe Campaign importeras inte.

Det tar 24-36 timmar att synkronisera importprocessen när segment importeras direkt från personkärntjänsten eller Audience Manager. Efter den här perioden kan ni hitta och använda er nya målgrupp i Adobe Campaign.

>[!NOTE]
>
>Om du importerar målgrupper från Adobe Analytics till Adobe Campaign måste dessa målgrupper först delas i People Core Service eller Audience Manager. Den här processen tar 12-24 timmar, vilket måste läggas till i synkroniseringen av 24-36 timmar med Campaign.
>
>I det specifika fallet kan tidsramen för målgruppsdelning vara upp till 60 timmar. Mer information om Adobe Analytics-målgruppsdelning i tjänsten People Core och Audience Manager finns i den här [dokumentationen](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html).

Publiken ersätts helt och hållet varje gång den synkroniseras. Endast segment kan importeras. Detaljerade data som nyckelvärdepar, egenskaper och regler stöds inte.

## Exportera en målgrupp {#exporting-an-audience}

Du kan exportera en målgrupp från Adobe Campaign till Audience Manager eller People core service med hjälp av ett arbetsflöde. Processerna för att skapa och använda ett arbetsflöde beskrivs i [det här dokumentet](../../workflow/using/building-a-workflow.md). De exporterade målgrupperna sparas som segment i bastjänsten Folk:

1. Skapa ett nytt arbetsflöde för målinriktning.
1. Använd olika aktiviteter för att ange en uppsättning mottagare som mål.
1. Dra och släpp en **[!UICONTROL Update shared audience]** aktivitet efter att du har målat den och öppna den.

   ![](assets/aam_export_example.png)

1. Definiera målgruppen som du vill exportera med **[!UICONTROL Select a shared audience]** alternativet. I det fönster som öppnas kan du välja en befintlig målgrupp eller skapa en ny.

   Om du väljer en befintlig målgrupp läggs endast de nya posterna till i målgruppen.

   Om du vill exportera mottagarlistan till en ny målgrupp fyller du i **[!UICONTROL Segment name]** fältet och klickar sedan **[!UICONTROL Create]** innan du väljer den nya målgruppen.

   Slutför åtgärden genom att klicka på bocksymbolen längst upp till höger i fönstret och sedan på **[!UICONTROL OK]** knappen.

1. Ange den förväntade datatypen genom **[!UICONTROL AMC Data source]** att markera. Schemat bestäms automatiskt.

   ![](assets/aam_export_audience_activity.png)

1. Spara publiken.

Publiken exporteras sedan. Det finns två utgående övergångar för aktiviteten Spara målgrupp. Huvudövergången innehåller de mottagare som exporterades. Den extra övergången innehåller de mottagare som inte kunde mappas med ett besökar-ID eller deklarerat ID.

Synkroniseringen mellan Adobe Campaign och People Core Service tar 24-36 timmar. Efter den här perioden kan du hitta din nya målgrupp i bastjänsten för människor och återanvända den i andra Adobe Experience Cloud-lösningar. Mer information om hur du använder en delad målgrupp i Adobe Campaign i huvudtjänsten Adobe People finns i den här [dokumentationen](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html).

>[!NOTE]
>
>För att posterna ska kunna stämmas av måste de ha ett Adobe Experience Cloud-ID (visitor-ID eller deklarerat ID). Posterna som inte har något Adobe Experience Cloud ID ignoreras när målgrupper exporteras och importeras.

