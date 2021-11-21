---
product: campaign
title: Datascheman
description: Datascheman
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# Datascheman{#data-schemas}

![](../../assets/common.svg)

Nedan följer några allmänna principer för användningen av datarotor i Adobe Campaign.

Mer information om hur du skapar och konfigurerar datascheman i Adobe Campaign finns i [det här avsnittet](../../configuration/using/about-schema-edition.md).

## Schemastruktur {#schema-structure}

XML-dokumentet i ett dataschema måste innehålla **`<srcschema>`** rotelementet med **name** och **namespace** attribut för att fylla i schemanamnet och dess namnutrymme.

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

The **mall** Med attribut som anges i huvudelementet kan du utöka schemat med generiska egenskaper till alla innehållsdefinitioner som namn, skapandedatum, författare, associerad sträng osv.

Dessa egenskaper beskrivs i **ncm:innehåll** schema.

>[!NOTE]
>
>Förekomsten av **xmlChildren** anger att den datastruktur som anges via huvudelementet lagras i ett XML-dokument i innehållsinstansen.

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

Olika egenskaper kan användas för att berika **`<element>`** och **`<attribute>`** elementen i dataschemat.

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

I vårt exempel **`<chapter>`** och **`<page>`** -element är samlingselement. The **obunden** Attributet måste därför läggas till i definitionen av dessa element:

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>Förekomsten av **ordered=&quot;true&quot;** kan du ordna de infogade samlingselementen.

## Elementreferens {#element-referencing}

Elementreferenser används ofta i innehållsscheman. Det gör att du kan faktorisera definitionen av en **`<element>`** så att det kan refereras till andra element med samma struktur.

The **ref** -attributet i det element som ska refereras måste fyllas med sökvägen (XPath) för referenselementet.

**Exempel**: tillägg av **Bilaga** -avsnitt med samma struktur som **`<chapter>`** element i vårt exempelschema.

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

## Databeräkningssträng {#compute-string}

A **Beräkningssträng** är ett XPath-uttryck som används för att konstruera en sträng som representerar en innehållsinstans.

Här är vårt exempelschema med dess **Beräkningssträng**:

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
>The **Namn** Med redigeringskontrollen kan du ange nyckeln för schemat, bestående av namnet och namnutrymmet. The **name** och **namespace** attribut för schemarotelementet uppdateras automatiskt i schemats XML-redigeringsfält.
