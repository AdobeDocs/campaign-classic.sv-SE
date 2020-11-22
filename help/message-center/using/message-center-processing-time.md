---
solution: Campaign Classic
product: campaign
title: Bearbetningstid för meddelandecentret
description: Bearbetningstid för meddelandecentret
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---


# Bearbetningstid för meddelandecentret{#message-center-processing-time}

Den här rapporten innehåller de viktigaste indikatorerna för realtidskön. Denna rapport, som riktar sig till tekniska administratörer, kan också nås via **[!UICONTROL Monitoring]** universum i kontrollinstansen.

![](assets/mc_reports_2.png)

Precis som för **[!UICONTROL Message Center service level]** rapporten kan du välja att visa den övergripande statistiken eller den som är relativ till en viss körningsinstans. Du kan också filtrera data efter kanal och under en viss period. Indikatorerna som visas i **[!UICONTROL Indicators over the period]** avsnittet beräknas för den valda perioden:

* **[!UICONTROL Average queuing time]** : Genomsnittlig tid som har bearbetat händelser som har ägnats åt i meddelandecentret. Endast bearbetningstiden beaktas.
* **[!UICONTROL Average message sending time (s)]** : Genomsnittlig tid som har bearbetat händelser som har ägnats åt i meddelandecentret. Endast den maximala leveranstiden beaktas.
* **[!UICONTROL Average processing time (s)]** : Genomsnittlig tid som har bearbetat händelser som har ägnats åt i meddelandecentret. Beräkningen tar hänsyn till bearbetningstiden och den maximala sändningstiden.
* **[!UICONTROL Maximum number of queued events]** : maximalt antal händelser i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Minimum number of queued events]** : minsta antal händelser som finns i Message Center-kön vid en given tidpunkt.
* **[!UICONTROL Average number of queued events]** : Genomsnittligt antal händelser i Message Center-kön vid en given tidpunkt.

>[!NOTE]
>
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i Adobe Campaign distributionsguide. Se [Övervakningströsklar](../../message-center/using/monitoring-thresholds.md).

