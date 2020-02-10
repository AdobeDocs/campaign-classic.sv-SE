---
title: Använda tabellen Adobe Campaign Classic-mottagare
description: Lär dig hur du använder den färdiga mottagartabellen i Adobe Campaign Classic när du utformar din datamodell.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Använda standardmottagartabellen{#default-recipient-table}

Den körklara mottagartabellen i Adobe Campaign är en bra startpunkt för att skapa din datamodell. Den har ett antal fördefinierade fält och tabelllänkar som enkelt kan utökas. Detta är särskilt användbart när du främst riktar dig till mottagare, eftersom det passar en enkel mottagarorienterad datamodell.

Fördelarna med att använda den vanliga mottagartabellen är följande:

* Arbeta direkt med funktioner som prenumerationer, listor, undersökningar, sociala medier och så vidare.
* Tillhandahåller en marknadsföringsdatabas med en mottagarcentrerad datamodell.
* Snabbare implementering.
* Enkelt underhåll av support och partners.

Det går dock att utöka mottagartabellen, men inte att minska antalet fält eller länkar i tabellen.

>[!IMPORTANT]
>
>Vi rekommenderar att du inte tar bort fält (även om de är oanvändbara) i mottagartabellen eftersom det kan leda till fel i de inbyggda modulerna.

Och eftersom mottagartabellen är en del av produkten utvecklas både tabellen och dess tillhörande form allt eftersom produkten ändras. Det krävs därför extra underhåll för att kontrollera att eventuella tillägg fortfarande är giltiga vid uppgraderingen.
