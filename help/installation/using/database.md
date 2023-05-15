---
product: campaign
title: Rekommendationer för Campaign Classic-databasen
description: Databasrekommendationer
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-on-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 0429c3608fbcec98a397cc17fd45cd173cf64b6e
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---

# Databas{#database}



Databasservern kan köras på ett givet operativsystem oavsett vilket operativsystem som används av programservern eller -servrarna, förutsatt att det finns nätverksanslutningar mellan dem.

Databasserverns operativsystem är inte viktigt så länge det finns en anslutning till de olika komponenterna i Adobe Campaign.

Kontrollera även [Åtkomstlager för databaser](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) -avsnitt.

## Microsoft SQL Server {#microsoft-sql-server}

Den inbyggda klienten måste vara installerad på Adobe Campaign programservrar.

Du kan söka efter den inbyggda klienten på servern via ODBC-drivrutinens konfigurationspanel, under **SQL Server Native Client 11.0**.

Följande åtkomst-DLL måste finnas: **sqlncli11.dll**.

Åtkomst-DLL:er finns på Microsoft webbplats.

>[!NOTE]
>
>Åtkomst till Microsoft SQL Server från en programserver som körs i Linux stöds inte.

## Oracle {#oracle}

>[!NOTE]
>
>Kolumnnamn med flerbytetecken stöds inte.

The **NLS_NCHAR_CHARACTERSET** och **NLS_CHARACTERSET** parametrar måste vara korrekt konfigurerade för att databasen ska fungera i Unicode eller ANSI.

Adobe Campaign använder standardkodning för Oraclen. Om du använder annan kodning kan kompatibilitetsproblem uppstå: Kontakta då teknisk support.

Om du vill veta mer om kodningen använder du följande **sqlplus** kommando:

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

Logga in på **sqlplus** använder du Oraclets användarprofil:

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
