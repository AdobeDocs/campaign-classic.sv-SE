---
title: Schema för en befintlig tabell
seo-title: Schema för en befintlig tabell
description: Schema för en befintlig tabell
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Schema för en befintlig tabell{#schema-of-an-existing-table}

## Översikt {#overview}

När programmet behöver komma åt data från en befintlig tabell, en SQL-vy eller data från en fjärrdatabas skapar du schemat i Adobe Campaign med följande data:

* Tabellnamn: Ange namnet på tabellen (med dess alias när en blink används) med attributet &quot;sqltable&quot;.
* schemanyckel: hänvisa till avstämningsfält,
* index: används för att generera frågor,
* Fälten och deras plats i XML-strukturen: fylla i endast de fält som används i programmet,
* länkar: om det finns kopplingar till andra tabeller i basen.

## Implementering {#implementation}

Om du vill skapa motsvarande schema använder du följande steg:

1. Redigera noden **[!UICONTROL Administration>Configuration>Data schemas]** i Adobe Campaign-trädet och klicka på **[!UICONTROL New]** .
1. Markera **[!UICONTROL Access data from an existing table or an SQL view]** alternativet och klicka på **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Välj tabellen eller den befintliga vyn:

   ![](assets/s_ncs_configuration_select_table.png)

1. Anpassa schemainnehållet efter dina behov.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Schemat måste fyllas i med attributet view=&quot;true&quot; på `<srcSchema>` rotelementet för att inte SQL-skript ska kunna skapas för tabeller.

**Exempel** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Åtkomst till en extern databas {#accessing-an-external-database}

Med alternativet **Federated Data Access - FDA** får du åtkomst till data som lagras i en extern databas.

Hur scheman ska konfigureras för att få åtkomst till data i en extern databas beskrivs på [den här sidan](../../platform/using/accessing-an-external-database.md#creating-the-data-schema).
