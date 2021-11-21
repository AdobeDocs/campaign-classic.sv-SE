---
product: campaign
title: Schema för en befintlig tabell
description: Schema för en befintlig tabell
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---

# Schema för en befintlig tabell{#schema-of-an-existing-table}

![](../../assets/v7-only.svg)

## Översikt {#overview}

När programmet behöver komma åt data från en befintlig tabell, en SQL-vy eller data från en fjärrdatabas skapar du dess schema i Adobe Campaign med följande data:

* Tabellnamn: Ange namnet på tabellen (med dess alias när en blink används) med attributet &quot;sqltable&quot;.
* schemanyckel: hänvisa till avstämningsfält,
* index: används för att generera frågor,
* Fälten och deras plats i XML-strukturen: fylla i endast de fält som används i programmet,
* länkar: om det finns kopplingar till andra tabeller i basen.

## Implementering {#implementation}

Om du vill skapa motsvarande schema använder du följande steg:

1. Redigera **[!UICONTROL Administration>Configuration>Data schemas]** noden i Adobe Campaign-trädet och klicka **[!UICONTROL New]** .
1. Välj **[!UICONTROL Access data from an existing table or an SQL view]** och klicka **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Välj tabellen eller den befintliga vyn:

   ![](assets/s_ncs_configuration_select_table.png)

1. Anpassa schemainnehållet efter dina behov.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Schemat måste fyllas i med attributet view=&quot;true&quot; på `<srcSchema>` rotelement för att inte skapa ett SQL-skript för tabellgenerering.

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

The **Åtkomst till federerade data - FDA** ger åtkomst till data som lagras i en extern databas.

Hur scheman ska konfigureras för att få åtkomst till data i en extern databas beskrivs i [den här sidan](../../installation/using/creating-data-schema.md).
