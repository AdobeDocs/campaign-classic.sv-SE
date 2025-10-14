---
product: campaign
title: Skapa ett målinriktat arbetsflöde
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# AB-testning: Skapa ett arbetsflöde för målinriktning {#step-1--creating-a-targeting-workflow}

Du måste skapa ditt arbetsflöde på fliken **[!UICONTROL Targeting and Workflows]** i en kampanj. Den består av en **[!UICONTROL Query]**-aktivitet, en **[!UICONTROL Split]**-aktivitet som är länkad till två **[!UICONTROL Email delivery]**-aktiviteter, en **[!UICONTROL Wait]**-aktivitet, en **[!UICONTROL JavaScript code]**-aktivitet och en **[!UICONTROL Delivery]**-aktivitet.

1. Skapa en kampanj om du inte redan har gjort det. Mer information finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html){target=_blank}.

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Gå till fliken **[!UICONTROL Targeting and Workflows]**.

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Ändra etiketten för det befintliga arbetsflödet eller klicka på **[!UICONTROL Add]** om du vill skapa en ny (mer information finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html){target="_blank"}).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Använd musen för att dra och släppa aktiviteter i arbetsflödesdiagrammet, inklusive en **[!UICONTROL Query]** (**[!UICONTROL Target]** tab), en **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), två **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** tab), en **[!UICONTROL Wait]** activity (**[!UICONTROL Flow Control]** tab), en **[!UICONTROL JavaScript code]** activity (**[!UICONTROL Actions]** tab) och en **[!UICONTROL Delivery]** activity (**[!UICONTROL Actions]** tab).

![](assets/use_case_abtesting_targetwkfl_004.png)

Du kan nu konfigurera populationsexemplen. [Läs mer](a-b-testing-uc-population-samples.md).
