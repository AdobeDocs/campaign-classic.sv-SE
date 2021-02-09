---
solution: Campaign Classic
product: campaign
title: Skapa ett målarbetsflöde
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 9%

---


# Skapa ett målarbetsflöde {#step-1--creating-a-targeting-workflow}

Du måste skapa ett arbetsflöde på fliken **[!UICONTROL Targeting and Workflows]** i en kampanj. Den består av en **[!UICONTROL Query]**-aktivitet, en **[!UICONTROL Split]**-aktivitet som är länkad till två **[!UICONTROL Email delivery]**-aktiviteter, en **[!UICONTROL Wait]**-aktivitet, en **[!UICONTROL JavaScript code]**-aktivitet och en **[!UICONTROL Delivery]**-aktivitet.

1. Om du inte redan har gjort det skapar du en kampanj (mer information finns i [avsnittet](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gå till fliken **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Ändra etiketten för det befintliga arbetsflödet eller klicka på **[!UICONTROL Add]** för att skapa en ny (mer information finns i [avsnittet](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Använd musen för att dra och släppa aktiviteter i arbetsflödesdiagrammet, inklusive en **[!UICONTROL Query]** (**[!UICONTROL Target]**-flik), en **[!UICONTROL Split]** (**[!UICONTROL Target]**-flik), två **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]**-flik), en **[!UICONTROL Wait]**-aktivitet (**[!UICONTROL Flow Control]**-flik), en **[!UICONTROL JavaScript code]**-aktivitet (**[!UICONTROL Actions]**) och en &lt;a &lt;a10///// > aktivitet (**[!UICONTROL Actions]**-flik).**[!UICONTROL Delivery]**

![](assets/use_case_abtesting_targetwkfl_004.png)
