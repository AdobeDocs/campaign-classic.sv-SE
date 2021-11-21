---
product: campaign
title: Definiera den slutliga leveransen
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 9%

---

# Definiera den slutliga leveransen {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

När skriptet har skapats för att välja vinnare av A/B-tester kan du definiera parametrarna för den slutliga leveransen.

1. Anslut **[!UICONTROL JavaScript code]** aktivitet till återstående **[!UICONTROL Delivery]** aktivitet.
1. Öppna **[!UICONTROL Delivery]** aktivitet.
1. Avmarkera **[!UICONTROL Generate an outbound transition]** för att slutföra arbetsflödet med den här aktiviteten.
1. Låt de andra alternativen behålla standardvärdena.

   ![](assets/ab_test_final_delivery.png)

Genom att förbereda leveransen som anges i övergången (definieras via **[!UICONTROL Javascript Code]** -aktivitet) kan du sedan godkänna den och starta sändningen, enligt beskrivningen i nästa steg.

Du kan nu starta arbetsflödet. [Läs mer](a-b-testing-uc-start-workflow.md).
