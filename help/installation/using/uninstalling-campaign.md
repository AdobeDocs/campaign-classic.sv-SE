---
solution: Campaign Classic
product: campaign
title: Avinstallerar Campaign
description: Lär dig hur du avinstallerar Campaign
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 13%

---


# Avinstallerar Campaign{#uninstalling-campaign}

>[!CAUTION]
>
>Dessa procedurer avinstallerar Adobe Campaign permanent. Alla data kommer att gå förlorade.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Refer to this [page](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Glöm inte att ta bort installationsmappen för Campaign.
