---
product: campaign
title: Element och attribut - compute-string-element
description: compute-string-element
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 2%

---

# compute-string-element {#compute-string--element}


## Innehållsmodell {#content-model-1}

compute-string:==EMPTY

## Attribut {#attributes-1}

@expr

## Överordnade {#parents-1}

`<element>`

## Barn {#children-1}

Ingen

## Beskrivning {#description-1}

Med elementet `<compute-string>` kan du generera en sträng baserat på ett XTK-uttryck som visar en inbyggd etikett i gränssnittet baserat på flera värden.

## Användning och användningssammanhang {#use-and-context-of-use-1}

När `<compute-string>` inte har definierats anges ett `<compute-string>`-element som standard med värdena för primärnyckeln i schemat.

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
