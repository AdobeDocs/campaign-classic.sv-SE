---
solution: Campaign Classic
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 18%

---


# sysfilter-element {#sysfilter--element}

## Innehållsmodell {#content-model-15}

sysFilter:==villkor

## Attribut {#attributes-15}

Ingen

## Överordnade {#parents-15}

`<element>`

## Underordnade {#children-15}

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
