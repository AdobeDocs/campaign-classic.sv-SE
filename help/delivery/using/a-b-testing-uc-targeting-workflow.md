---
product: campaign
title: Skapa ett molninriktat arbetsflöde
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# Skapa ett målinriktat arbetsflöde {#step-1--creating-a-targeting-workflow}

Du måste skapa ett arbetsflöde på fliken **[!UICONTROL Targeting and Workflows]** i en kampanj. Den består av en **[!UICONTROL Query]**-aktivitet, en **[!UICONTROL Split]**-aktivitet som är länkad till två **[!UICONTROL Email delivery]**-aktiviteter, en **[!UICONTROL Wait]**-aktivitet, en **[!UICONTROL JavaScript code]**-aktivitet och en **[!UICONTROL Delivery]**-aktivitet.

1. Om du inte redan har gjort det skapar du en kampanj (mer information finns i [det här avsnittet](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gå till fliken **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Ändra etiketten för det befintliga arbetsflödet eller klicka på **[!UICONTROL Add]** för att skapa en ny (mer information finns i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Använd musen för att dra och släppa aktiviteter i arbetsflödesdiagrammet, inklusive en **[!UICONTROL Query]** (**[!UICONTROL Target]**-flik), en **[!UICONTROL Split]** (**[!UICONTROL Target]**-flik), två **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]**-flik), en **[!UICONTROL Wait]**-aktivitet (**[!UICONTROL Flow Control]**-flik), en **[!UICONTROL JavaScript code]**-aktivitet (**[!UICONTROL Actions]**) och en &lt;a &lt;a10///// > aktivitet (**[!UICONTROL Actions]**-flik).**[!UICONTROL Delivery]**

![](assets/use_case_abtesting_targetwkfl_004.png)

Du kan nu konfigurera populationsexemplen. [Läs mer](a-b-testing-uc-population-samples.md).
