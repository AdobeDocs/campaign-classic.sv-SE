---
product: campaign
title: Spåra loggproblem
description: Spåra loggproblem
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# Spåra loggproblem{#tracking-logs-issues}

![](../../assets/v7-only.svg)

Det kan finnas flera orsaker till att loggar inte vidarebefordras. Vi rekommenderar att du kontrollerar följande information:

* **Har****spårningsarbetsflödet fel?**

   Se [Övervaka tekniska arbetsflöden](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **Är modulen****trackinglogg på servern?**

   Se [Loggfiler](../../production/using/log-files.md).

* **Har ändringar gjorts?**

   De kan utlösa en förlust av anslutningen till servrarna med hjälp av spårningsaliaset.
