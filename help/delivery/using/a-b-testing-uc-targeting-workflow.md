---
product: campaign
title: Skapa ett målinriktat arbetsflöde
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# Skapa ett målinriktat arbetsflöde {#step-1--creating-a-targeting-workflow}



Du måste skapa arbetsflödet i **[!UICONTROL Targeting and Workflows]** -fliken i en kampanj. Den består av en **[!UICONTROL Query]** aktivitet, **[!UICONTROL Split]** aktivitet länkad till två **[!UICONTROL Email delivery]** verksamhet, **[!UICONTROL Wait]** aktivitet, **[!UICONTROL JavaScript code]** aktivitet och **[!UICONTROL Delivery]** aktivitet.

1. Om du inte redan har gjort det skapar du en kampanj (mer information om detta finns i [det här avsnittet](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gå till fliken **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Ändra etiketten för det befintliga arbetsflödet eller klicka på **[!UICONTROL Add]** om du vill skapa en ny (mer information om detta finns i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Använd musen för att dra och släppa aktiviteter i arbetsflödesdiagrammet, inklusive en **[!UICONTROL Query]** (**[!UICONTROL Target]** tabba), **[!UICONTROL Split]** (**[!UICONTROL Target]** tabbtangent), två **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tabba), **[!UICONTROL Wait]** aktivitet (**[!UICONTROL Flow Control]** tabba), **[!UICONTROL JavaScript code]** aktivitet (**[!UICONTROL Actions]** tabbtangenten) och **[!UICONTROL Delivery]** aktivitet (**[!UICONTROL Actions]** -fliken).

![](assets/use_case_abtesting_targetwkfl_004.png)

Du kan nu konfigurera populationsexemplen. [Läs mer](a-b-testing-uc-population-samples.md).
