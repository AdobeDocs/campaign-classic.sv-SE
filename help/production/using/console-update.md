---
solution: Campaign Classic
product: campaign
title: Konsoluppdatering
description: Konsoluppdatering
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# Konsoluppdatering{#console-update}

Om du valde alternativet **[!UICONTROL Do not request console update]** och vill återaktivera uppdateringsbegäran gör du så här:

1. Öppna redigeraren för registerdatabasen med kommandot **regedit** i Windows **[!UICONTROL Start > Execute]**-menyn.

   ![](assets/ncs_console_update_1.png)

1. Visa alternativen för noden **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** i trädet.
1. Ta bort **[!UICONTROL confAdvisedUpgrade]**-posten och stäng Registereditorn.

   ![](assets/ncs_console_update_2.png)

