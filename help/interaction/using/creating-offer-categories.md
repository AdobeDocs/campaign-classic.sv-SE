---
solution: Campaign Classic
product: campaign
title: Skapa erbjudandekategorier
description: Skapa erbjudandekategorier
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Skapa erbjudandekategorier{#creating-offer-categories}

Det går bara att skapa erbjudandekategorier i **[!UICONTROL Design]** miljön. De distribueras automatiskt i **[!UICONTROL Live]** miljön (dvs. görs tillgängliga) när de erbjudanden de innehåller har skapats/ändrats och godkänts. Som standard innehåller **[!UICONTROL Design]** miljön en kategori för att ta emot alla erbjudanden. Underkategorier kan skapas för att lägga till hierarki i katalogerbjudandena.

För varje kategori kan du definiera datum för behörighet, dvs. en period efter vilken erbjudandena i kategorin inte längre kan presenteras för deras mål. Om du vill att erbjudandena från en viss kategori ska väljas som en prioritet av erbjudandemotorn, ska visa en produkt bättre, till exempel, kan du öka deras vikt för en viss period genom att lägga till en multipliceringsvikt i kategorin.

Om du vill skapa ytterligare en kategori gör du så här:

1. Go to the **[!UICONTROL Offer catalog]** folder.

   ![](assets/offer_cat_create_001.png)

1. Högerklicka och välj **[!UICONTROL Create a new "Offer category" folder]** i listrutan.

   ![](assets/offer_cat_create_002.png)

1. Ge kategorin ett nytt namn. Du kan redigera etiketten senare på **[!UICONTROL General]** fliken.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Upprepa dessa steg om du vill skapa så många kategorier som behövs.

   Därefter kan du, efter behov,

   * Tilldela berättigandedatum från **[!UICONTROL Eligibility]** fliken.

      ![](assets/offer_cat_create_004.png)

   * Ange nyckelord som kan användas för att välja erbjudanden i den här kategorin med hjälp av **[!UICONTROL Themes]** fältet.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >När du anropar erbjudandemotorn väljs bara den del av katalogen där teman eller kategorierna matchar parametrarna.

   * Tillfälligt&quot;öka&quot; erbjudandevikten för en kategori under en viss period via **[!UICONTROL Multiplier weight]** fältet.

      ![](assets/offer_cat_create_006.png)

En sammanfattning av reglerna för behörighet finns på kontrollpanelen för de erbjudanden som ingår i kategorin. Klicka på **[!UICONTROL Schedule and eligibility rules of the offer]** länken om du vill visa dem.

![](assets/offer_create_006.png)

