---
product: campaign
title: Element och attribut - compute-string-element
description: compute-string-element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 2%

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

The `<compute-string>` Med -element kan du generera en sträng baserat på ett XTK-uttryck som visar en&quot;inbyggd&quot; etikett i gränssnittet baserat på flera värden.

## Användning och användningssammanhang {#use-and-context-of-use-1}

När nej `<compute-string>` är definierad, en `<compute-string>` -elementet anges som standard med värdena för primärnyckeln i schemat.

## Attributbeskrivning {#attribute-description-1}

* **expr (sträng)**: XTK- och/eller Xpath-uttryck

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
