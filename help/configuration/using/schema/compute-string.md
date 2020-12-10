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
source-wordcount: '88'
ht-degree: 9%

---


# `<compute-string>` element  {#compute-string--element}

## Innehållsmodell {#content-model-1}

compute-string:==EMPTY

## Attribut {#attributes-1}

@expr

## Överordnade {#parents-1}

`<element>`

## Underordnade {#children-1}

Ingen

## Beskrivning {#description-1}

Med `<compute-string>`-elementet kan du generera en sträng baserat på ett XTK-uttryck som visar en inbyggd etikett i gränssnittet baserat på flera värden.

## Använd och använd {#use-and-context-of-use-1}

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
