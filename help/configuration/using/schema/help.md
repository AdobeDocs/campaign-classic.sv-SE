---
product: campaign
title: Schemaelement och attribut - hjälpelement
description: help-element
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 4%

---

# help-element {#help--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-6}

help:==EMPTY

## Attribut {#attributes-6}

Ingen

## Överordnade {#parents-6}

`<srcschema>`, `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## Barn {#children-6}

Ingen

## Beskrivning {#description-6}

Med det här elementet kan du beskriva en `<element>` eller `<attribute>`   -element. Den kan bara innehålla text och lagras i XML i databasen.

## Attributbeskrivning {#attribute-description-6}

Det här elementet har inga attribut.

## Exempel {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
