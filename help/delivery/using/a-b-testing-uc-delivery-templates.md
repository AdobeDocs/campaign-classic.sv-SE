---
product: campaign
title: Skapa leveransmallarna
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
role: User
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 15%

---

# AB-testning: Skapa leveransmallar {#step-3--creating-two-delivery-templates}

Vi vill nu skapa två leveransmallar. Varje mall refereras i en **[!UICONTROL Email delivery]** aktivitet länkad till **[!UICONTROL Split]** aktivitet. Mer information om detta finns i [det här avsnittet](about-templates.md).

1. Gå till **[!UICONTROL Resources > Delivery template]** mapp.
1. Duplicera **[!UICONTROL Email]** leveransmall.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Skapa innehållet som ska användas för leverans A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Upprepa den här processen om du vill skapa en mall för leverans B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Du kan nu konfigurera leveranser i arbetsflödet. [Läs mer](a-b-testing-uc-configuring-deliveries.md).
