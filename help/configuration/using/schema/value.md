---
product: campaign
title: Element och attribut - värdeelement
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 3%

---

# värdeelement {#value--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-16}

value:==help

## Attribut {#attributes-16}

* @applicableIf (sträng)
* @desc (sträng)
* @enabledIf (sträng)
* @img (sträng)
* @label (sträng)
* @name (sträng)
* @value (sträng)

## Överordnade {#parents-16}

`<enumeration>`

## Barn {#children-16}

`<help>`

## Beskrivning {#description-16}

Med det här elementet kan du definiera de värden som lagras i en uppräkning.

## Attributbeskrivning {#attribute-description-16}

* **applicableIf (string)**: Med det här attributet kan du göra ett uppräkningsvärde valfritt. Det tar emot ett XTK-uttryck.
* **desc (sträng)**: beskrivning av uppräkningsvärdet.
* **enabledIf (sträng)**: villkor för aktivering av uppräkningsvärdet.
* **img (sträng)**: bild länkad till uppräkningen i formuläret &quot;namespace:image_name&quot;. Bilden måste importeras till programservern.
* **label (string)**: uppräkningsvärdets etikett.
* **name (sträng)**: uppräkningsvärdets interna namn.
* **värde (sträng)**: uppräkningsvärdets värde. Värdetypen definieras baserat på uppräkningstypen. Om uppräkningen är av strängtyp kan den bara innehålla teckensträngtypsvärden.

## Exempel {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
