---
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 6%

---

# param element {#param--element}

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

## Underordnade {#children-12}

`<help>`

## Beskrivning {#description-12}

Med det här elementet kan du definiera en parameter för att anropa en SOAP-metod.

## Attributbeskrivning {#attribute-description-12}

* **desc (sträng)**: beskrivning som rör  `<param>` elementet.
* **inout (sträng)**: det här attributet definierar om parametern finns vid indata (in) eller utdata (ut) för SOAP-anropet eller inte. Om det här attributet inte anges används standardparametern (&quot;@inout=in&quot;).
* **label (string)**:  `<param>` label
* **localizable (string)**: om det är aktiverat anger det här attributet att samlingsverktyget ska återställa värdet för attributet &quot;@label&quot; för översättning (intern användning).
* **name (MNTOKEN)**: internt namn på  `<param>`
* **type (string)**: this-attributet definierar typen av  `<param>` element

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
