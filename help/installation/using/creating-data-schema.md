---
product: campaign
title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---

# Skapa dataschemat {#creating-the-data-schema}

![](../../assets/v7-only.svg)

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
