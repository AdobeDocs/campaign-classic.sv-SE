---
solution: Campaign Classic
product: campaign
title: Konfigurerar populationsexempel
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 177b4e74c75e4fcca70dc90b5ff2c0406181e0f7
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 3%

---


# Konfigurerar populationsexempel {#step-2--configuring-population-samples}

## Konfigurera frågeaktiviteten {#configuring-the-query-activity}

* Dubbelklicka på aktiviteten **[!UICONTROL Query]**.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Klicka på länken **[!UICONTROL Edit query]** och välj de mottagare som du vill ange som mål.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Länka aktiviteten **[!UICONTROL Query]** till aktiviteten **[!UICONTROL Split]**.

   ![](assets/use_case_abtesting_createrecipients_003.png)

## Konfigurera den delade aktiviteten {#configuring-the-split-activity}

Med den här aktiviteten kan du skapa flera populationer: den som får A, den som får B, och den återstående befolkningen. Om du använder slumpmässig markering kan du bara rikta in dig på en del av populationen av varje leverans.

1. Skapar population A:

   * Dubbelklicka på aktiviteten **[!UICONTROL Split]**.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Ändra etiketten till A på den befintliga fliken.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Välj alternativet **[!UICONTROL Limit the selected records]**.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Klicka på länken **[!UICONTROL Edit]**, välj **[!UICONTROL Activate random sampling]** och klicka på **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Ange tröskelvärdet till 10 % och klicka sedan på **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Skapar population B:

   * Klicka på **[!UICONTROL Add]** för att skapa en ny flik för population B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Begränsa populationen till 10% som tidigare.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Skapar den återstående populationen:

   * Gå till fliken **[!UICONTROL General]**.

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Välj **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Ändra etiketten för att ange att den här populationen varken innehåller A eller B och klicka på **[!UICONTROL OK]** för att stänga aktiviteten.

      ![](assets/use_case_abtesting_createrecipients_013.png)
