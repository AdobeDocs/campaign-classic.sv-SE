---
solution: Campaign Classic
product: campaign
title: Rensa händelser
description: Rensa händelser
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 6%

---


# Rensa händelser{#purging-events}

Du kan använda [distributionsguiden](../../production/using/database-cleanup-workflow.md#deployment-wizard) för att konfigurera hur länge data ska lagras i databasen.

Händelserensning utförs automatiskt av [arbetsflödet för databasrensning](../../production/using/database-cleanup-workflow.md). Det här arbetsflödet tömmer händelser som tagits emot och lagrats på körningsinstanser och händelser som arkiverats på en kontrollinstans.

Använd pilarna för att ändra inställningarna för tömning.

Inställningar för händelserensning på en kontrollinstans:

![](assets/messagecenter_delete_events_001.png)

Inställningar för händelserensning på en körningsinstans:

![](assets/messagecenter_delete_events_002.png)

Mer information om arbetsflödet för databasrensning finns i [det här avsnittet](../../production/using/database-cleanup-workflow.md).
