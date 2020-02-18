---
title: SQL Data Management
seo-title: SQL Data Management
description: SQL Data Management
seo-description: null
page-status-flag: never-activated
uuid: b6057496-2dd5-4289-96df-98378e4f0ae7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 18d6f5e1-308f-4080-b7c4-ebf836f74842
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# SQL Data Management{#sql-data-management}

Med **SQL Data Management** -aktiviteten kan du skriva egna SQL-skript för att skapa och fylla i arbetstabeller.

## Förutsättningar {#prerequisites}

Innan du konfigurerar aktiviteten bör du kontrollera att följande krav är uppfyllda:

* Aktiviteten är endast tillgänglig för fjärrdatakällor. Paketet **[!UICONTROL FDA]** (Federated Data Access) måste därför installeras på din instans (se [det här avsnittet](../../platform/using/about-fda.md)).
* Det utgående schemat måste finnas i databasen och vara länkat till en FDA-databas (mer information om datamodeller finns i [det här avsnittet](../../configuration/using/about-schema-reference.md)).
* Operatorn som kör arbetsflödet måste ha **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY (useSqlDmActivity)]** namngiven behörighet. Mer information om namngivna rättigheter finns i [det här avsnittet](../../platform/using/access-management.md#named-rights).

## Konfigurera SQL Data Management-aktiviteten {#configuring-the-sql-data-management-activity}

1. Ange aktiviteten **[!UICONTROL Label]**.
1. Markera det **[!UICONTROL External account]** som ska användas och markera sedan det **[!UICONTROL Outbound schema]** länkade till det här externa kontot.

   >[!CAUTION]
   >
   >Det utgående schemat är fast och kan inte redigeras.

1. Lägg till SQL-skriptet.

   >[!CAUTION]
   >
   >Det är SQL-skriptets skrivares ansvar att se till att SQL-skriptet fungerar och att dess referenser (fältnamn, etc.) är i enlighet med det utgående schemat.

   Om du vill läsa in en befintlig SQL-kod markerar du **[!UICONTROL The SQL script is contained in an entity stored in the database]** alternativet. SQL-skript måste skapas och lagras på menyn **[!UICONTROL Administration]** / **[!UICONTROL Configuration]** / **[!UICONTROL SQL scripts]** .

   I annat fall skriver eller kopierar och klistrar du in SQL-skriptet i det dedikerade området.

   ![](assets/sql_datamanagement.png)

   Med aktiviteten kan du använda följande variabler i skriptet:

   * **activity.tableName**: SQL-namn för utgående arbetstabell.
   * **task.inkommandeTransitionByName(&quot;name&quot;).tableName**: SQL-namn för arbetsregistret som medföljer den inkommande övergången som ska användas (övergången identifieras med sitt namn).

      >[!NOTE]
      >
      >Värdet (&#39;name&#39;) motsvarar **[!UICONTROL Name]** fältet från övergångsegenskaperna.

1. Om SQL-skriptet redan innehåller kommandon för att skapa en utgående arbetstabell avmarkerar du **[!UICONTROL Automatically create work table]** alternativet. I annat fall skapas en arbetstabell automatiskt när arbetsflödet körs.
1. Klicka **[!UICONTROL Ok]** för att bekräfta aktivitetskonfigurationen.

Aktiviteten är nu konfigurerad. Den är klar att köras i arbetsflödet.

>[!CAUTION]
>
>När aktiviteten har utförts är antalet utgående övergångsposter endast vägledande. Det kan variera beroende på SQL-skriptets komplexitet.
>  
>Om aktiviteten startas om körs hela skriptet från början, oavsett dess körningsstatus.

## SQL-skriptexempel {#sql-script-samples}

>[!NOTE]
>
>Skriptexemplen i det här avsnittet ska köras under PostgreSQL.

Med skriptet nedan kan du skapa en arbetstabell och infoga data i samma arbetstabell:

```
CREATE UNLOGGED TABLE <%= activity.tableName %> (
  iRecipientId INTEGER DEFAULT 0,
  sFirstName VARCHAR(100),
  sMiddleName VARCHAR(100),
  sLastName VARCHAR(100),
  sEmail VARCHAR(100)
);

INSERT INTO <%= activity.tableName %>
SELECT iRecipientId, sFirstName, sMiddleName, sLastName, sEmail
FROM nmsRecipient
GROUP BY iRecipientId, sFirstName, sMiddleName, sLastName, sEmail;
```

Nedan kan du utföra en CTAS-åtgärd (CREATE TABLE AS SELECT) och skapa ett arbetstabellindex:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT iRecipientId, sEmail, sFirstName, sLastName, sMiddleName
FROM nmsRecipient
WHERE sEmail IS NOT NULL
GROUP BY iRecipientId, sEmail, sFirstName, sLastName, sMiddleName;

CREATE INDEX ON <%= activity.tableName %> (sEmail);

ANALYZE <%= activity.tableName %> (sEmail);
```

Nedanför skript kan du sammanfoga två arbetsregister:

```
CREATE TABLE <%= activity.tableName %>
AS SELECT i1.sFirstName, i1.sLastName, i2.sEmail
FROM <%= task.incomingTransitionByName('input1').tableName %> i1
JOIN <%= task.incomingTransitionByName('input2').tableName %> i2 ON (i1.id = i2.id)
```

