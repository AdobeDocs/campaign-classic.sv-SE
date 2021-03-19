---
solution: Campaign Classic
product: campaign
title: Kommandorader
description: Kommandorader
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Kommandorader{#command-lines}

Följande kommandorader kräver åtkomst till programservern. För distributioner som hanteras av Adobe kan dessa kommandon bara köras av Adobe.

## Skapa en instans {#creating-an-instance}

Det går att skapa instanser med kommandorader, med syntaxen:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(där **eng** och **fra** är möjliga värden för parametern `[lang]`)

Med kommandot **nlserver config -addinstance:instance1/demo*/eng** kan du skapa en instans med namnet **instance1** på engelska med DNS-maskdemo*.

## Deklarera en databas {#declaring-a-database}

Du kan associera en befintlig databas med en instans från kommandoraden med följande syntax:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Följande värden är möjliga för parametern **`[rdbms]`**:

* **postgresql**: för PostgreSQL,
* **oracle**: för Oracle,
* **mssql**: för Microsoft SQL Server,
* **DB2**: för DB2-motorn.

Följande kommando konfigurerar **demo**-instansen med SQL-typservern **base6**, som är länkad till **kampanjkontot** och dess **lösenord** på **dbsrv**-servern:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

