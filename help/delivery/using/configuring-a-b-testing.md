---
product: campaign
title: Konfigurera A/B-tester
description: Lär dig hur du konfigurerar A/B-testning i Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 3%

---

# Konfigurera A/B-tester {#configuring-a-b-testing}

I det här avsnittet beskrivs hur du skapar ett arbetsflöde för A/B-testning.

1. Skapa ett nytt arbetsflöde och konfigurera sedan en [Query](../../workflow/using/query.md)-aktivitet så att den målar den önskade populationen.

1. Lägg till en [delad](../../workflow/using/split.md)-aktivitet för att dela målpopulationen i flera delmängder.

1. Öppna aktiviteten och konfigurera sedan varje delmängd efter dina behov. Mer information om hur du konfigurerar en **[!UICONTROL Split]**-aktivitet finns i [det här avsnittet](../../workflow/using/split.md).

   I det här exemplet vill vi testa två nya ämnen för ett nyhetsbrev genom att presentera vart och ett av dem för 10 procent av målbefolkningen.

   ![](assets/ab-testing-split.png)

1. Lägg till en övergång för att skicka nyhetsbrevet med det aktuella ämnet till den återstående populationen. Aktivera alternativet **[!UICONTROL Generate complement]** på fliken **[!UICONTROL General]** om du vill göra det.

   ![](assets/ab-testing-complement.png)

1. Lägg till den version av leveransen som ska testas för varje delmängd.

   ![](assets/ab-testing-delivery.png)

Du kan nu starta arbetsflödet. När leveranserna har skickats kan du spåra beteendet hos de tre delmängderna i leveransloggarna för att se vilket ämne som har varit mest framgångsrikt.

Med arbetsflöden kan ni också automatisera era processer genom att automatiskt identifiera den bättre levererade varianten och sedan skicka den till den återstående populationen. Mer information finns i det här dedikerade [användningsexemplet](a-b-testing-use-case.md).
