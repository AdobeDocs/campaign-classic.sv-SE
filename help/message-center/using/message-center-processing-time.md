---
product: campaign
title: Bearbetningstid för meddelandecentret
description: Läs mer i rapporten om bearbetningstid för Message Center
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# Bearbetningstid för meddelandecentret {#message-center-processing-time}



Den här rapporten innehåller de viktigaste indikatorerna för realtidskön.

Den här rapporten, som riktar sig till tekniska administratörer, kan också nås via fliken **[!UICONTROL Monitoring]** i kontrollinstansen.

![](assets/mc_reports_2.png)

Precis som för rapporten **[!UICONTROL Message Center service level]** kan du välja att visa den övergripande statistiken eller den som är relativ till en viss körningsinstans. Du kan också filtrera data efter kanal och under en viss period.

Indikatorerna som visas i avsnittet **[!UICONTROL Indicators over the period]** beräknas för den valda perioden:

* **[!UICONTROL Average queuing time]** : Genomsnittlig tid som slutfördes utan fel i meddelandecentret. Endast bearbetningstiden beaktas.
* **[!UICONTROL Average message sending time (s)]** : Genomsnittlig tid som slutfördes utan fel i meddelandecentret. Endast den maximala leveranstiden beaktas.
* **[!UICONTROL Average processing time (s)]** : Genomsnittlig tid som slutfördes utan fel i meddelandecentret. Beräkningen tar hänsyn till bearbetningstiden och den maximala sändningstiden.
* **[!UICONTROL Maximum number of queued events]** : maximalt antal händelser i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Minimum number of queued events]** : minsta antal händelser i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Average number of queued events]** : genomsnittligt antal händelser i Message Center-kön vid en given tidpunkt.

>[!NOTE]
>
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i Adobe Campaign distributionsguide. Se [Skärmtröskelvärden](../../message-center/using/additional-configurations.md#monitoring-thresholds).
