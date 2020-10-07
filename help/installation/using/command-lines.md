---
title: Kommandorader
seo-title: Kommandorader
description: Kommandorader
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 5%

---


# Kommandorader{#command-lines}

Följande kommandorader kräver åtkomst till programservern. För distributioner som hanteras av Adobe kan dessa kommandon bara köras av Adobe.

## Skapa en instans {#creating-an-instance}

Det går att skapa instanser med kommandorader, med syntaxen:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(där **eng** och **fra** är möjliga värden för `[lang]` parametern)

Med kommandot **nlserver config -addinstance:instance1/demo*/eng** kan du skapa en instans med namnet **instance1** på engelska med DNS-maskdemo*.

## Deklarera en databas {#declaring-a-database}

Du kan associera en befintlig databas med en instans från kommandoraden med följande syntax:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Följande värden är möjliga för **`[rdbms]`** parametern:

* **postgresql**: för PostgreSQL,
* **Oracle**: för Oracle,
* **mssql**: för Microsoft SQL Server,
* **DB2**: för DB2-motorn.

Följande kommando konfigurerar **demoinstansen** med SQL-typservern **base6**, som är länkad till **kampanjkontot** och dess **lösenord** på **dbsrv** -servern:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

