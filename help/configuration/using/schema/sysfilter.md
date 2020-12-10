---
solution: Campaign Classic
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '42'
ht-degree: 19%

---


# `<sysfilter>` element  {#sysfilter--element}

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
