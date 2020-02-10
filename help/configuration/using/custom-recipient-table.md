---
title: Om datamodellen Adobe Campaign Classic
description: I det här dokumentet beskrivs grunderna i datamodellen för Adobe Campaign Classic.
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


# Använda en anpassad mottagartabell{#custom-recipient-table}

När du utformar din Adobe Campaign-datamodell kan du använda [den körklara mottagartabellen](../../configuration/using/default-recipient-table.md)eller välja att skapa en mottagartabell som inte är standard för att lagra dina marknadsföringsprofiler.

Om er datamodell inte passar den mottagarcentrerade strukturen kan ni skapa andra tabeller som målgruppsdimension i Adobe Campaign. Detta kan till exempel vara relevant när du behöver rikta in dig på hushåll, konton (som mobiltelefoner) och företag/webbplatser i stället för bara mottagare.

>[!NOTE]
>
>I så fall måste du skapa en ny [målmappning](../../configuration/using/target-mapping.md).

Alla principer och steg som behövs när du använder en anpassad mottagartabell beskrivs i det här [avsnittet](../../configuration/using/about-custom-recipient-table.md).

Fördelarna med att använda en anpassad mottagartabell är följande:

## Flexibel datamodell {#flexible-data-model}

Mottagartabellen är inte användbar om du inte behöver de flesta av mottagartabellfälten eller om datamodellen inte är mottagarcentrerad.

## Skalbarhet {#scalability}

Stora volymer kräver en effektiv tabell med få fält för en effektiv design. Den färdiga mottagartabellen skulle ha för många oanvändbara fält, vilket skulle kunna påverka prestanda och bristande effektivitet.

## Dataplats {#data-location}

Om data finns i en extern befintlig marknadsföringsdatabas kan det kräva för mycket arbete för att använda den körklara mottagartabellen. Det är enklare att skapa en ny som baseras på en befintlig struktur.

## Smidig migrering {#easy-migration}

Inget underhåll krävs för att kontrollera att alla tillägg fortfarande är giltiga vid uppgraderingen.

>[!IMPORTANT]
>
>Användningen av en anpassad mottagartabell är reserverad för avancerade användare och är begränsad. Mer information finns i det här avsnittet.
