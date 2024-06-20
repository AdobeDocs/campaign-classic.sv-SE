---
product: campaign
title: Kommandorader
description: Kommandorader
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%

---

# Kommandorader{#command-lines}



Följande kommandorader kräver åtkomst till programservern. För distributioner som hanteras av Adobe kan dessa kommandon bara köras av Adobe.

## Skapa en instans {#creating-an-instance}

Det går att skapa instanser med kommandorader, med syntaxen:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(där **eng** och **fra** är möjliga värden för `[lang]` parameter)

Kommandot **nlserver config -addinstance:instance1/demo&#42;/eng** gör att du kan skapa en instans med namnet **instance1** på engelska med DNS-maskdemo&#42;.

## Deklarera en databas {#declaring-a-database}

Du kan associera en befintlig databas med en instans från kommandoraden med följande syntax:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Följande värden är möjliga för **`[rdbms]`** parameter:

* **postgresql**: för PostgreSQL,
* **oracle**: för Oracle,
* **mssql**: för Microsoft SQL Server,

Följande kommando konfigurerar **demo** instans med SQL-typservern känd som **base6**, länkad till **kampanj** konto och dess **lösenord** på **dbsrv** server:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
