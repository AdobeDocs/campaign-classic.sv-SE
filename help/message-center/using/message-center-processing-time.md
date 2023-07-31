---
product: campaign
title: Bearbetningstid för meddelandecentret
description: Läs mer i rapporten om bearbetningstid för Message Center
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 4%

---

# Bearbetningstid för meddelandecentret {#message-center-processing-time}



Den här rapporten innehåller de viktigaste indikatorerna för realtidskön.

Denna rapport, som riktar sig till tekniska administratörer, kan också nås via **[!UICONTROL Monitoring]** på kontrollinstansen.

![](assets/mc_reports_2.png)

Precis som i **[!UICONTROL Message Center service level]** kan du välja att visa den övergripande statistiken eller den som är relativ till en viss körningsinstans. Du kan också filtrera data efter kanal och under en viss period.

Indikatorerna som visas i **[!UICONTROL Indicators over the period]** -avsnittet beräknas över den valda perioden:

* **[!UICONTROL Average queuing time]** : den genomsnittliga tid som händelser i meddelandecentret bearbetades. Endast bearbetningstiden beaktas.
* **[!UICONTROL Average message sending time (s)]** : den genomsnittliga tid som händelser i meddelandecentret bearbetades. Endast den maximala leveranstiden beaktas.
* **[!UICONTROL Average processing time (s)]** : den genomsnittliga tid som händelser i meddelandecentret bearbetades. Beräkningen tar hänsyn till bearbetningstiden och den maximala sändningstiden.
* **[!UICONTROL Maximum number of queued events]** : maximalt antal händelser i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Minimum number of queued events]** : minsta antal händelser i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Average number of queued events]** : genomsnittligt antal händelser i Message Center-kön vid en given tidpunkt.

>[!NOTE]
>
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i Adobe Campaign distributionsguide. Se [Skärmtrösklar](../../message-center/using/additional-configurations.md#monitoring-thresholds).
