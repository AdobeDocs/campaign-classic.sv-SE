---
product: campaign
title: Skapar dataschemat för FDA
description: Lär dig hur du skapar dataschemat för FDA
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Skapar dataschemat {#creating-the-data-schema}



Så här skapar du ett schema i en extern databas:

1. Klicka på **[!UICONTROL New]** knappen ovanför listan med datamodeller och välj **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Ange en **[!UICONTROL Namespace]** och  **[!UICONTROL Name]** för schemat och välj **[!UICONTROL External account]** som möjliggör anslutning till databasen. Detta ger åtkomst till listan med tabeller som är tillgängliga i den externa basen.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Från **[!UICONTROL Table name]** väljer du den tabell som innehåller de data som ska samlas in.

   Med Snowflake kan du här välja dina vyer om databasanvändaren har fått rätt behörighet. Observera att när du använder vyer kommer Adobe Campaign inte att kunna generera XML-schemat automatiskt, utan du måste själv skapa det. Mer information om vyer finns i [Snowflake dokumentation](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Klicka **[!UICONTROL OK]** för att bekräfta. Adobe Campaign identifierar automatiskt strukturen i den markerade tabellen och genererar det logiska schemat. Observera att Adobe Campaign inte genererar några länkar.

1. Klicka **[!UICONTROL Save]** för att bekräfta skapandet.

   >[!CAUTION]
   >
   >Med Snowflake är en primärnyckel obligatorisk.

   ![](assets/wf_new_schema_generate_fda.png)

Index skapas automatiskt när en tabell mappas (standard- eller FDA-mappning).
