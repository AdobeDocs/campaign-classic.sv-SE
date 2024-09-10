---
product: campaign
title: Tjänstenivå för meddelandecentret
description: Läs mer i rapporten om servicenivån i meddelandecentret
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# Tjänstenivå för meddelandecentret {#message-center-service-level}



Den här rapporten innehåller leveransstatistik för transaktionsmeddelanden samt felinformation. Du kan klicka på en feltyp för att visa information om den.

Den här rapporten, som riktar sig till tekniska administratörer, kan också nås via fliken **[!UICONTROL Monitoring]** i kontrollinstansen.

![](assets/mc_reports_1.png)

I den här rapporten kan du välja att visa den övergripande statistiken eller den som är relativ till en viss körningsinstans. Du kan också filtrera data efter kanal och under en viss period.

Indikatorerna som visas i avsnittet **[!UICONTROL Indicators over the period]** beräknas för den valda perioden:

* **[!UICONTROL Incoming (throughput event/h)]** : genomsnittligt antal händelser per timme som anges i meddelandecenterkön.
* **[!UICONTROL Incoming (event vol)]** : antal händelser har angetts i meddelandecenterkön.
* **[!UICONTROL Outgoing (throughput msg/h)]** : genomsnittligt antal utgående Message Center-händelser per timme (skickas av en leverans).
* **[!UICONTROL Outgoing (msg vol)]** : antal slutförda utgående Message Center-händelser (skickade av en leverans).
* **[!UICONTROL Average sending time (seconds)]** : Genomsnittlig tid i meddelandecentret för slutförda händelser. Beräkningen tar hänsyn till bearbetningstiden och den maximala sändningstiden.
* **[!UICONTROL Error rate]** : antal händelser med fel jämfört med antalet händelser som har öppnats i Message Center-kön. Följande fel beaktas: routningsfel, utgångna händelser (händelse som har varit i kön för lång), leveransfel, ignoreras av leveransen (karantän, osv.).

>[!NOTE]
>
>Tröskelvärdena för varningsmeddelanden (orange) och varningsmeddelanden (röda) kan konfigureras i distributionsguiden. Se [Skärmtröskelvärden](../../message-center/using/additional-configurations.md#monitoring-thresholds).
