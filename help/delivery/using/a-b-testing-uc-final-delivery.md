---
solution: Campaign Classic
product: campaign
title: Definiera den slutliga leveransen
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Definiera den slutliga leveransen {#step-6--defining-the-final-delivery}

När skriptet har skapats för att välja vinnare av A/B-tester kan du definiera parametrarna för den slutliga leveransen.

1. Anslut aktiviteten **[!UICONTROL JavaScript code]** till den återstående **[!UICONTROL Delivery]**-aktiviteten.
1. Öppna aktiviteten **[!UICONTROL Delivery]**.
1. Avmarkera alternativet **[!UICONTROL Generate an outbound transition]** om du vill avsluta arbetsflödet med den här aktiviteten.
1. Låt de andra alternativen behålla standardvärdena.

   ![](assets/ab_test_final_delivery.png)

Genom att förbereda leveransen som anges i övergången (definieras via aktiviteten **[!UICONTROL Javascript Code]**) kan du sedan godkänna den och starta sändningen, enligt beskrivningen i nästa steg.

Du kan nu starta arbetsflödet (se [Steg 7: Starta arbetsflödet](../../delivery/using/a-b-testing-uc-start-workflow.md)).
