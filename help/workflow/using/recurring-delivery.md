---
product: campaign
title: Återkommande leverans
description: Läs mer om arbetsflödesaktiviteten Återkommande leverans
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 198921813ff097db0d4ba0a8203fef65bb591af7
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 12%

---

# Återkommande leverans{#recurring-delivery}

A **[!UICONTROL Recurring delivery]** Med -aktivitet kan du konfigurera en förekomst av en leveransmall som är specifik för en kampanj.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#recurring-delivery-video)

Den här aktiviteten är bara tillgänglig från **[!UICONTROL Targeting and workflows]** som finns i en kampanj.

Så här gör du:

1. Välj den leveransmall som aktiviteten ska baseras på.

   ![](assets/recurring_delivery_001.png)

1. Konfigurera leveransmallen.

Konfigurationsprocessen för den här aktiviteten liknar den för att skapa en leveransmall utifrån tillgängliga alternativ. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/about-templates.md).

>[!CAUTION]
>
>Återkommande leveranser stöder inte utskick av korrektur, inklusive [måldata](../../workflow/using/data-life-cycle.md#target-data) personaliseringselement.

Ett exempel på den här aktiviteten som används finns i [section](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Så här ställer du in återkommande leverans {#set-up-recurring-delivery}

A **återkommande leverans** skapar en ny leveransinstans varje gång den körs. Om arbetsflödet till exempel är schemalagt att köras en gång i veckan resulterar det i 52 leveranser efter ett år. Det innebär också att de breda loggarna och spårningsloggarna separeras av varje leveransinstans.

![Återkommande leverans](assets/delivery_recurring.jpg)

Om du vill stoppa en återkommande leverans från att köras bör du helt avbryta kampanjen eller stoppa arbetsflödet som körs. Om du stoppar leveransen från kontrollpanelen för Campaign kommer leveransförekomsten endast att stoppas: nästa instans av den återkommande leveransen kommer att fortsätta skapas vid varje arbetsflödeskörning.

>[!NOTE]
>
>Det går inte att skicka ett bevis från en **[!UICONTROL Recurring delivery]** typaktivitet.
> 
>Om du vill skapa en leverans direkt via ett kampanjarbetsflöde använder du de kanalspecifika aktiviteter som är förkonfigurerade (t.ex. **[!UICONTROL Recurring delivery]**).

## Självstudievideo {#recurring-delivery-video}

I den här videon förklaras hur du konfigurerar en återkommande leverans och en schemaläggningsaktivitet.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

Det finns fler videor med Campaign Classic om hur man gör [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
