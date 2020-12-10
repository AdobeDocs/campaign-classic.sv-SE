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
source-wordcount: '92'
ht-degree: 8%

---


# `<condition>` element  {#condition--element}

## Innehållsmodell {#content-model-2}

villkor:==TOM

## Attribut {#attributes-2}

* @boolOperator (sträng)
* @enabledIf (sträng)
* @expr (sträng)

## Överordnade {#parents-2}

`<sysfilter>`

## Underordnade {#children-2}

Ingen

## Beskrivning {#description-2}

Med det här elementet kan du definiera ett filtervillkor.

## Använd och använd {#use-and-context-of-use-2}

Ett `<sysfiler>`-element kan innehålla flera filtervillkor.

## Attributbeskrivning {#attribute-description-2}

* **boolOperator (sträng)**: om flera  `<conditions>` är definierade inom samma   `<sysfilter>` element kan du kombinera dem med det här attributet. Som standard är den logiska länken mellan `<condition>`-element&quot;AND&quot;. Med attributet @boolOperator kan du kombinera länkarna OR och AND.
* **enabledIf (string)**: aktiveringstest.
* **expr (string)**: ett XTK-uttryck.

## Exempel {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
