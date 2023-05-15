---
product: campaign
title: Kom igång med åtkomst till federerade data
description: Lär dig hur du får åtkomst till och bearbetar data i en extern databas
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Kom igång med åtkomst till federerade data {#about-federated-data-access}



Adobe Campaign tillhandahåller **Åtkomst till federerade data** (FDA) för att bearbeta information som lagras i en eller flera externa databaser: kan du få åtkomst till externa data utan att ändra datastrukturen i Adobe Campaign.

## Förhandskrav {#operating-principle}

Med FDA-alternativet kan du utöka din datamodell i en tredjepartsdatabas. Det identifierar automatiskt strukturen för måltabellerna och använder data från SQL-källorna.

För att kunna använda den här funktionen anges följande krav:

* **Konfiguration**: listan med kompatibla externa databaser beror på din [värdmodell](../../installation/using/hosting-models.md).
* **Extern databasversion**: du behöver en extern databas som är kompatibel med Adobe Campaign FDA-modulen.

   Listan över databassystem och kompatibla versioner per värdmodell finns i Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Behörigheter**: användarna måste också ha [nödvändiga behörigheter](../../installation/using/remote-database-access-rights.md) i Adobe Campaign och i den externa databasen.

