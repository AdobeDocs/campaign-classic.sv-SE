---
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 2%

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

En tangent kallas för sammansatt om den innehåller flera fält (d.v.s. flera) `<keyfield>` barn). Använd inte en sammansatt nyckel för att definiera en primärnyckel.

Om huvudelementet i schemat innehåller attributet &quot;@autopk=true&quot; är primärnyckeln unik. Vi kan bara ha en primärnyckel per schema.

De första 1000 identifierarna är reserverade, så om ett intervall med värden måste definieras för nycklar börjar du med 1000.

## Attributbeskrivning {#attribute-description-8}

* **allowEmptyPart (boolean)**: om det här attributet är aktiverat, anses nyckeln vara giltig om minst en av dess nycklar inte är tom. Om så är fallet är det tomma konceptvärdet &quot;0&quot; (booleskt eller för alla typer av numeriska data). Som standard måste alla tangenter som utgör en sammansatt nyckel anges.
* **applicableIf (string)**: Med det här attributet kan du göra nyckeln valfri. Den definierar det villkor som nyckeldefinitionen ska tillämpas på. Det här attributet tar emot ett XTK-uttryck.
* **internal (boolesk)**: om den är aktiverad, talar det här attributet om för Adobe Campaign att nyckeln är primär.
* **label (string)**: nyckelns etikett.
* **name (MNTOKEN)**: nyckelns interna namn.
* **noDbIndex (boolesk)**: om den är aktiverad (noDbIndex=&quot;true&quot;) kommer fältet som matchar nyckeln inte att indexeras.

## Exempel {#examples-------}

Deklaration av en sammansatt nyckel som tillåter att antingen fältet &quot;@expr&quot; eller &quot;alias&quot; är tomt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Deklaration av en primärnyckel i fältet &quot;Namn&quot; av STRING-typ i en `<srcschema>`  och den matchande SQL-frågan:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
