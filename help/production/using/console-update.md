---
title: Konsoluppdatering
seo-title: Konsoluppdatering
description: Konsoluppdatering
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Konsoluppdatering{#console-update}

Om du har valt alternativet och vill återaktivera uppdateringsbegäran gör du så här: **[!UICONTROL Do not request console update]**

1. Öppna redigeraren för registerdatabasen med kommandot **regedit** på Windows- **[!UICONTROL Start > Execute]** menyn.

   ![](assets/ncs_console_update_1.png)

1. Visa alternativen för **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** noden i trädet.
1. Ta bort **[!UICONTROL confAdvisedUpgrade]** posten och stäng Registereditorn.

   ![](assets/ncs_console_update_2.png)

