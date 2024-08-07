---
product: campaign
title: Kom igång med åtkomst till federerade data
description: Lär dig hur du får åtkomst till och bearbetar data i en extern databas
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Kom igång med åtkomst till federerade data {#about-federated-data-access}



Adobe Campaign tillhandahåller alternativet **FDA (Federated Data Access**) för att bearbeta information som lagras i en eller flera externa databaser: du kan få åtkomst till externa data utan att ändra strukturen för Adobe Campaign-data.

## Förhandskrav {#operating-principle}

Med FDA-alternativet kan du utöka din datamodell i en tredjepartsdatabas. Den identifierar automatiskt strukturen för måltabellerna och använder data från SQL-källorna.

För att kunna använda den här funktionen anges följande krav:

* **Konfiguration**: listan över kompatibla externa databaser beror på [värdmodellen](../../installation/using/hosting-models.md).
* **Extern databasversion**: Du måste ha en extern databas som är kompatibel med Adobe Campaign FDA-modulen.

  Listan över databassystem och kompatibla versioner per värdmodell finns i Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Behörigheter**: användare måste också ha de [nödvändiga behörigheterna](../../installation/using/remote-database-access-rights.md) i Adobe Campaign och i den externa databasen.

