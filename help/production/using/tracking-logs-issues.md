---
solution: Campaign Classic
product: campaign
title: Spåra loggproblem
description: Spåra loggproblem
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: f24642223a2ec9f3d8e78e2f7e71a55bf14b80c7
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# Spåra loggproblem{#tracking-logs-issues}

Det kan finnas flera orsaker till att loggar inte vidarebefordras. Vi rekommenderar att du kontrollerar följande information:

* **Har****spårningsarbetsflödet fel?**

   Se [Övervaka tekniska arbetsflöden](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Är modulen****trackinglogg på servern?**

   Se [Loggfiler](../../production/using/log-files.md).

* **Har ändringar gjorts?**

   De kan utlösa en förlust av anslutningen till servrarna med hjälp av spårningsaliaset.
