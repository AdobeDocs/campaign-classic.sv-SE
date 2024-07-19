---
product: campaign
title: Element och attribut - srcschema-element
description: Element och attribut
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# srcschema-element {#srcschema--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-14}

srcSchema:=(attribut) | createdBy | data | element | uppräkning | help | gränssnitt | metoder | modifiedBy)

## Attribut {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (sträng), img (sträng), implements (sträng), label (sträng), labelSingular (sträng), lastModified (datetime), library (boolean), mappingType (sträng), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (boolean), view (boolean), xtkschema (string)

## Överordnade {#parents-14}

Ingen

## Barn {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## Beskrivning {#description-14}

`<srcschema>` är rotelementet i ett schema. Det är indatapunkten för definitionen av schemat.

## Användning och användningssammanhang {#use-and-context-of-use-9}

Schemapresentation är tillgänglig i [Om schemareferens](../../../configuration/using/about-schema-reference.md) och [Schemastruktur](../../../configuration/using/schema-structure.md).

## Attributbeskrivning {#attribute-description-14}

* **skapad (datetime)**: Det här attributet innehåller information om datum och tid när schemat skapades. Den har ett&quot;Date Time&quot;-formulär. De värden som visas hämtas från servern. Tiden visas i UTC-format.
* **createdBy-id (long)**: är identifieraren för den operator som skapade schemat.
* **desc (sträng)**: schemabeskrivning
* **entitySchema (sträng)**: grundläggande schema som syntax och godkännande baseras på (som standard för Adobe Campaign: xtk:srcSchema). När du sparar det aktuella schemat kommer Adobe Campaign att godkänna dess grammatik med det schema som deklarerats i @xtkschema-attributet.
* **extendedSchema (sträng)**: tar emot namnet på det schema som är utanför rutan och som det aktuella schematillägget baseras på. Formuläret är &quot;namespace:name&quot;.
* **img (sträng)**: ikon länkad till schemat (kan definieras i guiden Skapa schema).
* **label (string)**: schemaetikett.
* **labelSingular (string)**: label (singular) för visning i gränssnittet.
* **lastModified (datetime)**: det här attributet innehåller information om datum och tid för den senaste ändringen. Den har ett&quot;Date Time&quot;-formulär. De värden som visas hämtas från servern. Tiden visas i UTC-format.
* **library (boolean)**: använd schemat som ett bibliotek och inte en entitet. Andra scheman kan därför referera till det här schemat tack vare attributen @ref och @template.
* **mappingType (sträng)**:

   * &quot;sql&quot;: databasmappning
   * &quot;textFile&quot;: textfilsmappning
   * &quot;xmlFile&quot;: Mappning av textfiler i XML-format
   * &quot;binaryFile&quot;: binär filmappning

* **modifiedBy-id (long)**: matchar identifieraren för den operator som ändrade schemat.
* **namn (sträng)**: unikt schemanamn.
* **namnrymd (sträng)**: schemats namnrymd (standard: nms, xtk, nl). När du skapar ett nytt schema för ett projekt rekommenderar vi att du använder ett dedikerat namnutrymme.
* **useRecycleBin (booleskt)**: aktiverar papperskorgsfunktionen i programmet. Borttagna poster placeras i papperskorgen innan de tas bort. Den här funktionen är bara tillgänglig i läget &quot;Leverans&quot;.
* **vy (boolesk)**: Om den aktiveras (@view=&quot;true&quot;) används schemat som vy. Databasstrukturuppdateringsguiden tar inte hänsyn till schemat. Det här alternativet används främst för att referera till externa tabeller.
* **xtkschema (sträng)**: namn på schemat som definierar schemagrammatik (xtk:srcSchema som standard).

## Exempel {#examples-11}

`<srcschema>`-elementet i &quot;nms:delivery&quot; ur rutschemat

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
