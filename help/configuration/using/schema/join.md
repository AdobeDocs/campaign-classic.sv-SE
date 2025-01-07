---
product: campaign
title: Schemaelement och attribut - join-element
description: join-element
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# join-element {#join--element}


## Innehållsmodell {#content-model-7}

join:==EMPTY

## Attribut {#attributes-7}

* @dstFilterExpr (sträng)
* @xpath-dst (sträng)
* @xpath-src (sträng)

## Överordnade {#parents-7}

`<element>`

## Barn {#children-7}

Ingen

## Beskrivning {#description-7}

Här kan du definiera de fält som skapar en koppling mellan SQL-tabeller.

## Användning och användningssammanhang {#use-and-context-of-use-5}

Ett `<join>`-element kan bara användas om det överordnade `<element>`-elementet är av typen link. Det innebär att det överordnade elementet måste ha attributet &quot;@type=link&quot; deklarerat.

Du behöver inte ange namnet och namnutrymmet för fjärrtabellen i elementet `<join>`. De måste anges i det överordnade objektet `<element>`.

Länkar definieras som regel i slutet av schemat.

Om elementet `<join>` inte anges när länktytelementet definieras, placeras länken automatiskt på primärnycklarna för båda tabellerna.

## Attributbeskrivning {#attribute-description-7}

* **dstFilterExpr (sträng)**: Med det här attributet kan du begränsa antalet giltiga värden i fjärrtabellen.
* **xpath-dst (sträng)**: det här attributet tar emot en Xpath (@name-attribut för fjärrtabellen).
* **xpath-src (sträng)**: det här attributet tar emot en Xpath (@name-attribut i det aktuella schemat).

## Exempel {#examples-6}

Länk mellan e-postfältet i den aktuella tabellen och fältet @compagny-id i fjärrtabellen:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Filtrerad länk till tabellen &quot;cus:Country&quot; baserat på innehållet i fältet &quot;@country&quot; som måste innehålla värdet &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
