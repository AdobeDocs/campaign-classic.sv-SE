---
title: Spåra loggproblem
seo-title: Spåra loggproblem
description: Spåra loggproblem
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Spåra loggproblem{#tracking-logs-issues}

Det kan finnas flera orsaker till att loggar inte vidarebefordras. Vi rekommenderar att du kontrollerar följande information:

* Har arbetsflödet för **spårning** fel?

   Se [Övervaka tekniska arbetsflöden](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* Körs modulens **spårningslogg** på servern?

   Se [Loggfiler](../../production/using/log-files.md).

* Har ändringar gjorts? De kan utlösa en förlust av anslutningen till servrarna med hjälp av spårningsaliaset.

