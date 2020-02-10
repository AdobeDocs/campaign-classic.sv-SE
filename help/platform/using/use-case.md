---
title: Använd skiftläge
seo-title: Använd skiftläge
description: Använd skiftläge
seo-description: null
page-status-flag: never-activated
uuid: d4c76fdf-d562-4151-93ec-08b4f6563440
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: fbc38e33-60a6-4d21-a598-312293d168fb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Använd skiftläge{#use-case}

## Skapa ett filter för e-postformat för prenumeranter {#creating-a-filter-on-the-email-format-of-subscribers}

I det här exemplet visas hur du skapar ett filter för att sortera nyhetsbrevsprenumerationer baserat på mottagarnas e-postformat.

För att göra detta måste vi använda en fördefinierad filhanterare: Dessa filter är länkade till en dokumenttyp och nås via **[!UICONTROL Administration > Configuration > Predefined filters]** noden. Dessa datafilter kan användas för varje typ av redigerare (eller dokument) i programmet.

Datafilter skapas på samma sätt som fördefinierade filter, men det finns ytterligare ett fält där du kan välja dokumenttypen som filtret ska tillämpas på.

Använd följande steg:

1. Skapa ett nytt filter via **[!UICONTROL Administration > Configuration > Predefined filters]** noden.
1. Klicka på **[!UICONTROL Select link]** ikonen för att markera det aktuella dokumentet:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Markera prenumerationsschemat (nms:subscription) och klicka på **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Klicka **[!UICONTROL Edit link]** för att visa fälten i det markerade dokumentet.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Du kan sedan visa innehållet i det markerade dokumentet:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Du kan komma åt dessa fält för att definiera filtervillkor i filterredigerarens brödtext. Ett programfilter definieras på exakt samma sätt som ett avancerat filter. Se [Skapa ett avancerat filter](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Skapa ett nytt filter för prenumerationer som endast visar prenumerationer med ett odefinierat e-postformat:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Klicka **[!UICONTROL Save]** för att lägga till ett filter i de fördefinierade filtren för den här typen av lista.
1. Du kan nu använda det här filtret på fliken **[!UICONTROL Subscriptions]** i mottagarprofilen; Du öppnar filtret Okänt e-postformat genom att klicka på **[!UICONTROL Filters]** .

   ![](assets/s_ncs_user_filter_on_events.png)

   Namnet på det aktuella filtret visas ovanför listan. Klicka på **[!UICONTROL Delete this filter]** ikonen om du vill avbryta filtret.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)

