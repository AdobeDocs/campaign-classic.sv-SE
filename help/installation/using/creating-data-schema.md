---
product: campaign
title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: d2d0ff575edbee18febb5ec895fcec1e0ae34de7
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 6%

---

# Skapa dataschemat {#creating-the-data-schema}

![](../../assets/v7-only.svg)

Så här skapar du ett schema i en extern databas:

1. Klicka på knappen **[!UICONTROL New]** ovanför listan med datamappningar och välj **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Ange en **[!UICONTROL Namespace]** och **[!UICONTROL Name]** för schemat och välj **[!UICONTROL External account]** som aktiverar anslutningen till databasen. Detta ger åtkomst till listan med tabeller som är tillgängliga i den externa basen.

   ![](assets/wf_new_schema_select_table_fda.png)

1. I fältet **[!UICONTROL Table name]** väljer du den tabell som innehåller de data som ska samlas in.

   Med Snowflake kan du här välja dina vyer om databasanvändaren har fått rätt behörighet. Observera att när du använder vyer kommer Adobe Campaign inte att kunna generera XML-schemat automatiskt, utan du måste själv skapa det. Mer information om vyer finns i [Snowflake-dokumentationen](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Bekräfta genom att klicka på **[!UICONTROL OK]**. Adobe Campaign identifierar automatiskt strukturen i den markerade tabellen och genererar det logiska schemat. Observera att Adobe Campaign inte genererar några länkar.

1. Bekräfta skapandet genom att klicka på **[!UICONTROL Save]**.

   >[!CAUTION]
   >
   >Med Snowflake är en primärnyckel obligatorisk.

   ![](assets/wf_new_schema_generate_fda.png)

Indexen skapas automatiskt när en tabell mappas (standard- eller FDA-mappning).
