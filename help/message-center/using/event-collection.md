---
solution: Campaign Classic
product: campaign
title: Händelsesamling
description: Händelsesamling
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# Händelsesamling{#event-collection}

Händelser som genereras av informationssystemet kan samlas in på två sätt:

* Anrop till SOAP-metoder gör att du kan skicka händelser i Adobe Campaign: Med metoden PushEvent kan du skicka en händelse i taget. Med metoden PushEvents kan du skicka flera händelser samtidigt. Se [Händelsebeskrivning](../../message-center/using/event-description.md).
* Om du skapar ett arbetsflöde kan du återställa händelser genom att importera filer eller via en SQL-gateway (med alternativet **Federated Data Access**).

När de har samlats in delas händelser upp, efter tekniska arbetsflöden, mellan realtids- och batchköer för körningsinstanserna, i väntan på att länkas till en meddelandemall.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>I körningsinstanserna får mapparna **[!UICONTROL Real time events]** eller **[!UICONTROL Batch events]** inte anges som vyer eftersom detta kan leda till problem med åtkomst. Mer information om hur du anger en mapp som en vy finns i [det här avsnittet](../../platform/using/access-management-folders.md).
