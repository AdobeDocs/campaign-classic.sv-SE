---
product: campaign
title: Åtkomst till en extern databas
description: Lär dig hur du får åtkomst till och bearbetar data i en extern databas
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# Kom igång med federerad dataåtkomst {#about-federated-data-access}

Adobe Campaign tillhandahåller alternativet **FDA (Federated Data Access**) för att bearbeta information som lagras i en eller flera externa databaser: kan du få åtkomst till externa data utan att ändra datastrukturen i Adobe Campaign.

## Förutsättningar {#operating-principle}

Med FDA-alternativet kan du utöka din datamodell i en tredjepartsdatabas. Den identifierar automatiskt strukturen för måltabellerna och använder data från SQL-källorna.

För att kunna använda den här funktionen anges följande krav:

* **Konfiguration**: förutom för Snowflake, behöver du en  **lokal** eller  **** överbryggningsmodell för att konfigurera Federated Data Access. [Läs mer](../../installation/using/hosting-models.md)
* **Extern databasversion**: du behöver en extern databas som är kompatibel med Adobe Campaign FDA-modulen. Listan över databassystem och kompatibla versioner finns i Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Behörigheter**: -användare måste också ha  [nödvändig ](../../installation/using/remote-database-access-rights.md) behörighet i Adobe Campaign och i den externa databasen.

