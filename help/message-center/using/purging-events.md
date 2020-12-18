---
solution: Campaign Classic
product: campaign
title: Rensa händelser
description: Rensa händelser
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 6%

---


# Rensa händelser{#purging-events}

Du kan använda distributionsguiden för att konfigurera hur länge data ska lagras i databasen.

Händelserensning utförs automatiskt av arbetsflödet **[!UICONTROL Database cleanup]**. Det här arbetsflödet tömmer händelser som tagits emot och lagrats på körningsinstanser och händelser som arkiverats på en kontrollinstans.

Använd pilarna för att ändra inställningarna för tömning.

Inställningar för händelserensning på en kontrollinstans:

![](assets/messagecenter_delete_events_001.png)

Inställningar för händelserensning på en körningsinstans:

![](assets/messagecenter_delete_events_002.png)

Mer information om arbetsflödet för databasrensning finns i [det här avsnittet](../../production/using/database-cleanup-workflow.md).
