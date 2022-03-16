---
product: campaign
title: Kom igång med åtkomst till federerade data
description: Lär dig hur du får åtkomst till och bearbetar data i en extern databas
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Kom igång med åtkomst till federerade data {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign tillhandahåller **Åtkomst till federerade data** (FDA) för att bearbeta information som lagras i en eller flera externa databaser: kan du få åtkomst till externa data utan att ändra datastrukturen i Adobe Campaign.

## Förhandskrav {#operating-principle}

Med FDA-alternativet kan du utöka din datamodell i en tredjepartsdatabas. Det identifierar automatiskt strukturen för måltabellerna och använder data från SQL-källorna.

För att kunna använda den här funktionen anges följande krav:

* **Konfiguration**: listan med kompatibla externa databaser beror på din [värdmodell](../../installation/using/hosting-models.md).
* **Extern databasversion**: du behöver en extern databas som är kompatibel med Adobe Campaign FDA-modulen.

   Listan över databassystem och kompatibla versioner per värdmodell finns i Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Behörigheter**: användarna måste också ha [nödvändiga behörigheter](../../installation/using/remote-database-access-rights.md) i Adobe Campaign och i den externa databasen.

