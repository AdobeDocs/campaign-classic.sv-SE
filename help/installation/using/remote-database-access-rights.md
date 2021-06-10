---
product: campaign
title: Behörigheter för åtkomst till en extern databas
description: Behörigheter för extern databasåtkomst
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 1312f7c319c96851bc83ae21501164e2688d0dff
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 1%

---

# Åtkomsträttigheter till fjärrdatabas {#remote-database-access-rights}

För det första, så att användaren kan utföra åtgärder på en extern databas via FDA, måste den senare ha en specifik namngiven behörighet i Adobe Campaign.

1. Markera noden **[!UICONTROL Administration > Access Management > Named Rights]** i Adobe Campaign Utforskaren.
1. Skapa en ny rättighet genom att ange den valda etiketten.
1. Fältet **[!UICONTROL Name]** måste ha följande format **användare:base@server**, där :

   * **** motsvarar namnet på användaren i den externa databasen.
   * **basecorresponds** med namnet på den externa databasen.
   * **** servermotsvarar namnet på den externa databasservern.

      >[!NOTE]
      >
      >Delen **:base** är valfri i Oraclet.

1. Spara den namngivna höger och länka den sedan till den valda användaren från noden **[!UICONTROL Administration > Access Management > Operators]** i Adobe Campaign Explorer.

Om du sedan vill bearbeta data i en extern databas måste Adobe Campaign-användaren ha minst skrivbehörighet för databasen för att kunna skapa arbetstabeller. Dessa tas bort automatiskt av Adobe Campaign.

I allmänhet är följande rättigheter nödvändiga:

