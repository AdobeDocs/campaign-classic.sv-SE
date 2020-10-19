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
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 15%

---


# Om åtkomst till federerade data {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>Åtkomst till en extern databas via FDA är endast möjlig för anläggningsinstallationer eller hybridinstallationer, med undantag för anslutningarna till Snowflake. Se denna [sida](https://helpx.adobe.com/se/campaign/kb/acc-on-prem-vs-hosted.html) för mer information om detta.

## Verksamhetsprincip {#operating-principle}

Med FDA-alternativet kan du utöka din datamodell i en tredjepartsdatabas. Den identifierar automatiskt strukturen för måltabellerna och använder data från SQL-källorna.

Om du vill använda den här funktionen måste du:

1. Ha en extern databas som är kompatibel med Adobe Campaign FDA-modulen. Listan över databassystem och kompatibla versioner finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html). Användarna måste också ha [nödvändiga behörigheter](../../platform/using/remote-database-access-rights.md) i Adobe Campaign och i den externa databasen.
1. [Installera de drivrutiner](../../platform/using/specific-configuration-database.md) som motsvarar din databas på Adobe Campaign-servern.
1. [Skapa och konfigurera ett externt konto](../../platform/using/connecting-to-database.md) som gör att du kan upprätta en anslutning mellan Adobe Campaign och den externa databasen. Mer information om tillgängliga externa konton finns på den här [sidan](../../platform/using/external-accounts.md).
1. [Skapa schemat](../../platform/using/creating-data-schema.md) för den externa databasen i Adobe Campaign. På så sätt kan du känna igen den externa databasens datastruktur.
1. Till slut [skapar du en ny målmappning](../../platform/using/defining-data-mapping.md) från det tidigare skapade schemat, om mottagarna av dina leveranser kommer från den externa databasen. Detta innebär vissa begränsningar, särskilt när det gäller att personalisera leveranserna.

När dataschemat har skapats kan data bearbetas i Adobe Campaign arbetsflöden. Mer information om detta finns i [det här avsnittet](../../workflow/using/accessing-an-external-database--fda-.md).

## Tillgängliga externa databaser {#external-database}

Nedan finns en lista över alla externa databaser som är kompatibla med Adobe Campaign FDA-modulen:

* Microsoft Azure Synapse Analytics. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md#azure-external).
* Snowflake. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).
* Hadoop. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3).
* Oracle. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md#configure-access-to-oracle).
* Netezza. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md#configure-access-to-netezza).
* Sybase IQ. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md#configure-access-to-sybase-iq).
* Teradata. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md#configure-access-to-teradata).
* SAP HANA. Mer information om detta hittar du i det här [avsnittet](../../platform/using/specific-configuration-database.md).

## God praxis och rekommendationer {#best-practices-and-recommendations}

FDA-alternativet används för att ändra data i externa databaser i batchläge i arbetsflöden. Användning av FDA i ett annat sammanhang, t.ex. för enhetsoperationer, måste utföras med försiktighet (personalisering, interaktion, realtidsleveranser osv.).

Undvik de åtgärder som behöver använda både Adobe Campaign och den externa databasen så mycket som möjligt. Om du vill göra det kan du:

* Exportera Adobe Campaign-databasen till den externa databasen och kör åtgärderna endast från den externa databasen innan du importerar resultaten till Adobe Campaign igen.
* Samla in data från den externa Adobe Campaign-databasen och kör åtgärderna lokalt.

Om du vill utföra personalisering i leveranser med data från den externa databasen, samlar du in data som ska användas i ett arbetsflöde för att göra dem tillgängliga i en tillfällig tabell. Använd sedan data från den tillfälliga tabellen för att anpassa leveransen.

## Begränsningar {#limitations}

FDA-alternativet är underställt begränsningsskyddet för det externa databassystem som du använder.

Av prestandaskäl rekommenderar vi inte att du använder den här funktionen för att utföra enhetliga operationer (leveranspersonalisering, interaktionsmodul, realtid).
