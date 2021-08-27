---
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---

# compute-string-element {#compute-string--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-1}

compute-string:==EMPTY

## Attribut {#attributes-1}

@expr

## Överordnade {#parents-1}

`<element>`

## Barn {#children-1}

Ingen

## Beskrivning {#description-1}

Med `<compute-string>`-elementet kan du generera en sträng baserat på ett XTK-uttryck som visar en inbyggd etikett i gränssnittet baserat på flera värden.

## Användning och användningssammanhang {#use-and-context-of-use-1}

När ingen `<compute-string>` är definierad anges ett `<compute-string>`-element som standard med värdena för primärnyckeln i schemat.

## Attributbeskrivning {#attribute-description-1}

* **expr (string)**: XTK och/eller Xpath-uttryck

## Exempel {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultat av strängen som beräknats på en mottagare: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
