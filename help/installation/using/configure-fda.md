---
product: campaign
title: Konfigurera FDA-anslutningar
description: Lär dig konfigurationssteg för FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Konfigurera FDA-kopplingar {#specific-configurations-by-database-type}

![](../../assets/v7-only.svg)

Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern.

Som regel måste du installera motsvarande klientlager på den externa databasen på Adobe Campaign-servern.

>[!NOTE]
>
>Kompatibla versioner visas i [Matris för kampanjkompatibilitet](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

## Konfigurationssteg {#fda-configuration-steps}

Så här ställer du in åtkomst till en extern databas med FDA:

1. Installera drivrutinerna och konfigurera det externa konto som motsvarar din databas på Adobe Campaign-servern. Se de databasspecifika sidorna [listas nedan](#fda-specific-configuration)
1. Testa det externa kontot eller skapa en tillfällig anslutning mellan Adobe Campaign och den externa databasen. [Läs mer](../../installation/using/connecting-to-database.md)
1. Skapa schemat för den externa databasen i Adobe Campaign. På så sätt kan du identifiera den externa databasens datastruktur. [Läs mer](../../installation/using/creating-data-schema.md)
1. Skapa vid behov en ny målmappning från det schema som skapades tidigare. Detta är nödvändigt om mottagarna av leveranserna kommer från den externa databasen. Den här implementeringen har begränsningar som rör meddelandepersonalisering. [Läs mer](../../installation/using/defining-data-mapping.md)

När dataschemat har skapats kan data bearbetas i Adobe Campaign arbetsflöden. Mer information om detta finns i [det här avsnittet](../../workflow/using/accessing-an-external-database--fda-.md).

## Databasspecifik konfiguration {#fda-specific-configuration}

Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern samt att konfigurera det externa kontot.

Följ länkarna nedan om du vill veta mer:

* Connect Campaign och [Vertica](../../installation/using/configure-fda-vertica.md)

* Connect Campaign och [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)

* Connect Campaign och [azure synapse](../../installation/using/configure-fda-synapse.md)

* Connect Campaign och [Snowflake](../../installation/using/configure-fda-snowflake.md)

* Connect Campaign och [Hadoop](../../installation/using/configure-fda-hadoop.md)

* Connect Campaign och [Oracle](../../installation/using/configure-fda-oracle.md)

* Connect Campaign och [Netezza](../../installation/using/configure-fda-netezza.md)

* Connect Campaign och [sybase IQ](../../installation/using/configure-fda-sybase.md)

* Connect Campaign och [Teradata](../../installation/using/configure-fda-teradata.md)

* Connect Campaign och [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

* Connect Campaign och [PostgreSQL](../../installation/using/configure-fda-postgresql.md)

* Connect Campaign och [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)

* Connect Campaign och [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

