---
product: campaign
title: Schemaelement och attribut - villkorselement
description: villkorselement
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%

---

# villkorselement {#condition--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-2}

villkor:==TOM

## Attribut {#attributes-2}

* @boolOperator (sträng)
* @enabledIf (sträng)
* @expr (sträng)

## Överordnade {#parents-2}

`<sysfilter>`

## Barn {#children-2}

Ingen

## Beskrivning {#description-2}

Med det här elementet kan du definiera ett filtervillkor.

## Användning och användningssammanhang {#use-and-context-of-use-2}

Ett `<sysfiler>`  -element kan innehålla flera filtervillkor.

## Attributbeskrivning {#attribute-description-2}

* **boolOperator (sträng)**: om flera `<conditions>` definieras inom samma  `<sysfilter>` kan du kombinera dem med det här attributet. Som standard är den logiska länken mellan `<condition>` är &quot;AND&quot;. Med attributet @boolOperator kan du kombinera länkarna OR och AND.
* **enabledIf (sträng)**: aktiveringstest.
* **expr (sträng)**: ett XTK-uttryck.

## Exempel {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
