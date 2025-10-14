---
product: campaign
title: Spåra loggproblem
description: Spåra loggproblem
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 12%

---

# Spåra loggproblem{#tracking-logs-issues}



Det kan finnas flera orsaker till att loggar inte vidarebefordras. Vi rekommenderar att du kontrollerar följande information:

* **Har arbetsflödet** Spårning **fel?**

Se [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html){target="_blank"}.

![](assets/tracking_scheduled_task.png)

* **Kör modulen** trackinglog **på servern?**

  Se [Loggfiler](../../production/using/log-files.md).

* **Har ändringar gjorts?**

  De kan utlösa en förlust av anslutningen till servrarna med hjälp av spårningsaliaset.
