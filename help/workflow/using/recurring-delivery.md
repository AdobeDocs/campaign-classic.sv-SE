---
solution: Campaign Classic
product: campaign
title: Återkommande leverans
description: Läs mer om arbetsflödesaktiviteten Återkommande leverans
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 7%

---


# Återkommande leverans{#recurring-delivery}

Med en **[!UICONTROL Recurring delivery]** aktivitet kan du konfigurera en förekomst av en leveransmall som är specifik för en kampanj.

Den här aktiviteten är bara tillgänglig från fliken **[!UICONTROL Targeting and workflows]** som finns i en kampanj.

Så här gör du:

1. Välj den leveransmall som aktiviteten ska baseras på.

   ![](assets/recurring_delivery_001.png)

1. Konfigurera leveransmallen.

Konfigurationsprocessen för den här aktiviteten liknar den för att skapa en leveransmall utifrån tillgängliga alternativ. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/about-templates.md).

Ett exempel på den här aktiviteten finns i det här [avsnittet](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## Så här ställer du in återkommande leverans

En **återkommande leverans** skapar en ny leveransinstans varje gång den körs. Om arbetsflödet till exempel är schemalagt att köras en gång i veckan resulterar det i 52 leveranser efter ett år. Det innebär också att de breda loggarna och spårningsloggarna separeras av varje leveransinstans.

![Återkommande leverans](assets/delivery_recurring.jpg)

I den här videon förklaras hur du konfigurerar en återkommande leverans och en schemaläggningsaktivitet.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>Det går inte att skicka ett korrektur från en **[!UICONTROL Recurring delivery]** typaktivitet.\
>Om du vill skapa en leverans direkt via ett kampanjarbetsflöde använder du de kanalspecifika aktiviteter som är förkonfigurerade (t.ex. **[!UICONTROL Email delivery]**).
