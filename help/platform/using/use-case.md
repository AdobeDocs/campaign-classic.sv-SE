---
product: campaign
title: Användningsfall
description: Användningsfall
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 2%

---

# Användningsfall{#use-case}

![](../../assets/common.svg)

## Skapa ett filter för e-postformat för prenumeranter {#creating-a-filter-on-the-email-format-of-subscribers}

I det här exemplet visas hur du skapar ett filter för att sortera nyhetsbrevsprenumerationer baserat på mottagarnas e-postformat.

För att göra detta måste vi använda en fördefinierad filhanterare: Dessa filter är länkade till en dokumenttyp och nås via noden **[!UICONTROL Administration > Configuration > Predefined filters]**. Dessa datafilter kan användas för varje typ av redigerare (eller dokument) i programmet.

Datafilter skapas på samma sätt som fördefinierade filter, men det finns ytterligare ett fält där du kan välja dokumenttypen som filtret ska tillämpas på.

Använd följande steg:

1. Skapa ett nytt filter via noden **[!UICONTROL Administration > Configuration > Predefined filters]**.
1. Klicka på ikonen **[!UICONTROL Select link]** för att välja det berörda dokumentet:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Välj prenumerationsschemat (nms:subscription) och klicka på **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Klicka på **[!UICONTROL Edit link]** för att visa fälten i det markerade dokumentet.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Du kan sedan visa innehållet i det markerade dokumentet:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Du kan komma åt dessa fält för att definiera filtervillkor i filterredigerarens brödtext. Ett programfilter definieras på exakt samma sätt som ett avancerat filter. Se [Skapa ett avancerat filter](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Skapa ett nytt filter för prenumerationer som endast visar prenumerationer med ett odefinierat e-postformat:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Klicka på **[!UICONTROL Save]** om du vill lägga till ett filter i de fördefinierade filtren för den här typen av lista.
1. Du kan nu använda det här filtret på fliken **[!UICONTROL Subscriptions]** i mottagarprofilen; Du kommer åt filtret Okänt e-postformat genom att klicka på knappen **[!UICONTROL Filters]**.

   ![](assets/s_ncs_user_filter_on_events.png)

   Namnet på det aktuella filtret visas ovanför listan. Om du vill avbryta filtret klickar du på ikonen **[!UICONTROL Delete this filter]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
