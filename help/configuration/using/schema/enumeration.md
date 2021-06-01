---
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 5%

---

# uppräkningselement {#enumeration--element}

## Innehållsmodell {#content-model-5}

uppräkning:==(help| value)

## Attribut {#attributes-5}

* @basetype (sträng)
* @default (sträng)
* @desc (sträng)
* @label (sträng)
* @name (sträng)
* @template (sträng)

## Överordnade {#parents-5}

`<srcschema>`

## Underordnade {#children-5}

* `<help>`
* `<value>`

## Beskrivning {#description-5}

Med det här elementet kan vi definiera en värdeuppräkning. En uppräkning tillhör schemat som den är definierad i, men är tillgänglig via ett annat schema.

## Använd och använd {#use-and-context-of-use-4}

Uppräkningar definieras i början av ett schema (innan huvudelementet definieras).

## Attributbeskrivning {#attribute-description-5}

* **basetype (sträng)**: typ av värden som lagras i uppräkningen.

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

* **default (string)**: Standardvärde. Standardvärdet kan också vara ett av de värden som definieras i uppräkningen.
* **desc (sträng)**: uppräkningsbeskrivning.
* **label (string)**: uppräkningsetikett.
* **name (string)**: uppräkningens interna namn.
* **template (string)**: det här attributet definierar en referens till ett  `<enumeration>` element som delas av flera scheman. Definitionen kopieras automatiskt till det aktuella schemat.

## Exempel {#examples-4}

Exempel på uppräkningsvärden vars värden lagras i databasen:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

Definition av en uppräkning med ett standardvärde:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
