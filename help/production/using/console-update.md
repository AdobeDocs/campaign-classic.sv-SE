---
product: campaign
title: Konsoluppdatering
description: Konsoluppdatering
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 20%

---

# Konsoluppdatering{#console-update}



Om du valde **[!UICONTROL Do not request console update]** och du vill återaktivera uppdateringsbegäran gör du så här:

1. Öppna redigeraren för registerdatabasen med **regedit** i Windows **[!UICONTROL Start > Execute]** -menyn.

   ![](assets/ncs_console_update_1.png)

1. Visa alternativen för **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nod.
1. Ta bort **[!UICONTROL confAdvisedUpgrade]** och stäng Registereditorn.

   ![](assets/ncs_console_update_2.png)
