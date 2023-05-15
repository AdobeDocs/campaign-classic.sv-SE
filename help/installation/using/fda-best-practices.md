---
product: campaign
title: Bästa praxis och begränsningar för FDA-kampanjer
description: Lär dig bästa praxis och begränsningar när du arbetar med en extern databas (FDA)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 4%

---

# God praxis och begränsningar



## Optimera e-postpersonalisering med externa data {#optimizing-email-personalization-with-external-data}

Du kan förbearbeta meddelandepersonalisering i ett dedikerat arbetsflöde. Om du vill göra det använder du **[!UICONTROL Prepare the personalization data with a workflow]** alternativ, finns i **[!UICONTROL Analysis]** -fliken för leveransegenskaperna.

Under leveransanalysen skapar och kör det här alternativet automatiskt ett arbetsflöde som lagrar alla data som är länkade till målet i en tillfällig tabell, inklusive data från tabeller som är länkade i en extern databas.

Det här alternativet förbättrar prestanda avsevärt när personaliseringssteget körs.

## Använd data från en extern databas i ett arbetsflöde {#using-data-from-an-external-database-in-a-workflow}

I flera Adobe Campaign-arbetsflödesaktiviteter kan du använda data som lagras i en extern databas.

* **Filtrera på externa data** - [Fråga](../../workflow/using/targeting-data.md#selecting-data) Med -aktivitet kan du lägga till externa data och använda dem i definierade filterkonfigurationer. Mer information finns på [den här sidan](../../workflow/using/targeting-data.md#selecting-data).

* **Skapa underuppsättningar** - [Dela](../../workflow/using/split.md) kan du skapa delmängder. Du kan använda externa data för att definiera de filtervillkor som ska användas. Mer information finns på [den här sidan](../../workflow/using/split.md).

* **Läs in extern databas** - Du kan använda externa data i [Datainläsning](../../workflow/using/data-loading--rdbms-.md) (RDBMS) aktivitet. Läs mer i [den här sidan](../../workflow/using/data-loading--rdbms-.md).

* **Lägga till information och länkar** - [Berikning](../../workflow/using/enrichment.md) Med -aktivitet kan du lägga till ytterligare data i arbetsflödet och länka till en extern tabell. I det här sammanhanget kan den använda data från en extern databas. Läs mer i [den här sidan](../../workflow/using/enrichment.md).

## FDA-begränsningar {#limitations}

FDA-alternativet används för att ändra data i externa databaser i batchläge i arbetsflöden. För att undvika prestandaproblem rekommenderar vi inte att du använder FDA-modulen i samband med enhetsåtgärder som: personalisering, interaktion, meddelanden i realtid osv.

Undvik de åtgärder som behöver använda både Adobe Campaign och den externa databasen så mycket som möjligt. Om du vill göra det kan du:

* Exportera Adobe Campaign-databasen till den externa databasen och kör åtgärderna endast från den externa databasen innan du importerar resultaten till Adobe Campaign igen.

* Samla in data från den externa Adobe Campaign-databasen och kör åtgärderna lokalt.

Om du vill utföra personalisering i leveranser med data från den externa databasen, samlar du in data som ska användas i ett arbetsflöde för att göra dem tillgängliga i en tillfällig tabell. Använd sedan data från den tillfälliga tabellen för att anpassa leveransen.

FDA-alternativet har begränsningar för det externa databassystem som du använder.
