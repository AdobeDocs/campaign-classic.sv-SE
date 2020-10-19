---
title: Rekommendationer för Campaign Classic-databasen
description: Databasrekommendationer
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---


# Databas{#database}

Databasservern kan köras på ett givet operativsystem oavsett vilket operativsystem som används av programservern eller -servrarna, förutsatt att det finns nätverksanslutningar mellan dem.

Databasserverns operativsystem är inte viktigt så länge det finns en anslutning till de olika komponenterna i Adobe Campaign.

Kontrollera även avsnittet [Databasåtkomstlager](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) .

## Microsoft SQL Server {#microsoft-sql-server}

Den inbyggda klienten måste vara installerad på Adobe Campaign programservrar.

Du kan söka efter den inbyggda klienten på servern via ODBC-drivrutinens konfigurationspanel under **SQL Server Native Client 11.0**.

Följande åtkomst-DLL måste finnas: **sqlncli11.dll**.

Åtkomst-DLL:er finns på Microsofts webbplats.

>[!NOTE]
>
>Åtkomst till Microsoft SQL Server från en programserver som körs i Linux stöds inte.

## Oracle {#oracle}

>[!NOTE]
>
>Kolumnnamn med flerbytetecken stöds inte.

Parametrarna **NLS_NCHAR_CHARACTERSET** och **NLS_CHARACTERSET** måste vara korrekt konfigurerade för att databasen ska fungera i Unicode eller ANSI.

Adobe Campaign använder Oracle-standardkodning. Om du använder annan kodning kan kompatibilitetsproblem uppstå: Kontakta då teknisk support.

Om du vill veta mer om kodningen använder du följande **sqlplus** -kommando:

```
SELECT * FROM nls_database_parameters ;
```

* För en Unicode-installation stöds följande kodningar:

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* För en ANSI-installation (icke-Unicode) stöds endast följande kodning:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Om du vill logga in på **sqlplus** använder du användarprofilen i Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

Du kan även referera till [Oracle Client i Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Vi rekommenderar att du installerar UTF-8-stödet när du installerar databasmotorn. På så sätt kan du skapa Unicode-databaser.

**Relaterat ämne**

* [Alternativet Ologgad i Adobe Campaign Classic-tabeller](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
