---
solution: Campaign Classic
product: campaign
title: Spåra loggproblem
description: Spåra loggproblem
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# Spåra loggproblem{#tracking-logs-issues}

Det kan finnas flera orsaker till att loggar inte vidarebefordras. Vi rekommenderar att du kontrollerar följande information:

* Har arbetsflödet för **spårning** fel?

   Se [Övervaka tekniska arbetsflöden](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* Körs modulens **spårningslogg** på servern?

   Se [Loggfiler](../../production/using/log-files.md).

* Har ändringar gjorts? De kan utlösa en förlust av anslutningen till servrarna med hjälp av spårningsaliaset.

