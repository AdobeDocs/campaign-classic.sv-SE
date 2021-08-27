---
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 7%

---

# nyckelfältelement {#keyfield--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-9}

nyckelfält:==EMPTY

## Attribut {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## Överordnade {#parents-9}

`<key>`  ,  `<dbindex />`

## Barn {#children-9}

Ingen

## Beskrivning {#description-9}

Det här elementet definierar de fält som ska integreras i ett index eller en nyckel.

## Attributbeskrivning {#attribute-description-9}

* **xlink (MNTOKEN)**: I kan du automatiskt referera till sekundärnycklar som definieras i kopplingen för en relationstabell (N-N-länk).
* **xpath (MNTOKEN)**: definition av ett index eller en nyckel för ett  `<attribute>`  element. Det här attributet tar emot en Xpath som definierar sökvägen till schemaattributet som definierar nyckeln eller indexet.

## Exempel {#examples-}

Markering av fältet &quot;sName&quot; i ett index med en Xpath på &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```
