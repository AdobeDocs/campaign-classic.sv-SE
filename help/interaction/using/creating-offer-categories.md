---
title: Skapa erbjudandekategorier
seo-title: Skapa erbjudandekategorier
description: Skapa erbjudandekategorier
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Skapa erbjudandekategorier{#creating-offer-categories}

Det går bara att skapa erbjudandekategorier i **[!UICONTROL Design]** miljön. De distribueras automatiskt i **[!UICONTROL Live]** miljön (dvs. görs tillgängliga) när de erbjudanden de innehåller har skapats/ändrats och godkänts. Som standard innehåller **[!UICONTROL Design]** miljön en kategori för att ta emot alla erbjudanden. Underkategorier kan skapas för att lägga till hierarki i katalogerbjudandena.

För varje kategori kan du definiera datum för behörighet, dvs. en period efter vilken erbjudandena i kategorin inte längre kan presenteras för deras mål. Om du vill att erbjudandena från en viss kategori ska väljas som en prioritet av erbjudandemotorn, ska visa en produkt bättre, till exempel, kan du öka deras vikt för en viss period genom att lägga till en multipliceringsvikt i kategorin.

Om du vill skapa ytterligare en kategori gör du så här:

1. Gå till **[!UICONTROL Offer catalog]** mappen.

   ![](assets/offer_cat_create_001.png)

1. Högerklicka och välj **[!UICONTROL Create a new "Offer category" folder]** i listrutan.

   ![](assets/offer_cat_create_002.png)

1. Ge kategorin ett nytt namn. Du kan redigera etiketten senare på **[!UICONTROL General]** fliken.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Upprepa dessa steg om du vill skapa så många kategorier som behövs.

   Därefter kan du, efter behov,

   * tilldela berättigandedatum från **[!UICONTROL Eligibility]** fliken.

      ![](assets/offer_cat_create_004.png)

   * Ange nyckelord som kan användas för att välja erbjudanden inom denna kategori, med hjälp av **[!UICONTROL Themes]** fältet.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >När du anropar erbjudandemotorn väljs bara den del av katalogen där teman eller kategorierna matchar parametrarna.

   * Du kan tillfälligt &quot;öka&quot; en kategoris vikt under en viss period via **[!UICONTROL Multiplier weight]** fältet.

      ![](assets/offer_cat_create_006.png)

En sammanfattning av reglerna för behörighet finns på kontrollpanelen för de erbjudanden som ingår i kategorin. Klicka på **[!UICONTROL Schedule and eligibility rules of the offer]** länken om du vill visa dem.

![](assets/offer_create_006.png)

