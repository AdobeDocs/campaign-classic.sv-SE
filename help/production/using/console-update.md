---
product: campaign
title: Konsoluppdatering
description: Konsoluppdatering
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Konsoluppdatering{#console-update}



Om du har valt alternativet **[!UICONTROL Do not request console update]** och vill återaktivera uppdateringsbegäran gör du så här:

1. Öppna redigeraren för registerdatabasen med kommandot **regedit** på Windows **[!UICONTROL Start > Execute]** -menyn.

   ![](assets/ncs_console_update_1.png)

1. Visa alternativen för noden **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** i trädet.
1. Ta bort posten **[!UICONTROL confAdvisedUpgrade]** och stäng Registereditorn.

   ![](assets/ncs_console_update_2.png)
