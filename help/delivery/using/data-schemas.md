---
title: Datamodeller
seo-title: Datamodeller
description: Datamodeller
seo-description: null
page-status-flag: never-activated
uuid: 3327a38c-e44d-4581-a67b-bb60c1604a5f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: aeaa9475-3715-40a4-8864-29d126883272
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Datamodeller{#data-schemas}

Nedan följer några allmänna principer för användningen av datamappningar i Adobe Campaign.

Mer information om hur du skapar och konfigurerar datamappningar i Adobe Campaign finns i [det här avsnittet](../../configuration/using/about-schema-edition.md).

## Schemastruktur {#schema-structure}

XML-dokumentet i ett dataschema måste innehålla **`<srcschema>`** rotelementet med attributen **name** och **namespace** för att schemanamnet och dess namnutrymme ska kunna fyllas i.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Startpunkten för schemat är dess huvudelement. Det är enkelt att identifiera eftersom det har samma namn som schemat och bör vara underordnat rotelementet. Beskrivningen av innehållet börjar med det här elementet.

I ett innehållshanteringsschema representeras huvudelementet av följande rad:

```
<element name="book" template="ncm:content" xmlChildren="true">
```

Med **mallattributet** som anges i huvudelementet kan du utöka schemat med generiska egenskaper till alla innehållsdefinitioner, som namn, skapandedatum, författare, associerad sträng osv.

Dessa egenskaper beskrivs i **ncm:content** -schemat.

>[!NOTE]
>
>Förekomsten av **xmlChildren** -attributet anger att den datastruktur som anges via huvudelementet lagras i ett XML-dokument i innehållsinstansen.

>[!CAUTION]
>
>När du skapar ett nytt schema eller under ett schematillägg måste du behålla samma sekvensvärde för primärnyckeln (@pkSequence) för hela schemat.

## Datatyper {#data-types}

Här är ett exempel på ett innehållshanteringsschema där typerna är ifyllda:

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## Egenskaper {#properties}

Olika egenskaper kan användas för att förbättra **`<element>`** - och **`<attribute>`** elementen i dataschemat.

De huvudegenskaper som används i innehållshantering är följande:

* **label**: kort beskrivning,
* **desc**: lång beskrivning,
* **standard**: uttryck som returnerar ett standardvärde när innehåll skapas,
* **userEnum**: kostnadsfri uppräkning för att lagra och visa de värden som anges i detta fält,
* **enum**: fast uppräkning som används när listan med möjliga värden är känd i förväg.

Här är vårt exempelschema med egenskaperna ifyllda:

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## Samlingselement {#collection-elements}

En samling är en lista med element med samma namn och samma hierarkiska nivå.

I det här exemplet är elementen **`<chapter>`** och **`<page>`** samlingar. Attributet **obundet** måste därför läggas till i definitionen av dessa element:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>Med attributet **ordered=&quot;true&quot;** kan du ordna de infogade samlingselementen.

## Elementreferens {#element-referencing}

Elementreferenser används ofta i innehållsscheman. Det gör att du kan faktorisera definitionen av ett **`<element>`** element så att det kan refereras till andra element med samma struktur.

Attributet **ref** för elementet som ska refereras måste slutföras med sökvägen (XPath) för referenselementet.

**Exempel**: tillägg av en **bilaga** -sektion med samma struktur som **`<chapter>`** elementet i vårt exempelschema.

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

Kapitelstrukturen flyttas till elementet med namnet &quot;section&quot; utanför huvudelementet. Kapitlet och avsnittet refererar till avsnittselementet.

## Beräkningssträng {#compute-string}

En **beräkningssträng** är ett XPath-uttryck som används för att konstruera en sträng som representerar en innehållsinstans.

Här är vårt exempelschema med **beräkningssträngen**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## Redigera scheman {#editing-schemas}

I redigeringsfältet kan du ange XML-innehållet i källschemat:

![](assets/d_ncs_integration_schema_edition.png)

När källschemat sparas startas generering av utökade scheman automatiskt.

>[!NOTE]
>
>Med **namnredigeringskontrollen** kan du ange schemats nyckel som består av namnet och namnutrymmet. Attributen **name** och **namespace** för schemarotelementet uppdateras automatiskt i schemats XML-redigeringsfält.
