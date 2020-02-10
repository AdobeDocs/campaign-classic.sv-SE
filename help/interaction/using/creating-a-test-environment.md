---
title: Skapa en testmiljö
seo-title: Skapa en testmiljö
description: Skapa en testmiljö
seo-description: null
page-status-flag: never-activated
uuid: 60ce42d5-6c0c-4a0d-bfd6-c778b42563a7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 7a92bc51-24cf-4ce6-bd50-a315f8f6e34e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Skapa en testmiljö{#creating-a-test-environment}

Så här skapar du en testmiljö (sandlådeläge):

>[!CAUTION]
>
>Använd bara den här metoden för att skapa miljöer för testmiljöer. I alla andra fall använder du guiden för målmappning. Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Starta Adobe Campaign Explorer och gå till instansroten.
1. Högerklicka och lägg till en **[!UICONTROL Generic folder]** med hjälp av listrutorna.

   ![](assets/offer_env_creation_001.png)

1. Gå sedan till den mapp du just skapade och lägg till en **[!UICONTROL Offer environment]** med högerklicksmenyerna.

   ![](assets/offer_env_creation_001bis.png)

1. Använd samma process för att skapa miljöns undermappar och element.
1. När testerna är klara och du vill använda miljön i produktionen kan du duplicera erbjudandena och utrymmena i designmiljön. (Högerklicka > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)

