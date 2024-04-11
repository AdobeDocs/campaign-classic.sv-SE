---
product: campaign
title: Konfigurera populationsexempel
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: A/B Testing
role: User
exl-id: 1ca01cab-734a-4299-b112-04eec51222fb
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 2%

---

# AB-testning: Konfigurera populationsexempel {#step-2--configuring-population-samples}

## Konfigurera aktiviteten Fråga {#configuring-the-query-activity}

* Dubbelklicka på **[!UICONTROL Query]** aktivitet.

  ![](assets/use_case_abtesting_createrecipients_001.png)

* Klicka på **[!UICONTROL Edit query]** och markera de mottagare som du vill ange som mål.

  ![](assets/use_case_abtesting_createrecipients_002.png)

* Länka **[!UICONTROL Query]** till **[!UICONTROL Split]** aktivitet.

  ![](assets/use_case_abtesting_createrecipients_003.png)

## Konfigurera aktiviteten Dela {#configuring-the-split-activity}

Med den här aktiviteten kan du skapa flera populationer: den som får A, den som får B och den återstående populationen. Om du använder slumpmässig markering kan du bara rikta in dig på en del av populationen av varje leverans.

1. Skapar population A:

   * Dubbelklicka på **[!UICONTROL Split]** aktivitet.

     ![](assets/use_case_abtesting_createrecipients_004.png)

   * Ändra etiketten till A på den befintliga fliken.

     ![](assets/use_case_abtesting_createrecipients_005.png)

   * Välj **[!UICONTROL Limit the selected records]** alternativ.

     ![](assets/use_case_abtesting_createrecipients_006.png)

   * Klicka på **[!UICONTROL Edit]** länk, markera **[!UICONTROL Activate random sampling]** och klicka **[!UICONTROL Next]**.

     ![](assets/use_case_abtesting_createrecipients_007.png)

   * Ange tröskelvärdet till 10 % och klicka sedan på **[!UICONTROL Finish]**.

     ![](assets/use_case_abtesting_createrecipients_008.png)

1. Skapar population B:

   * Klicka **[!UICONTROL Add]** för att skapa en ny flik för population B.

     ![](assets/use_case_abtesting_createrecipients_009.png)

   * Begränsa populationen till 10% som tidigare.

     ![](assets/use_case_abtesting_createrecipients_010.png)

1. Skapar den återstående populationen:

   * Gå till **[!UICONTROL General]** -fliken.

     ![](assets/use_case_abtesting_createrecipients_011.png)

   * Välj **[!UICONTROL Generate complement]**.

     ![](assets/use_case_abtesting_createrecipients_012.png)

   * Ändra etiketten för att ange att den här populationen varken innehåller A eller B och klicka på **[!UICONTROL OK]** för att stänga aktiviteten.

     ![](assets/use_case_abtesting_createrecipients_013.png)

Nu kan du skapa de två leveransmallarna. [Läs mer](a-b-testing-uc-delivery-templates.md)).
