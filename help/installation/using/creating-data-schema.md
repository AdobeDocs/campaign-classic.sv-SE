---
solution: Campaign Classic
product: campaign
title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---


# Skapa dataschemat {#creating-the-data-schema}

Så här skapar du ett schema i en extern databas:

1. Klicka på knappen **[!UICONTROL New]** ovanför listan med datamappningar och välj **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Ange ett namn och en beskrivning för schemat och välj det externa konto som ska aktivera anslutningen till databasen. Detta ger åtkomst till listan med tabeller som är tillgängliga i den externa basen. Välj den tabell som innehåller de data som ska samlas in.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Bekräfta genom att klicka på **[!UICONTROL OK]**. Adobe Campaign identifierar automatiskt strukturen i den markerade tabellen och genererar det logiska schemat. Observera att Adobe Campaign inte genererar några länkar.

1. Bekräfta skapandet genom att klicka på **[!UICONTROL Save]**.

   >[!CAUTION]
   >
   >Med Snowflake är en primärnyckel obligatorisk.

   ![](assets/wf_new_schema_generate_fda.png)

Indexen skapas automatiskt när en tabell mappas (standard- eller FDA-mappning).
