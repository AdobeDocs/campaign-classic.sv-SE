---
title: Åtkomst till en extern databas
seo-title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Använda data från en extern databas i ett arbetsflöde {#using-data-from-an-external-database-in-a-workflow}

I flera arbetsflödesaktiviteter i Adobe Campaign kan du använda data som lagras i en extern databas.

## Filtrera externa data {#filtering-on-external-data}

Med frågeaktiviteten kan du lägga till externa data och använda dem i definierade filterkonfigurationer.

Mer information finns i avsnittet [Fråga](../../workflow/using/targeting-data.md#selecting-data) .

## Skapa delmängder {#creating-sub-sets}

Med den delade aktiviteten kan du skapa delmängder. Du kan använda externa data för att definiera de filtervillkor som ska användas.

Mer information finns i avsnittet [Dela](../../workflow/using/split.md) .

## Läser in extern databas {#loading-external-database}

Du kan använda externa data i datainläsningen (RDBMS). Den här aktiviteten visas i avsnittet [Datainläsning](../../workflow/using/data-loading--rdbms-.md) .

## Lägga till information och länkar {#adding-information-and-links}

Med hjälp av anrikningsaktiviteten kan du lägga till ytterligare data till arbetsflödets arbetstabell samt länkar till en extern tabell. Därför kan den utnyttja data från en extern databas. Den här aktiviteten presenteras i [anrikningsavsnittet](../../workflow/using/enrichment.md) .
