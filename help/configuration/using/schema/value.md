---
product: campaign
title: Element och attribut - värdeelement
description: Element och attribut
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%

---

# värdeelement {#value--element}


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
* **img (sträng)**: bild länkad till uppräkningen i formatet &quot;namespace:image_name&quot;. Bilden måste importeras till programservern.
* **label (string)**: etikett för uppräkningsvärdet.
* **name (string)**: uppräkningsvärdets interna namn.
* **värde (sträng)**: uppräkningsvärdets värde. Värdetypen definieras baserat på uppräkningstypen. Om uppräkningen är av strängtyp kan den bara innehålla teckensträngtypsvärden.

## Exempel {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
