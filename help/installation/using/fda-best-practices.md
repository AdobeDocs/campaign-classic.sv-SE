---
product: campaign
title: Bästa praxis och begränsningar för FDA-kampanjer
description: Lär dig bästa praxis och begränsningar när du arbetar med en extern databas (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# God praxis och begränsningar



## Optimera e-postpersonalisering med externa data {#optimizing-email-personalization-with-external-data}

Du kan förbearbeta meddelandepersonalisering i ett dedikerat arbetsflöde. Använd alternativet **[!UICONTROL Prepare the personalization data with a workflow]** som finns på fliken **[!UICONTROL Analysis]** i leveransegenskaperna för att göra detta.

Under leveransanalysen skapar och kör det här alternativet automatiskt ett arbetsflöde som lagrar alla data som är länkade till målet i en tillfällig tabell, inklusive data från tabeller som är länkade i en extern databas.

Det här alternativet förbättrar prestanda avsevärt när personaliseringssteget körs.

## Använd data från en extern databas i ett arbetsflöde {#using-data-from-an-external-database-in-a-workflow}

I flera Adobe Campaign-arbetsflödesaktiviteter kan du använda data som lagras i en extern databas.

* **Filter på externa data** - Med aktiviteten Fråga kan du lägga till externa data och använda dem i definierade filterkonfigurationer. Mer information finns i [dokumentationen för Campaign v8]https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}.

* **Skapa delmängder** - Med aktiviteten Dela kan du skapa delmängder. Du kan använda externa data för att definiera de filtervillkor som ska användas. Se [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}.

* **Läs in extern databas** - Du kan använda externa data i aktiviteten Datainläsning (RDBMS). Läs mer i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html){target="_blank"}.

* **Lägger till information och länkar** - Med hjälp av aktiviteten Berika kan du lägga till ytterligare data i arbetsflödet och länka till en extern tabell. I det här sammanhanget kan den använda data från en extern databas. Se [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}.

## Skyddsritningar och begränsningar {#fda-limitations}

FDA-alternativet är utformat för att hantera data i externa databaser i batchläge i arbetsflöden. För att undvika prestandaproblem bör du inte använda FDA-modulen i samband med enhetsåtgärder som personalisering, interaktion, meddelanden i realtid osv.

Det går inte att ange måldata från en databas och filtrera resultaten med en filtreringsdimension som tillhör en annan databas. Du kan inte koppla tabeller som finns i olika datakällor i en fråga. Du kan lösa den här begränsningen med andra arbetsflödesaktiviteter som Ändra dimension.

Undvik de åtgärder som behöver använda både Adobe Campaign och den externa databasen så mycket som möjligt. Det bästa är att

* Exportera Adobe Campaign-databasen till den externa databasen och kör åtgärderna endast från den externa databasen innan du importerar resultaten till Adobe Campaign igen.

* Samla in data från den externa Adobe Campaign-databasen och kör åtgärderna lokalt.

Om du vill utföra personalisering i leveranser med data från den externa databasen, samlar du in data som ska användas i ett arbetsflöde för att göra dem tillgängliga i en tillfällig tabell. Använd sedan data från den tillfälliga tabellen för att anpassa leveransen.

FDA-alternativet har begränsningar för det externa databassystem som du använder.
