---
product: campaign
title: Spåra loggproblem
description: Spåra loggproblem
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
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
