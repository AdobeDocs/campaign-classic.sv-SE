---
product: campaign
title: Konfigurera FDA-anslutningar
description: Lär dig konfigurationssteg för FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 4%

---

# Konfigurera FDA-anslutningar {#specific-configurations-by-database-type}



Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern.

Som regel måste du installera motsvarande klientlager på den externa databasen på Adobe Campaign-servern.

>[!NOTE]
>
>Kompatibla versioner visas i [Kompatibilitetsmatris för kampanj](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
>

## Konfigurationssteg {#fda-configuration-steps}

Så här ställer du in åtkomst till en extern databas med FDA:

1. Installera drivrutinerna och konfigurera det externa konto som motsvarar din databas på Adobe Campaign-servern. Se de databasspecifika sidorna [som listas nedan](#fda-specific-configuration)
1. Testa det externa kontot eller skapa en tillfällig anslutning mellan Adobe Campaign och den externa databasen. [Läs mer](../../installation/using/connecting-to-database.md)
1. Skapa schemat för den externa databasen i Adobe Campaign. På så sätt kan du identifiera den externa databasens datastruktur. [Läs mer](../../installation/using/creating-data-schema.md)
1. Skapa vid behov en ny målmappning från det schema som skapades tidigare. Detta är nödvändigt om mottagarna av leveranserna kommer från den externa databasen. Den här implementeringen har begränsningar som rör meddelandepersonalisering. [Läs mer](../../installation/using/defining-data-mapping.md)

När dataschemat har skapats kan data bearbetas i Adobe Campaign arbetsflöden. Mer information om detta finns i [det här avsnittet](../../workflow/using/accessing-an-external-database-fda.md).

## Databasspecifik konfiguration {#fda-specific-configuration}

Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern samt att konfigurera det externa kontot.

Följ länkarna nedan om du vill veta mer:

* Connect Campaign och [Amazon Redshift](../../installation/using/configure-fda-redshift.md)
* Connect Campaign och [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Connect Campaign och [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Anslut kampanj och [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Connect Campaign och [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* Connect Campaign och [Netezza](../../installation/using/configure-fda-netezza.md)
* Anslut kampanj och [Oracle](../../installation/using/configure-fda-oracle.md)
* Connect Campaign och [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* Connect Campaign och [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Connect Campaign och [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Connect Campaign och [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Connect Campaign och [Teradata](../../installation/using/configure-fda-teradata.md)
* Connect Campaign och [Vertica analytics](../../installation/using/configure-fda-vertica.md)
