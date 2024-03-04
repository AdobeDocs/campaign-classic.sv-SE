---
product: campaign
title: Kom igång med scheman i Adobe Campaign
description: Lär dig hur du arbetar med scheman och utökar den konceptuella datamodellen i Adobe Campaign-databasen
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: bd1007ffcfa58ee60fdafa424c7827e267845679
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 1%

---

# Kom igång med scheman {#about-schema-reference}

## Vad är ett schema? {#what-is-a-schema}

I det här kapitlet beskrivs hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen för Adobe Campaign-databasen.

Om du vill få en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion kan du läsa [Campaign Classicens datamodell](about-data-model.md).

I Adobe Campaign beskrivs den fysiska och logiska strukturen för de data som finns i programmet i XML-format. A **schema** är ett XML-dokument som är associerat med en databastabell. Den definierar datastrukturen och beskriver tabellens SQL-definition:

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

Schemats rotelement är **`<srcschema>`**. Den innehåller **`<element>`** och **`<attribute>`** delelement.

Den första **`<element>`** delelement sammanfaller med entitetens rot.

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

The **`<element>`** -taggar definierar namnen på enhetselement. **`<attribute>`** -taggar i schemat definierar namnen på attributen i **`<element>`** -taggar som de har länkats till.

## Identifiering av ett schema {#identification-of-a-schema}

Ett dataschema identifieras med sitt namn och namnutrymme.

Med ett namnutrymme kan du gruppera en uppsättning scheman efter intresseområde. Till exempel **kus** namnutrymme används för kundspecifik konfiguration (**kunder**).

Identifieringsnyckeln för ett schema är en sträng som skapats med namnutrymmet och namnet avgränsat med ett kolon, till exempel: **cus:mottagare**.

>[!IMPORTANT]
>
>Namnutrymmets namn måste vara kortfattat och får endast innehålla tillåtna tecken enligt reglerna för XML-namngivning.
>
>Identifierare får inte börja med numeriska tecken.
>
>Följande namnutrymmen är reserverade för beskrivningar av de systemenheter som krävs för att Adobe Campaign-programmet ska fungera och får inte användas: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.

