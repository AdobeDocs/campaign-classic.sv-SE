---
title: Typer av leveranser
seo-title: Typer av leveranser
description: Typer av leveranser
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# Typer av leveranser{#types-of-deliveries}

Det finns tre typer av leveransobjekt i Campaign:

## Enskild leverans {#single-delivery}

En **leverans** är ett fristående leveransobjekt som körs en gång. Den kan dupliceras, förberedas på nytt, men så länge den är i det slutliga tillståndet (avbryts, stoppas, slutförd) kan den inte återanvändas.

Leveranser kan skapas antingen i listan över leveranser eller i ett arbetsflöde via en [leveransaktivitet](../../workflow/using/delivery.md) .

Arbetsflödena innehåller också specifika leveransaktiviteter beroende på vilken typ av kanal du vill använda. Mer information om dessa aktiviteter finns i [det här avsnittet](../../workflow/using/cross-channel-deliveries.md).

## Återkommande leverans {#recurring-delivery}

Med en **återkommande leverans** kan du skapa en ny leverans varje gång aktiviteten körs. På så sätt slipper du skapa en ny leverans för återkommande uppgifter.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du 12 leveranser efter ett år.

Återkommande leveranser skapas i arbetsflöden via aktiviteten [Återkommande leverans](../../workflow/using/recurring-delivery.md). Ett exempel på den här aktiviteten visas i det här avsnittet: [Skapa en återkommande leverans i ett målarbetsflöde](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Kontinuerlig leverans {#continuous-delivery}

Med en **kontinuerlig leverans** kan du lägga till nya mottagare till en befintlig leverans, vilket innebär att du slipper skapa en ny leverans varje gång den körs.

Om en information i leveransen ändras (innehåll, namn osv.) skapas ett nytt leveransobjekt vid leveranskörningen. Om ingen information ändrades återanvänds samma leveransobjekt och leverans- och spårningsloggarna läggs till i samma objekt.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du en leverans efter ett år (förutsatt att du inte har ändrat leveransen).

Kontinuerliga leveranser skapas i arbetsflöden via aktiviteten [](../../workflow/using/continuous-delivery.md)Kontinuerlig leverans.
