---
product: campaign
title: Spåra loggproblem
description: Spåra loggproblem
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Spåra loggproblem{#tracking-logs-issues}



Det kan finnas flera orsaker till att loggar inte vidarebefordras. Vi rekommenderar att du kontrollerar följande information:

* **Har arbetsflödet** Spårning **fel?**

  Se [Övervaka tekniska arbetsflöden](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **Kör modulen** trackinglog **på servern?**

  Se [Loggfiler](../../production/using/log-files.md).

* **Har ändringar gjorts?**

  De kan utlösa en förlust av anslutningen till servrarna med hjälp av spårningsaliaset.
