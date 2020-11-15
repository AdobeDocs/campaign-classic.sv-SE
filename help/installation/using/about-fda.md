---
title: Åtkomst till en extern databas
description: Lär dig hur du får åtkomst till och bearbetar data i en extern databas
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 99d766cb6234347ea2975f3c08a6ac0496619b41
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 3%

---


# Kom igång med åtkomst till federerade data {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

## Förutsättningar {#operating-principle}

Med FDA-alternativet kan du utöka din datamodell i en tredjepartsdatabas. Den identifierar automatiskt strukturen för måltabellerna och använder data från SQL-källorna.

För att kunna använda den här funktionen anges följande krav:

* **Konfiguration**: förutom för Snowflake behöver du en **lokal** eller **hybridvärdmodell** för att kunna konfigurera Federated Data Access. [Läs mer](../../installation/using/hosting-models.md)
* **Extern databasversion**: du behöver en extern databas som är kompatibel med Adobe Campaign FDA-modulen. Listan över databassystem och kompatibla versioner finns i Campaign- [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Behörigheter**: -användare måste också ha [nödvändiga behörigheter](../../installation/using/remote-database-access-rights.md) i Adobe Campaign och i den externa databasen.

## Begränsningar {#limitations}

FDA-alternativet används för att ändra data i externa databaser i batchläge i arbetsflöden. För att undvika prestandaproblem rekommenderar vi inte att du använder FDA-modulen i samband med enhetsåtgärder som: personalisering, interaktion, meddelanden i realtid osv.

Undvik de åtgärder som behöver använda både Adobe Campaign och den externa databasen så mycket som möjligt. Om du vill göra det kan du:

* Exportera Adobe Campaign-databasen till den externa databasen och kör åtgärderna endast från den externa databasen innan du importerar resultaten till Adobe Campaign igen.

* Samla in data från den externa Adobe Campaign-databasen och kör åtgärderna lokalt.

Om du vill utföra personalisering i leveranser med data från den externa databasen, samlar du in data som ska användas i ett arbetsflöde för att göra dem tillgängliga i en tillfällig tabell. Använd sedan data från den tillfälliga tabellen för att anpassa leveransen.

FDA-alternativet har begränsningar för det externa databassystem som du använder.

## Rekommendationer {#recommendations}

### Skapa tillfälliga scheman {#create-temporary-schemas}

Du kan hantera flera åtkomster av den externa Greenplum-databasen via FDA. Med ett dedikerat alternativ kan du skapa ett arbetsschema direkt när du konfigurerar det externa kontot.

![](assets/fda_work_table.png)

>[!NOTE]
>
>Det här alternativet är bara tillgängligt med PostgreSQL Greenplum.

### Optimera e-postpersonalisering med externa data {#optimizing-email-personalization-with-external-data}

Du kan förbearbeta meddelandepersonalisering i ett dedikerat arbetsflöde. För att göra detta använder du **[!UICONTROL Prepare the personalization data with a workflow]** alternativet som finns på fliken **[!UICONTROL Analysis]** i leveransegenskaperna.

Under leveransanalysen skapar och kör det här alternativet automatiskt ett arbetsflöde som lagrar alla data som är länkade till målet i en tillfällig tabell, inklusive data från tabeller som är länkade i en extern databas.

Det här alternativet förbättrar prestanda avsevärt när personaliseringssteget körs.

### Use data from an external database in a workflow {#using-data-from-an-external-database-in-a-workflow}

I flera Adobe Campaign-arbetsflödesaktiviteter kan du använda data som lagras i en extern databas.

* **Filtrera på externa data** - Med [aktiviteten Fråga](../../workflow/using/targeting-data.md#selecting-data) kan du lägga till externa data och använda dem i definierade filterkonfigurationer. Se denna [sida](../../workflow/using/targeting-data.md#selecting-data) för mer information om detta.

* **Skapa delmängder** - Med aktiviteten [Dela](../../workflow/using/split.md) kan du skapa delmängder. Du kan använda externa data för att definiera de filtervillkor som ska användas. Se denna [sida](../../workflow/using/split.md) för mer information om detta.

* **Läs in extern databas** - Du kan använda externa data i aktiviteten [Datainläsning](../../workflow/using/data-loading--rdbms-.md) (RDBMS). Läs mer på [den här sidan](../../workflow/using/data-loading--rdbms-.md).

* **Lägga till information och länkar** - Med [anrikningsaktiviteten](../../workflow/using/enrichment.md) kan du lägga till ytterligare data i arbetsflödet och länka till en extern tabell. I det här sammanhanget kan den använda data från en extern databas. Läs mer på [den här sidan](../../workflow/using/enrichment.md).
