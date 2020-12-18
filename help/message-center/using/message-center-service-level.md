---
solution: Campaign Classic
product: campaign
title: Tjänstenivå för meddelandecentret
description: Tjänstenivå för meddelandecentret
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 5%

---


# Tjänstenivå för meddelandecentret{#message-center-service-level}

Den här rapporten innehåller leveransstatistik för transaktionsmeddelanden samt felinformation. Du kan klicka på en feltyp för att visa information om den. Den här rapporten, som riktar sig till tekniska administratörer, kan också nås via **[!UICONTROL Monitoring]**-universum i kontrollinstansen.

![](assets/mc_reports_1.png)

I den här rapporten kan du välja att visa den övergripande statistiken eller den som är relativ till en viss körningsinstans. Du kan också filtrera data efter kanal och under en viss period. Indikatorerna som visas i avsnittet **[!UICONTROL Indicators over the period]** beräknas för den valda perioden:

* **[!UICONTROL Incoming (throughput event/h)]** : genomsnittligt antal händelser per timme som anges i Message Center-kön.
* **[!UICONTROL Incoming (event vol)]** : antal händelser som anges i Message Center-kön.
* **[!UICONTROL Outgoing (throughput msg/h)]** : Genomsnittligt antal utgående Message Center-händelser per timme (skickas av en leverans).
* **[!UICONTROL Outgoing (msg vol)]** : Antal slutförda utgående Message Center-händelser (skickade av en leverans).
* **[!UICONTROL Average sending time (seconds)]** : Genomsnittlig tid i meddelandecentret för lyckade bearbetade händelser. Beräkningen tar hänsyn till bearbetningstiden och den maximala sändningstiden.
* **[!UICONTROL Error rate]** : antal händelser med fel jämfört med antalet händelser som har angetts i Message Center-kön. Följande fel beaktas: routningsfel, utgången händelse (händelse som har varit i kön för lång), leveransfel, ignoreras av leveransen (karantän, osv.).

>[!NOTE]
>
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i distributionsguiden. Se [Övervakningströsklar](../../message-center/using/monitoring-thresholds.md).

