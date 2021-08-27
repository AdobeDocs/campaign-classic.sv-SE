---
product: campaign
title: Konsoluppdatering
description: Konsoluppdatering
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Konsoluppdatering{#console-update}

![](../../assets/v7-only.svg)

Om du valde alternativet **[!UICONTROL Do not request console update]** och vill återaktivera uppdateringsbegäran gör du så här:

1. Öppna redigeraren för registerdatabasen med kommandot **regedit** i Windows **[!UICONTROL Start > Execute]**-menyn.

   ![](assets/ncs_console_update_1.png)

1. Visa alternativen för noden **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** i trädet.
1. Ta bort **[!UICONTROL confAdvisedUpgrade]**-posten och stäng Registereditorn.

   ![](assets/ncs_console_update_2.png)
