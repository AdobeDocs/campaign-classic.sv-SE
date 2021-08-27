---
product: campaign
title: Programobjekt
description: Programobjekt
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---

# Programobjekt{#application-objects}

![](../../assets/v7-only.svg)

Inbyggda objekt bör övervakas och det är viktigt att förhindra att de växer för mycket.

## Sekvens med ID:n {#sequence-of-ids}

Adobe Campaign använder en ID-sekvens som måste användas i enlighet med detta: **xtkNewId**. Om sekvensen konsumeras mycket snabbt (t.ex. från 100 000 per dag) måste du kontrollera att den överensstämmer med dina affärskrav, t.ex. skicka miljontals e-postmeddelanden per dag. Det går att definiera en dedikerad sekvens för särskilda tabeller. Du kan konfigurera ett arbetsflöde för att övervaka ID-användningen.

När sekvensen når över 2 miljarder (2 147 483 648 är det exakta talet) återgår den till noll. Det måste undvikas och skapar problem, och därför måste den här sekvensen övervakas.

Du kan förhindra detta med stora tabeller genom att använda en viss sekvens. Detta kan göras med attributet **pkSequence** i schemat.

Högfrekventa arbetsflöden som skapar många loggar kommer att ta många ID:n i anspråk. Vi rekommenderar därför att du undviker alltför många loggar och höga frekvenser i arbetsflöden.

Om sekvensen redan har cyklats är den bästa lösningen att växla till negativa ID:n, från -2 147 483 648.

## Mappar {#folders}

Det får inte finnas fler än 1 000 mappar i någon instans. Om du har fler mappar än detta kan det orsaka prestandaproblem med Campaign-klienten. Du kan ställa in ett övervakningsjobb för att räkna antalet mappar, arbetsflöden osv. och rapportera tillbaka regelbundet.

Den här metoden markerar även användare som skapar för många objekt.

## Leveranser {#deliveries}

Det får inte finnas fler än 1000 leveranser på instansen när som helst. Många leveranser förbrukar databasutrymme och skapar problem. En instans som skapar mer än 10 leveranser per dag måste kontrolleras mot affärsbehoven. Överväg att använda kontinuerliga leveranser för att skapa färre leveranser. Mer information om detta finns i [det här avsnittet](../../workflow/using/continuous-delivery.md).

Leveranser som är äldre än två år ska rensas från instansen.

## Filer {#files}

Antalet filer på programserverdisken bör inte öka i oändlighet.

Importera arbetsflöden skapar filer och orsakar därför diskexpansion. Detta kan förhindras genom att använda standardaktiviteten [Filinsamlare](../../workflow/using/file-collector.md). Filinsamlaren flyttar filer till en tillfällig mapp och tömmer dem automatiskt.

Om ett arbetsflöde importerar filer och inte använder standardfunktionerna måste det rensas för att diskutrymmet ska bli så litet som möjligt.

## Transaktionsdata och transaktionsloggar {#transactional-data-and-logs}

Varje [arbetsflöde](../../workflow/using/data-life-cycle.md#work-table) som importerar data till Adobe Campaign gör att databasens storlek ökar.

Kontrollera att arbetsflödena för rensning eller tömning körs och att posterna effektivt rensas. Alla transaktionsdata och loggar måste rensas. Rensningsaktiviteten rensar endast standardtabellerna: spårning och breda loggar. Specifika tabeller måste rensas av specifika arbetsflöden. Se [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

Håll utkik efter åldersfördelade transaktionsdata genom att kontrollera det äldsta skapandedatumet för posterna.
