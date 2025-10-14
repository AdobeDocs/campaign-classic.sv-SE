---
product: campaign
title: Skapa leveransmallarna
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
role: User
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: A/B Testing
exl-id: 77b3a906-b76e-49e1-b524-b6f1ae537259
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 6%

---

# AB-testning: Skapa leveransmallar {#step-3--creating-two-delivery-templates}

Vi vill nu skapa två leveransmallar. Varje mall refereras i en **[!UICONTROL Email delivery]**-aktivitet som är länkad till **[!UICONTROL Split]**-aktiviteten. Se [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=sv-SE){target="_blank"}.

1. Gå till mappen **[!UICONTROL Resources > Delivery template]**.
1. Duplicera leveransmallen **[!UICONTROL Email]**.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Skapa innehållet som ska användas för leverans A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Upprepa den här processen om du vill skapa en mall för leverans B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

Du kan nu konfigurera leveranser i arbetsflödet. [Läs mer](a-b-testing-uc-configuring-deliveries.md).
