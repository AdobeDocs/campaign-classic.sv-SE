---
title: Händelsesamling
seo-title: Händelsesamling
description: Händelsesamling
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Händelsesamling{#event-collection}

Händelser som genereras av informationssystemet kan samlas in på två sätt:

* anrop till SOAP-metoder gör att du kan skicka händelser i Adobe Campaign: Med metoden PushEvent kan du skicka en händelse i taget. Med metoden PushEvents kan du skicka flera händelser samtidigt. Se [Händelsebeskrivning](../../message-center/using/event-description.md).
* genom att skapa ett arbetsflöde kan du återställa händelser genom att importera filer eller via en SQL-gateway (med alternativet **Federated Data Access** ).

När de har samlats in delas händelser upp, efter tekniska arbetsflöden, mellan realtids- och batchköer för körningsinstanserna, i väntan på att länkas till en meddelandemall.

![](assets/messagecenter_events_queues_001.png)

