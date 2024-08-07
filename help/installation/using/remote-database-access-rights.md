---
product: campaign
title: Behörigheter för åtkomst till en extern databas
description: Behörigheter för extern databasåtkomst
feature: Installation, Instance Settings, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Åtkomsträttigheter till fjärrdatabas {#remote-database-access-rights}



För det första, så att användaren kan utföra åtgärder på en extern databas via FDA, måste den senare ha en specifik namngiven behörighet i Adobe Campaign.

1. Markera noden **[!UICONTROL Administration > Access Management > Named Rights]** i Adobe Campaign Utforskaren.
1. Skapa en ny rättighet genom att ange den valda etiketten.
1. Fältet **[!UICONTROL Name]** måste ha följande format: **user:base@server**, där:

   * **användare** motsvarar namnet på användaren i den externa databasen.
   * **base** motsvarar namnet på den externa databasen.
   * **server** motsvarar namnet på den externa databasservern.

     >[!NOTE]
     >
     >Delen **:base** är valfri i Oraclet.

1. Spara den namngivna rättigheten och länka den sedan till den valda användaren från noden **[!UICONTROL Administration > Access Management > Operators]** i Adobe Campaign Utforskaren.

Om du sedan vill bearbeta data i en extern databas måste Adobe Campaign-användaren ha minst skrivbehörighet för databasen för att kunna skapa arbetstabeller. Dessa tas bort automatiskt av Adobe Campaign.

I allmänhet är följande rättigheter nödvändiga:

* **CONNECT**: anslutning till fjärrdatabasen,
* **LÄS data**: skrivskyddad åtkomst till tabeller som innehåller kunddata,
* **READ &#39;MetaData&#39;**: åtkomst till serverns datakataloger för att hämta tabellstrukturen,
* **LOAD**: massinläsning i arbetstabeller (krävs när du arbetar med samlingar och kopplingar),
* **CREATE/DROP** för **TABLE/INDEX/PROCEDURE/FUNCTION** (endast för arbetstabeller som genererats av Adobe Campaign),
* **EXPLAIN** (rekommenderas): för övervakning av prestanda vid problem,
* **SKRIV data** (beroende på integrationsscenariot).

Databasadministratören måste se till att dessa rättigheter matchar de rättigheter som är specifika för varje databasmotor. Mer information finns i avsnittet nedan.

## FDA-rättigheter {#fda-rights}

|   | Snowflake | Skift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Ansluter till fjärrdatabas** | ANVÄNDNING I LAGERHUS, ANVÄNDNING I DATABAS OCH ANVÄNDNING I SCHEMABEHÖRIGHETER | Skapa en användare som är länkad till AWS-kontot | SKAPA SESSIONSprivilegium | CONNECT behörighet | CONNECT privilegium | Skapa en användare som är bunden till en fjärrvärddator som har ALLA BEHÖRIGHETER |
| **Skapar tabeller** | Behörighet SKAPA TABELL PÅ SCHEMA | SKAPA privilegium | Privilegium SKAPA TABELL | SKAPA TABELLBEHÖRIGHET | SKAPA privilegium | SKAPA privilegium |
| **Skapar index** | N/A | SKAPA privilegium | INDEX- eller CREATE EVENTUELL INDEX-BEHÖRIGHET | ALTERNATIVbehörighet | SKAPA privilegium | INDEX-privilegium |
| **Skapar funktioner** | SKAPA FUNKTION PÅ SCHEMABEHÖRIGHET | ANVÄNDNING PÅ SPRÅKPLAN-plypthonu-privilegium för att kunna anropa externa python-skript | SKAPA PROCEDUR ELLER SKAPA VALFRITT BEHÖRIGHET | SKAPA FUNKTIONSTILLSTÅND | Behörighet att använda | SKAPA ROUTINprivilegium |
| **Skapar procedurer** | N/A | ANVÄNDNING PÅ SPRÅKPLAN-plypthonu-privilegium för att kunna anropa externa python-skript | SKAPA PROCEDUR ELLER SKAPA VALFRITT BEHÖRIGHET | SKAPA PROCESSTILLSTÅND | Behörighet för ANVÄNDNING (procedurer är funktioner) | SKAPA ROUTINprivilegium |
| **Tar bort objekt (tabeller, index, funktioner, procedurer)** | Äga objektet | Äga objektet eller vara superanvändare | DROP ANY &lt; object > privilege | ALTERNATIVbehörighet | Tabell: äger tabellindexet: äger indexfunktionen: äger funktionen | DROP-privilegium |
| **Övervaka körningar** | MONITOR-behörighet för det begärda objektet | Ingen behörighet krävs för kommandot EXPLAIN | Behörighet INSERT och SELECT samt nödvändiga privilegier för att köra den sats som EXPLAIN-planen baseras på | SHOWPLAN-behörighet | Inga privilegier krävs för att använda EXPLAIN-programsatsen | VÄLJ privilegium |
| **Skriver data** | INSERT- och/eller UPDATE-behörigheter (beroende på skrivåtgärd) | INSERT- och UPDATE-behörigheter | INFOGA OCH UPPDATERA ELLER INFOGA OCH UPPDATERA VALFRITT TABELLBEHÖRIGHET | INFOGA- och UPPDATERINGSbehörigheter | INSERT- och UPDATE-behörigheter | INSERT- och UPDATE-behörigheter |
| **Läser in data i tabeller** | SKAPA SCENEN I SCHEMA, MARKERA OCH INFOGA i målregisterprivilegier | VÄLJ OCH INFOGA BEHÖRIGHETER | VÄLJ OCH INFOGA BEHÖRIGHETER | INFOGA, ADMINISTRERA BULK-ÅTGÄRDER OCH ALTER TABLE-behörigheter | VÄLJ OCH INFOGA BEHÖRIGHETER | FILE-privilegium |
| **Åtkomst till klientdata** | VÄLJ BEHÖRIGHET FÖR (FRAMTIDA) TABELL(ER) ELLER VY(ER) | VÄLJ privilegium | VÄLJ ELLER VÄLJ ETT TABELLprivilegium | VÄLJ behörighet | VÄLJ privilegium | VÄLJ privilegium |
| **Åtkomst till metadata** | VÄLJ BEHÖRIGHET FÖR INFORMATION_SCHEMA SCHEMA | VÄLJ privilegium | Ingen behörighet krävs för att använda programsatsen DESCRIBE | VISA DEFINITIONSTILLSTÅND | Inget privilegium krävs för att använda kommandot &quot;\d table&quot; | VÄLJ privilegium |

|   | Teradata | InfiniDB | Sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|
| **Ansluter till fjärrdatabas** | CONNECT privilegium | Skapa en användare som är bunden till en fjärrvärddator som har ALLA BEHÖRIGHETER | Ingen behörighet krävs för programsatsen CONNECT | Inget privilegium krävs | CONNECT privilegium |
| **Skapar tabeller** | CREATE TABLE or TABLE keyword | SKAPA privilegium | RESURSutfärdare och SKAPA behörighet | TABELLprivilegium | SKAPA privilegium |
| **Skapar index** | CREATE INDEX or INDEX keyword | INDEX-privilegium | RESURSutfärdare och SKAPA behörighet | INDEX-privilegium | SKAPA privilegium |
| **Skapar funktioner** | CREATE FUNCTION or FUNCTION, nyckelord | SKAPA ROUTINprivilegium | RESURSANSVARIG eller DBA-myndighet för Java-funktioner | BEHÖRIGHET FÖR FUNKTION | SKAPA FUNKTIONSBEHÖRIGHET |
| **Skapar procedurer** | SKAPA nyckelordet PROCEDUR eller PROCEDURE | SKAPA ROUTINprivilegium | RESURSANSVARIG | BEHÖRIGHET FÖR FÖRFARANDE | SKAPA FUNKTIONSBEHÖRIGHET |
| **Tar bort objekt (tabeller, index, funktioner, procedurer)** | DROP &lt; object > eller objektrelaterat nyckelord | DROP-privilegium | Äger objektet eller DBA-utfärdaren | DROP-privilegium | Äga objektet |
| **Övervaka körningar** | Inga privilegier krävs för att använda EXPLAIN-programsatsen | VÄLJ privilegium | Endast en systemadministratör kan köra sp_showplan | Inga privilegier krävs för att använda EXPLAIN-programsatsen | Inga privilegier krävs för att använda EXPLAIN-programsatsen |
| **Skriver data** | INSERT- och UPDATE-behörigheter | INSERT- och UPDATE-behörigheter | INFOGA- och UPPDATERINGSbehörigheter | INSERT- och UPDATE-behörigheter | INSERT- och UPDATE-behörigheter |
| **Läser in data i tabeller** | SELECT- och INSERT-behörighet för att använda COPY TO- respektive COPY FROM-satser | FILE-privilegium | Var ägare av tabellen eller behörigheten ALTER. Beroende på alternativet -gl kan LOAD TABLE bara utföras om användaren har DBA-behörighet | VÄLJ OCH INFOGA BEHÖRIGHETER | VÄLJ OCH INFOGA BEHÖRIGHETER |
| **Åtkomst till klientdata** | VÄLJ privilegium | VÄLJ behörighet | VÄLJ privilegium | VÄLJ privilegium |
| **Åtkomst till metadata** | VISA privilegium | VÄLJ privilegium | Ingen behörighet krävs för programsatsen DESCRIBE | Inget privilegium krävs för att använda kommandot &quot;\d table&quot; | Ingen behörighet krävs för att använda kommandot VISA |
