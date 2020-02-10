---
title: Bearbetningstid för meddelandecenter
seo-title: Bearbetningstid för meddelandecenter
description: Bearbetningstid för meddelandecenter
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Bearbetningstid för meddelandecenter{#message-center-processing-time}

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
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i distributionsguiden för Adobe Campaign. Se [Övervakningströsklar](../../message-center/using/monitoring-thresholds.md).

