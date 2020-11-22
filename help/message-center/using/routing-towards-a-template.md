---
solution: Campaign Classic
product: campaign
title: Routning mot en mall
description: Routning mot en mall
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 9%

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
