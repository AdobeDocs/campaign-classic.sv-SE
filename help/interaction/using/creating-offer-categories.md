---
product: campaign
title: Skapa erbjudandekategorier
description: Skapa erbjudandekategorier
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Skapa erbjudandekategorier{#creating-offer-categories}



Det går bara att skapa erbjudandekategorier i miljön **[!UICONTROL Design]**. De distribueras automatiskt i **[!UICONTROL Live]**-miljön (d.v.s. görs tillgängliga) när de erbjudanden som de innehåller har skapats/ändrats godkänns. Miljön **[!UICONTROL Design]** innehåller som standard en kategori för att ta emot alla erbjudanden. Underkategorier kan skapas för att lägga till hierarki i katalogerbjudandena.

För varje kategori kan du definiera datum för behörighet, dvs. en period efter vilken erbjudandena i kategorin inte längre kan presenteras för deras mål. Om du vill att erbjudandena från en viss kategori ska väljas som en prioritet av erbjudandemotorn, ska visa en produkt bättre, till exempel, kan du öka deras vikt för en viss period genom att lägga till en multipliceringsvikt i kategorin.

Om du vill skapa ytterligare en kategori gör du så här:

1. Gå till mappen **[!UICONTROL Offer catalog]**.

   ![](assets/offer_cat_create_001.png)

1. Högerklicka och välj **[!UICONTROL Create a new "Offer category" folder]** i listrutan.

   ![](assets/offer_cat_create_002.png)

1. Ge kategorin ett nytt namn. Du kan redigera etiketten senare på fliken **[!UICONTROL General]**.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Upprepa dessa steg om du vill skapa så många kategorier som behövs.

   Därefter kan du, efter behov,

   * Tilldela berättigandedatum från fliken **[!UICONTROL Eligibility]**.

     ![](assets/offer_cat_create_004.png)

   * Ange nyckelord som kan användas för att välja erbjudanden i den här kategorin med hjälp av fältet **[!UICONTROL Themes]**.

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >När du anropar erbjudandemotorn väljs bara den del av katalogen där teman eller kategorierna matchar parametrarna.

   * Tillfälligt&quot;öka&quot; erbjudandevikten för en kategori för en viss period via fältet **[!UICONTROL Multiplier weight]**.

     ![](assets/offer_cat_create_006.png)

En sammanfattning av reglerna för behörighet finns på kontrollpanelen för de erbjudanden som ingår i kategorin. Klicka på länken **[!UICONTROL Schedule and eligibility rules of the offer]** om du vill visa dem.

![](assets/offer_create_006.png)
