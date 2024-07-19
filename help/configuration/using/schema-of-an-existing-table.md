---
product: campaign
title: Schema för en befintlig tabell
description: Schema för en befintlig tabell
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 7%

---

# Schema för en befintlig tabell{#schema-of-an-existing-table}

## Översikt {#overview}

När programmet behöver komma åt data från en befintlig tabell, en SQL-vy eller data från en fjärrdatabas skapar du dess schema i Adobe Campaign med följande data:

* Tabellens namn: Ange tabellens namn (med dess alias när en blink används) med attributet &quot;sqltable&quot;.
* schemanyckel: referera till avstämningsfält,
* index: används för att generera frågor,
* Fälten och deras plats i XML-strukturen: fyll endast i de fält som används i programmet,
* länkar: om det finns kopplingar till andra tabeller i basen.

## Implementering {#implementation}

Om du vill skapa motsvarande schema använder du följande steg:

1. Redigera noden **[!UICONTROL Administration>Configuration>Data schemas]** i Adobe Campaign-trädet och klicka på **[!UICONTROL New]** .
1. Välj alternativet **[!UICONTROL Access data from an existing table or an SQL view]** och klicka på **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Välj tabellen eller den befintliga vyn:

   ![](assets/s_ncs_configuration_select_table.png)

1. Anpassa schemainnehållet efter dina behov.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Schemat måste fyllas i med attributet view=&quot;true&quot; i rotelementet `<srcSchema>` för att inte SQL-skript för att skapa tabeller.

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

Alternativet **Åtkomst av federerade data - FDA** ger dig åtkomst till data som lagras i en extern databas.

Den konfiguration som ska utföras på scheman för att komma åt data i en extern databas beskrivs på [den här sidan](../../installation/using/creating-data-schema.md).
