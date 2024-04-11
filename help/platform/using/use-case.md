---
product: campaign
title: Användningsfall
description: Användningsfall
feature: Subscriptions, Email, Data Management
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 2%

---

# Användningsfall{#use-case}



## Skapa ett filter för e-postformat för prenumeranter {#creating-a-filter-on-the-email-format-of-subscribers}

I det här exemplet visas hur du skapar ett filter för att sortera nyhetsbrevsprenumerationer baserat på mottagarnas e-postformat.

För att göra detta måste vi använda en fördefinierad filhanterare: dessa filter är länkade till en dokumenttyp och nås via **[!UICONTROL Administration > Configuration > Predefined filters]** nod. Dessa datafilter kan användas för varje typ av redigerare (eller dokument) i programmet.

Datafilter skapas på samma sätt som fördefinierade filter, men det finns ytterligare ett fält där du kan välja dokumenttypen som filtret ska tillämpas på.

Använd följande steg:

1. Skapa ett nytt filter via **[!UICONTROL Administration > Configuration > Predefined filters]** nod.
1. Klicka på **[!UICONTROL Select link]** ikon för att välja det berörda dokumentet:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Välj prenumerationsschemat (nms:subscription) och klicka på **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Klicka **[!UICONTROL Edit link]** om du vill visa fälten i det markerade dokumentet.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Du kan sedan visa innehållet i det markerade dokumentet:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Du kan komma åt dessa fält för att definiera filtervillkor i filterredigerarens brödtext. Ett programfilter definieras på exakt samma sätt som ett avancerat filter. Se [Skapa ett avancerat filter](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Skapa ett nytt filter för prenumerationer som endast visar prenumerationer med ett odefinierat e-postformat:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Klicka **[!UICONTROL Save]** om du vill lägga till ett filter i de fördefinierade filtren för den här typen av lista.
1. Nu kan du använda det här filtret i **[!UICONTROL Subscriptions]** -fliken i mottagarprofilen. Du kan komma åt filtret Okänt e-postformat genom att klicka på **[!UICONTROL Filters]** -knappen.

   ![](assets/s_ncs_user_filter_on_events.png)

   Namnet på det aktuella filtret visas ovanför listan. Klicka på knappen **[!UICONTROL Delete this filter]** -ikon.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