* **CONNECT**: anslutning till fjärrdatabasen,
* **LÄS data**: skrivskyddad åtkomst till tabeller som innehåller kunddata,
* **LÄS &#39;MetaData&#39;**: åtkomst till serverns datakataloger för att få fram tabellstrukturen,
* **LADDA**: massinläsning i arbetstabeller (krävs vid arbete med samlingar och kopplingar),
* **CREATE/** DROP **for TABLE/INDEX/PROCEDURE/FUNCTION** (endast för arbetstabeller som genererats av Adobe Campaign),
* **EXPLAIN**  (rekommenderas): för övervakning av prestanda vid problem,
* **SKRIV data**  (beroende på integrationsscenariot).

Databasadministratören måste se till att dessa rättigheter matchar de rättigheter som är specifika för varje databasmotor. Mer information finns i avsnittet nedan.

## FDA-rättigheter {#fda-rights}

|   | Snowflake | Skift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Ansluter till fjärrdatabas** | ANVÄNDNING I LAGERHUS, ANVÄNDNING I DATABAS OCH ANVÄNDNING I SCHEMABEHÖRIGHETER | Skapa en användare som är länkad till AWS-kontot | SKAPA SESSIONSprivilegium | CONNECT behörighet | CONNECT privilegium | Skapa en användare som är bunden till en fjärrvärddator som har ALLA BEHÖRIGHETER |
| **Skapa tabeller** | Behörighet SKAPA TABELL PÅ SCHEMA | SKAPA privilegium | Privilegium SKAPA TABELL | SKAPA TABELLBEHÖRIGHET | SKAPA privilegium | SKAPA privilegium |
| **Skapa index** | N/A | SKAPA privilegium | INDEX- eller CREATE EVENTUELL INDEX-BEHÖRIGHET | ALTERNATIVbehörighet | SKAPA privilegium | INDEX-privilegium |
| **Skapa funktioner** | SKAPA FUNKTION PÅ SCHEMABEHÖRIGHET | ANVÄNDNING PÅ SPRÅKPLAN-plypthonu-privilegium för att kunna anropa externa python-skript | SKAPA PROCEDUR ELLER SKAPA VALFRITT BEHÖRIGHET | SKAPA FUNKTIONSTILLSTÅND | Behörighet att använda | SKAPA ROUTINprivilegium |
| **Skapa procedurer** | Ej tillämpligt | ANVÄNDNING PÅ SPRÅKPLAN-plypthonu-privilegium för att kunna anropa externa python-skript | SKAPA PROCEDUR ELLER SKAPA VALFRITT BEHÖRIGHET | SKAPA PROCESSTILLSTÅND | Behörighet för ANVÄNDNING (procedurer är funktioner) | SKAPA ROUTINprivilegium |
| **Ta bort objekt (tabeller, index, funktioner, procedurer)** | Äga objektet | Äga objektet eller vara superanvändare | DROP ANY &lt; object > privilege | ALTERNATIVbehörighet | Tabell: äger tabellindexet: äger indexfunktionen: äger funktionen | DROP-privilegium |
| **Övervaka körningar** | MONITOR-behörighet för det begärda objektet | Ingen behörighet krävs för kommandot EXPLAIN | Behörighet INSERT och SELECT samt nödvändiga privilegier för att köra den sats som EXPLAIN-planen baseras på | SHOWPLAN-behörighet | Inga privilegier krävs för att använda EXPLAIN-programsatsen | VÄLJ privilegium |
| **Skriver data** | INSERT- och/eller UPDATE-behörigheter (beroende på skrivåtgärd) | INSERT- och UPDATE-behörigheter | INFOGA OCH UPPDATERA ELLER INFOGA OCH UPPDATERA VALFRITT TABELLBEHÖRIGHET | INFOGA- och UPPDATERINGSbehörigheter | INSERT- och UPDATE-behörigheter | INSERT- och UPDATE-behörigheter |
| **Läsa in data i tabeller** | SKAPA SCENEN I SCHEMA, MARKERA OCH INFOGA i målregisterprivilegier | VÄLJ OCH INFOGA BEHÖRIGHETER | VÄLJ OCH INFOGA BEHÖRIGHETER | INFOGA, ADMINISTRERA BULK-ÅTGÄRDER OCH ALTER TABLE-behörigheter | VÄLJ OCH INFOGA BEHÖRIGHETER | FILE-privilegium |
| **Åtkomst till klientdata** | VÄLJ BEHÖRIGHET FÖR (FRAMTIDA) TABELL(ER) ELLER VY(ER) | VÄLJ privilegium | VÄLJ ELLER VÄLJ ETT TABELLprivilegium | VÄLJ behörighet | VÄLJ privilegium | VÄLJ privilegium |
| **Åtkomst till metadata** | VÄLJ BEHÖRIGHET FÖR INFORMATION_SCHEMA SCHEMA | VÄLJ privilegium | Ingen behörighet krävs för att använda programsatsen DESCRIBE | VISA DEFINITIONSTILLSTÅND | Det krävs inget privilegium för att använda kommandot &quot;\d table&quot; | VÄLJ privilegium |

|   | DB2 UDB | teradata | InfiniDB | sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Ansluter till fjärrdatabas** | CONNECT | CONNECT privilegium | Skapa en användare som är bunden till en fjärrvärddator som har ALLA BEHÖRIGHETER | Ingen behörighet krävs för programsatsen CONNECT | Inget privilegium krävs | CONNECT privilegium |
| **Skapa tabeller** | CREATETAB-utfärdare | CREATE TABLE or TABLE keyword | SKAPA privilegium | RESURSutfärdare och SKAPA behörighet | TABELLprivilegium | SKAPA privilegium |
| **Skapa index** | INDEX-privilegium | CREATE INDEX or INDEX keyword | INDEX-privilegium | RESURSutfärdare och SKAPA behörighet | INDEX-privilegium | SKAPA privilegium |
| **Skapa funktioner** | IMPLICIT_SCHEMA-behörighet eller CREATEIN-behörighet | CREATE FUNCTION or FUNCTION, nyckelord | SKAPA ROUTINprivilegium | RESURSANSVARIG eller DBA-myndighet för Java-funktioner | BEHÖRIGHET FÖR FUNKTION | SKAPA FUNKTIONSHINDER |
| **Skapa procedurer** | IMPLICIT_SCHEMA-behörighet eller CREATEIN-behörighet | SKAPA nyckelordet PROCEDUR eller PROCEDURE | SKAPA ROUTINprivilegium | RESURSANSVARIG | BEHÖRIGHET FÖR FÖRFARANDE | SKAPA FUNKTIONSHINDER |
| **Ta bort objekt (tabeller, index, funktioner, procedurer)** | DROPIN-behörighet eller BEHÖRIGHET för KONTROLL eller ägande av objektet | DROP &lt; object > eller objektrelaterat nyckelord | DROP-privilegium | Äger objektet eller DBA-utfärdaren | DROP-privilegium | Äga objektet |
| **Övervaka körningar** | FÖRKLARING | Inga privilegier krävs för att använda EXPLAIN-programsatsen | VÄLJ privilegium | Endast en systemadministratör kan köra sp_showplan | Inga privilegier krävs för att använda EXPLAIN-programsatsen | Inga privilegier krävs för att använda EXPLAIN-programsatsen |
| **Skriver data** | INFOGA- och UPPDATERINGSbehörigheter eller DATAACCESS-utfärdare | INSERT- och UPDATE-behörigheter | INSERT- och UPDATE-behörigheter | INFOGA- och UPPDATERINGSbehörigheter | INSERT- och UPDATE-behörigheter | INSERT- och UPDATE-behörigheter |
| **Läsa in data i tabeller** | BELASTNINGSTILLSTÅND | SELECT- och INSERT-behörighet för att använda COPY TO- respektive COPY FROM-satser | FILE-privilegium | Var ägare av tabellen eller behörigheten ALTER. Beroende på alternativet -gl kan LOAD TABLE bara utföras om användaren har DBA-behörighet | VÄLJ OCH INFOGA BEHÖRIGHETER | VÄLJ OCH INFOGA BEHÖRIGHETER |
| **Åtkomst till klientdata** | INSERT/UPDATE-behörighet eller DATAACCESS-utfärdare | VÄLJ privilegium | VÄLJ privilegium | VÄLJ behörighet | VÄLJ privilegium | VÄLJ privilegium |
| **Åtkomst till metadata** | Ingen behörighet krävs för att använda programsatsen DESCRIBE | VISA privilegium | VÄLJ privilegium | Ingen behörighet krävs för att använda programsatsen DESCRIBE | Det krävs inget privilegium för att använda kommandot &quot;\d table&quot; | Ingen behörighet krävs för att använda kommandot VISA |
