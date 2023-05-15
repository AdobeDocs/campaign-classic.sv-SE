---
product: campaign
title: Spåra loggproblem
description: Spåra loggproblem
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Spåra loggproblem{#tracking-logs-issues}



Det kan finnas flera orsaker till att loggar inte vidarebefordras. Vi rekommenderar att du kontrollerar följande information:

* **Gör** Spårning **Har arbetsflödet fel?**

   Se [Övervaka tekniska arbetsflöden](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Är modulen** trackinglogd **körs på servern?**

   Se [Loggfiler](../../production/using/log-files.md).

* **Har ändringar gjorts?**

   De kan utlösa en förlust av anslutningen till servrarna med hjälp av spårningsaliaset.
