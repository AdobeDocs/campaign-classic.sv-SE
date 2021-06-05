---
product: campaign
title: Om schemareferens i Adobe Campaign Classic
description: Lär dig hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen för Adobe Campaign Classic-databasen.
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 7%

---

# Om schemareferens{#about-schema-reference}

I det här kapitlet beskrivs hur du konfigurerar tilläggsscheman för att utöka Adobe Campaign-databasens konceptuella datamodell.

Mer information om inbyggda tabeller i Campaign och hur de fungerar finns i datamodellen [Campaign Classic](https://helpx.adobe.com/se/campaign/kb/acc-datamodel.html).

Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign och som kallas **schema**.

Ett schema är ett XML-dokument som är associerat med en databastabell. Den definierar datastrukturen och beskriver tabellens SQL-definition:

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

**`<element>`**-taggarna definierar namnen på entitetselementen. **`<attribute>`** -taggar i schemat definierar namnen på attributen i de  **`<element>`** taggar som de har länkats till.

## Identifiering av ett schema {#identification-of-a-schema}

Ett dataschema identifieras med sitt namn och namnutrymme.

Med ett namnutrymme kan du gruppera en uppsättning scheman efter intresseområde. Namnutrymmet **cus** används till exempel för kundspecifik konfiguration (**kunder**).

Identifieringsnyckeln för ett schema är en sträng som byggts med namnutrymmet och namnet avgränsat med ett kolon. till exempel: **cus:mottagare**.

>[!IMPORTANT]
>
>Namnutrymmets namn måste vara kortfattat och får endast innehålla tillåtna tecken enligt reglerna för XML-namngivning.
>
>Identifierare får inte börja med numeriska tecken.
>
>Följande namnutrymmen är reserverade för beskrivningar av de systemenheter som krävs för att Adobe Campaign-programmet ska fungera och får inte användas: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm&lt;a1 3/>,** xxl **.**

