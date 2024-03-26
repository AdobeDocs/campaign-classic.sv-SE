---
product: campaign
title: Skapa erbjudandekategorier
description: Skapa erbjudandekategorier
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 2%

---

# Skapa erbjudandekategorier{#creating-offer-categories}



Det går endast att skapa erbjudandekategorier i **[!UICONTROL Design]** miljö. De driftsätts automatiskt i **[!UICONTROL Live]** miljö (dvs. görs tillgänglig) när de erbjudanden som de innehåller har skapats/ändrats godkänns. Som standard är **[!UICONTROL Design]** -miljön innehåller en kategori för att ta emot alla erbjudanden. Underkategorier kan skapas för att lägga till hierarki i katalogerbjudandena.

För varje kategori kan du definiera datum för behörighet, dvs. en period efter vilken erbjudandena i kategorin inte längre kan presenteras för deras mål. Om du vill att erbjudandena från en viss kategori ska väljas som en prioritet av erbjudandemotorn, ska visa en produkt bättre, till exempel, kan du öka deras vikt för en viss period genom att lägga till en multipliceringsvikt i kategorin.

Om du vill skapa ytterligare en kategori gör du så här:

1. Gå till **[!UICONTROL Offer catalog]** mapp.

   ![](assets/offer_cat_create_001.png)

1. Högerklicka och välj **[!UICONTROL Create a new "Offer category" folder]** i listrutan.

   ![](assets/offer_cat_create_002.png)

1. Ge kategorin ett nytt namn. Du kan redigera etiketten senare med **[!UICONTROL General]** -fliken.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Upprepa dessa steg om du vill skapa så många kategorier som behövs.

   Därefter kan du, efter behov,

   * Tilldela berättigandedatum från **[!UICONTROL Eligibility]** -fliken.

     ![](assets/offer_cat_create_004.png)

   * Ange nyckelord som kan användas för att välja erbjudanden inom denna kategori med hjälp av **[!UICONTROL Themes]** fält.

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >När du anropar erbjudandemotorn väljs bara den del av katalogen där teman eller kategorierna matchar parametrarna.

   * Tillfälligt&quot;öka&quot; erbjudandevikten för en kategori under en viss period via **[!UICONTROL Multiplier weight]** fält.

     ![](assets/offer_cat_create_006.png)

En sammanfattning av reglerna för behörighet finns på kontrollpanelen för de erbjudanden som ingår i kategorin. Klicka på **[!UICONTROL Schedule and eligibility rules of the offer]** länk.

![](assets/offer_create_006.png)
