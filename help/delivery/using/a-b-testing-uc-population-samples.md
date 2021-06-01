---
product: campaign
title: Konfigurera populationsexempel
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 6%

---

# Konfigurera populationsexempel {#step-2--configuring-population-samples}

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

Nu kan du skapa två leveransmallar (se [Steg 3: Skapa två leveransmallar](../../delivery/using/a-b-testing-uc-delivery-templates.md)).
