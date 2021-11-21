---
product: campaign
title: Skapa en testmiljö
description: Skapa en testmiljö
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 10%

---

# Skapa en testmiljö{#creating-a-test-environment}

![](../../assets/v7-only.svg)

Så här skapar du en testmiljö (sandlådeläge):

>[!IMPORTANT]
>
>Använd bara den här metoden för att skapa miljöer för testmiljöer. I alla andra fall använder du guiden för målmappning. Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Starta Adobe Campaign Explorer och gå till instansroten.
1. Högerklicka och lägg till en **[!UICONTROL Generic folder]** i listrutorna.

   ![](assets/offer_env_creation_001.png)

1. Gå sedan till mappen som du just skapade och lägg till en **[!UICONTROL Offer environment]** med högerklicksmenyerna.

   ![](assets/offer_env_creation_001bis.png)

1. Använd samma process för att skapa miljöns undermappar och element.
1. När testerna är klara och du vill använda miljön i produktionen kan du duplicera erbjudandena och utrymmena i designmiljön. (Högerklicka > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)
