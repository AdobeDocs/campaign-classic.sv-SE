---
product: campaign
title: Avinstallerar Campaign
description: Lär dig avinstallera Campaign
feature: Installation
audience: installation
content-type: reference
hide: true
hidefromtoc: true
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 49f6ffe4f78cbd790fb27ac6250f4bd7e3bc9e68
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 2%

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

Se den här [sidan](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Glöm inte att ta bort installationsmappen för Campaign.
