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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a0698ad55afb391bdc652a00b43b20df6fb9851b

---


# Om åtkomst till federerade data {#about-federated-data-access}

I Adobe Campaign finns alternativet **FDA (Federated Data Access** ) för att bearbeta information som lagras i en eller flera externa databaser: kan ni få åtkomst till externa data utan att ändra strukturen på Adobe Campaign-data.

>[!CAUTION]
>
>Åtkomst till en extern databas via FDA är endast möjlig för lokala eller hybridinstallationer, utom med Snowflake-anslutningarna. Mer information finns på den här [sidan](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Verksamhetsprincip {#operating-principle}

Med FDA-alternativet kan du utöka din datamodell i en tredjepartsdatabas. Den identifierar automatiskt strukturen för måltabellerna och använder data från SQL-källorna.


Om du vill använda den här funktionen måste du:

1. Ha en extern databas som är kompatibel med Adobe Campaign FDA-modulen. Listan över databassystem och kompatibla versioner finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Användarna måste också ha [nödvändiga behörigheter](#remote-database-access-rights) i Adobe Campaign och i den externa databasen.
1. [Installera drivrutinerna](#specific-configurations-by-database-type) som motsvarar databasen på Adobe Campaign-servern.
1. [Skapa och konfigurera ett externt konto](#connecting-to-the-database) som gör att du kan upprätta en anslutning mellan Adobe Campaign och den externa databasen. Mer information om tillgängliga externa konton finns på den här [sidan](../../platform/using/external-accounts.md).
1. [Skapa schemat](#creating-the-data-schema) för den externa databasen i Adobe Campaign. På så sätt kan du känna igen den externa databasens datastruktur.
1. Till slut [skapar du en ny målmappning](#defining-data-mapping) från det tidigare skapade schemat, om mottagarna av dina leveranser kommer från den externa databasen. Detta innebär vissa begränsningar, särskilt när det gäller att personalisera leveranserna.

När dataschemat har skapats kan data bearbetas i Adobe Campaign-arbetsflöden. Mer information finns i [det här avsnittet](../../workflow/using/executing-a-workflow.md#architecture).

## God praxis och rekommendationer {#best-practices-and-recommendations}

FDA-alternativet används för att ändra data i externa databaser i batchläge i arbetsflöden. Användning av FDA i ett annat sammanhang, t.ex. för enhetsoperationer, måste utföras med försiktighet (personalisering, interaktion, realtidsleveranser osv.).

Undvik de åtgärder som behöver använda både Adobe Campaign och den externa databasen så mycket som möjligt. Om du vill göra det kan du:

* Exportera Adobe Campaign-databasen till den externa databasen och kör åtgärderna endast från den externa databasen innan du importerar resultaten till Adobe Campaign igen.
* Samla in data från den externa Adobe Campaign-databasen och kör åtgärderna lokalt.

Om du vill utföra personalisering i leveranser med data från den externa databasen, samlar du in data som ska användas i ett arbetsflöde för att göra dem tillgängliga i en tillfällig tabell. Använd sedan data från den tillfälliga tabellen för att anpassa leveransen.

## Begränsningar {#limitations}

FDA-alternativet är underställt begränsningsskyddet för det externa databassystem som du använder.

Av prestandaskäl rekommenderar vi inte att du använder den här funktionen för att utföra enhetliga operationer (leveranspersonalisering, interaktionsmodul, realtid).
