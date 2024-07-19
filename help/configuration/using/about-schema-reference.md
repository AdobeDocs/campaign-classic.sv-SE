---
product: campaign
title: Kom igång med scheman i Adobe Campaign
description: Lär dig hur du arbetar med scheman och utökar den konceptuella datamodellen i Adobe Campaign-databasen
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 1%

---

# Kom igång med scheman {#about-schema-reference}

## Vad är ett schema? {#what-is-a-schema}

I det här kapitlet beskrivs hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen för Adobe Campaign-databasen.

Mer information om inbyggda tabeller i Campaign och deras interaktion finns i datamodellen [Campaign Classic](about-data-model.md).

I Adobe Campaign beskrivs den fysiska och logiska strukturen för de data som finns i programmet i XML-format. Ett **schema** är ett XML-dokument som är associerat med en databastabell. Den definierar datastrukturen och beskriver tabellens SQL-definition:

* Tabellens namn
* Fält
* Index
* Länkar till andra tabeller

Här beskrivs också XML-strukturen som används för att lagra data:

* Element och attribut
* Elementhierarki
* Element- och attributtyper
* Standardvärden
* Etiketter, beskrivningar och andra egenskaper.

Med scheman kan du definiera en enhet i databasen. Det finns ett schema för varje entitet.

I följande bild visas schemats placering i Adobe Campaign datasystem:

![](assets/reference_schema_intro.png)

## Syntax för scheman {#syntax-of-schemas}

Schemats rotelement är **`<srcschema>`**. Den innehåller underelementen **`<element>`** och **`<attribute>`**.

Det första **`<element>`**-underelementet sammanfaller med entitetens rot.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Entitetens rotelement har samma namn som schemat.

![](assets/s_ncs_configuration_schema_and_entity.png)

**`<element>`**-taggarna definierar namnen på entitetselementen. **`<attribute>`** taggar i schemat definierar namnen på attributen i **`<element>`** -taggarna som de har länkats till.

## Identifiering av ett schema {#identification-of-a-schema}

Ett dataschema identifieras med sitt namn och namnutrymme.

Med ett namnutrymme kan du gruppera en uppsättning scheman efter intresseområde. Namnområdet **cus** används till exempel för kundspecifik konfiguration (**kunder**).

Identifieringsnyckeln för ett schema är en sträng som skapats med namnutrymmet och namnet avgränsat med ett kolon, till exempel: **cus:mottagare**.

>[!IMPORTANT]
>
>Namnutrymmets namn måste vara kortfattat och får endast innehålla tillåtna tecken enligt reglerna för XML-namngivning.
>
>Identifierare får inte börja med numeriska tecken.
>
>Följande namnutrymmen är reserverade för beskrivningar av de systementiteter som krävs för Adobe Campaign-programmets åtgärd och får inte användas: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.

