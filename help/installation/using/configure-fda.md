---
title: Konfigurera FDA-anslutningar
description: Lär dig konfigurationssteg för FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 3d6515ca291715e5e02f9b5404803e9087555284
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---


# Konfigurera FDA-kopplingar {#specific-configurations-by-database-type}

Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern.

Som regel måste du installera motsvarande klientlager på den externa databasen på Adobe Campaign-servern.

>[!NOTE]
>
>Kompatibla versioner visas i [Campaign-kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).


## Konfigurationssteg {#fda-configuration-steps}

Så här ställer du in åtkomst till en extern databas med FDA:

1. Installera de drivrutiner som motsvarar din databas på Adobe Campaign-servern. Drivrutiner listas på de databasspecifika sidorna [som listas nedan](#fda-specific-configuration).
1. [Skapa och konfigurera ett externt konto](../../installation/using/connecting-to-database.md) som gör att du kan upprätta en anslutning mellan Adobe Campaign och den externa databasen. Mer information om externa konton i Campaign finns på [den här sidan](../../installation/using/external-accounts.md).
1. [Skapa schemat](../../installation/using/creating-data-schema.md) för den externa databasen i Adobe Campaign. På så sätt kan du känna igen den externa databasens datastruktur.
1. Om det behövs [skapar du en ny målmappning](../../installation/using/defining-data-mapping.md) från det schema som skapades tidigare. Detta är nödvändigt om mottagarna av leveranserna kommer från den externa databasen. Den här implementeringen har begränsningar som rör meddelandepersonalisering.

När dataschemat har skapats kan data bearbetas i Adobe Campaign arbetsflöden. Mer information om detta finns i [det här avsnittet](../../workflow/using/accessing-an-external-database--fda-.md).

## Databasspecifik konfiguration {#fda-specific-configuration}

Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern.

Följ länkarna nedan om du vill veta mer:

* [Azure Synapse](../../installation/using/configure-fda-synapse.md)

* [Snowflake](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [Netezza](../../installation/using/configure-fda-netezza.md)

* [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
