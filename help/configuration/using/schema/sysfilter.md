---
product: campaign
title: Element och attribut - sysfilter-element
description: Element och attribut
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 4%

---

# sysfilter-element {#sysfilter--element}


## Innehållsmodell {#content-model-15}

sysFilter:==villkor

## Attribut {#attributes-15}

Ingen

## Överordnade {#parents-15}

`<element>`

## Barn {#children-15}

`<condition>`

## Beskrivning {#description-15}

Med det här elementet kan du definiera ett filter.

## Attributbeskrivning {#attribute-description-15}

Det här elementet har inga attribut.

## Exempel {#examples-12}

Definition av ett filter med ett villkor i @name-attributet:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
