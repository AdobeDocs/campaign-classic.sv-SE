---
product: campaign
title: Schemaelement och attribut - param-element
description: param-element
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 2%

---

# param-element {#param--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-12}

param:==help

## Attribut {#attributes-12}

* @_operation (sträng)
* @desc (sträng)
* @enum (sträng)
* @inout (sträng)
* @label (sträng)
* @localizable (sträng)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (sträng)

## Överordnade {#parents-12}

`<parameters>`

## Barn {#children-12}

`<help>`

## Beskrivning {#description-12}

Med det här elementet kan du definiera en parameter för att anropa en SOAP-metod.

## Attributbeskrivning {#attribute-description-12}

* **desc (sträng)**: beskrivning som gäller `<param>` -element.
* **inout (sträng)**: det här attributet definierar om parametern finns vid indata (in) eller utdata (ut) för SOAP-anropet eller inte. Om det här attributet inte anges används standardparametern (&quot;@inout=in&quot;).
* **label (string)**: `<param>` label
* **localizable (sträng)**: om det är aktiverat anger det här attributet att samlingsverktyget ska återställa värdet för attributet &quot;@label&quot; för översättning (intern användning).
* **name (MNTOKEN)**: internt namn på `<param>`
* **type (sträng)**: this-attributet definierar typen av `<param>` element

   Lista över tillgängliga typer:

   * VALFRITT
   * bin
   * blob
   * boolesk
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * datum
   * DOMDocument
   * DOMElement
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * PM
   * MNTOKEN
   * procent
   * primarykey
   * kort
   * string
   * tid
   * tidsintervall
   * uuid

## Exempel {#examples-9}

Definition av den inkommande inställningen &quot;serviceName&quot; av teckensträngstyp:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
