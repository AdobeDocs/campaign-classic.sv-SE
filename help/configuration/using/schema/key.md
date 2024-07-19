---
product: campaign
title: Schemaelement och attribut - nyckelelement
description: nyckelelement
feature: Schema Extension
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# nyckelelement {#key--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-8}

nyckel:==nyckelfält

## Attribut {#attributes-8}

* @allowEmptyPart (boolesk)
* @applicableIf (sträng)
* @internal (boolesk)
* @label (sträng)
* @name (MNTOKEN)
* @noDbIndex (boolesk)

## Överordnade {#parents-8}

`<element>`

## Barn {#children-8}

`<keyfield>`

## Beskrivning {#description-8}

Med det här elementet kan du definiera en nyckel för att identifiera en post i tabellen.

En tabell måste ha minst en nyckel.

## Användning och användningssammanhang {#use-and-context-of-use-6}

Nycklar deklareras som regel efter huvudelementet i schemat och indexen.

En nyckel kallas för sammansatt om den innehåller flera fält (t.ex. flera `<keyfield>` underordnade). Använd inte en sammansatt nyckel för att definiera en primärnyckel.

Om huvudelementet i schemat innehåller attributet &quot;@autopk=true&quot; är primärnyckeln unik. Vi kan bara ha en primärnyckel per schema.

De första 1000 identifierarna är reserverade, så om ett intervall med värden måste definieras för nycklar börjar du med 1000.

## Attributbeskrivning {#attribute-description-8}

* **allowEmptyPart (boolean)**: om det här attributet aktiveras för en sammansatt nyckel anses nyckeln vara giltig om minst en av nycklarna inte är tom. Om så är fallet är det tomma konceptvärdet &quot;0&quot; (booleskt eller för alla typer av numeriska data). Som standard måste alla tangenter som utgör en sammansatt nyckel anges.
* **applicableIf (string)**: Med det här attributet kan du göra nyckeln valfri. Den definierar det villkor som nyckeldefinitionen ska tillämpas på. Attributet tar emot ett XTK-uttryck.
* **internal (boolean)**: Om det är aktiverat informerar det här attributet Adobe Campaign om att nyckeln är primär.
* **label (string)**: nyckelns etikett.
* **name (MNTOKEN)**: nyckelns interna namn.
* **noDbIndex (booleskt)**: Om det aktiveras (noDbIndex=&quot;true&quot;) indexeras inte fältet som matchar nyckeln.

## Exempel {#examples-------}

Deklaration av en sammansatt nyckel som tillåter att antingen fältet &quot;@expr&quot; eller &quot;alias&quot; är tomt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Deklaration för en primärnyckel i fältet Namn av STRING-typ i en `<srcschema>` och den matchande SQL-frågan:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
