---
title: Routning mot en mall
seo-title: Routning mot en mall
description: Routning mot en mall
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 12%

---


# Routning mot en mall{#routing-towards-a-template}

När meddelandemallen har publicerats på körningsinstansen/körningsinstanserna genereras automatiskt två mallar som ska länkas till en realtid eller en batchhändelse. Vägningssteget består av att länka en händelse till rätt meddelandemall. Länkningen baseras på händelsetypen som anges i egenskaperna för själva händelsen och mallens egenskaper.

Definition av händelsetypen i händelseegenskaperna:

![](assets/messagecenter_event_type_001.png)

Definition av händelsetypen i meddelandemallens egenskaper:

![](assets/messagecenter_event_type_002.png)

Som standard baseras routningen på följande information:

* Händelsetypen
* Den kanal som ska användas (som standard: e-post)
* Den senaste leveransmallen, baserad på publiceringsdatumet
