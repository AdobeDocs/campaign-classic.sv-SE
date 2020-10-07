---
title: Åtkomst till en extern databas
seo-title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# Skapa dataschemat {#creating-the-data-schema}

Så här skapar du ett schema i en extern databas:

1. Klicka på **[!UICONTROL New]** knappen ovanför listan med datamodeller och välj **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Ange ett namn och en beskrivning för schemat och välj det externa konto som ska aktivera anslutningen till databasen. Detta ger åtkomst till listan med tabeller som är tillgängliga i den externa basen. Välj den tabell som innehåller de data som ska samlas in.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Bekräfta genom **[!UICONTROL OK]** att klicka. Adobe Campaign identifierar automatiskt strukturen i den markerade tabellen och genererar det logiska schemat. Observera att Adobe Campaign inte genererar några länkar.

1. Klicka **[!UICONTROL Save]** för att bekräfta skapandet.

   >[!CAUTION]
   >
   >Med Snowflake är en primärnyckel obligatorisk.

   ![](assets/wf_new_schema_generate_fda.png)

Indexen skapas automatiskt när en tabell mappas (standard- eller FDA-mappning).
