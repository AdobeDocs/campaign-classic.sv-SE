---
product: campaign
title: Konfigurera leveranser
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Konfigurera leveranser i arbetsflödet {#step-4--configuring-the-deliveries-in-the-workflow}

![](../../assets/common.svg)

Once [populations are created](a-b-testing-uc-population-samples.md), you can configure the deliveries. In this use case, the first two deliveries enable you to send different contents to population A and B. The third delivery is the fall-back delivery: it will be sent to the recipients who do not belong to A nor B. Its content will be calculated by a script and will be identical to either A or B, depending on which one scored the highest open rate. Vi måste konfigurera en vänteperiod för den tredje leveransen för att ta reda på resultatet av leveranserna A och B. Det är därför den tredje leveransen innehåller **[!UICONTROL Wait]** aktivitet.

1. Go to the **[!UICONTROL Split]** activity and link the transition destined for population A to one of the email deliveries already in the workflow.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Double-click the delivery to open it.
1. Using the drop-down list, select the template for delivery A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Click **[!UICONTROL Continue]** to view the delivery, then save it.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Länka övergången för **[!UICONTROL Split]** aktivitet avsedd för population B till den andra e-postleveransen.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Öppna leveransen, välj mallen i leverans B och spara sedan leveransen.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Länka övergången som är avsedd för den återstående populationen till **[!UICONTROL Wait]** aktivitet.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Open the **[!UICONTROL Wait]** activity and configure a 5-day waiting period.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Link the **[!UICONTROL Wait]** activity to the **[!UICONTROL JavaScript code]** activity.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Nu kan du skapa skriptet. [Läs mer](a-b-testing-uc-script.md).
