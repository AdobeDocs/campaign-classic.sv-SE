---
product: campaign
title: Element och attribut - dbindex-element
description: dbindex-element
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# dbindex-element {#dbindex--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-3}

dbindex:==nyckelfält

## Attribut {#attributes-3}

* @_operation (sträng)
* @applicableIf (sträng)
* @label (sträng)
* @name (MNTOKEN)
* @unique (boolean)

## Överordnade {#parents-3}

`<element>`

## Barn {#children-3}

`<keyfield>`

## Beskrivning {#description-3}

Med det här elementet kan du definiera ett index som är länkat till en tabell.

## Användning och användningssammanhang {#use-and-context-of-use-3}

Du kan definiera flera index. Ett index kan referera till ett eller flera fält i tabellen. Indexdeklarationen följer vanligtvis definitionen för huvudschemaelementet.

Ordningen på `<keyfield>` element definierade i en `<dbindex>` är mycket viktigt. Den första `<keyfield>` måste vara indexeringskriteriet som frågorna huvudsakligen bygger på.

Indexnamnet i databasen beräknas genom att sammanfoga tabellnamnet och indexnamnet. Till exempel: Tabellnamnet &quot;Sample&quot;, Namespace &quot;Cus&quot;, indexnamnet &quot;MyIndex&quot;-> namnet på indexfältet när en indexfråga skapas: &quot;CusSample_myIndex&quot;.

## Attributbeskrivning {#attribute-description-3}

* **operation (sträng)**: definierar typen av skrivning i databasen.

   Det här attributet används främst vid utökning av scheman som ligger utanför rutan.

   Tillgängliga värden är:

   * &quot;none&quot;: enbart avstämning. Det innebär att Adobe Campaign återställer elementet utan att uppdatera det eller genererar ett fel om det inte finns.
   * &quot;insertOrUpdate&quot;: uppdatera med infogning. Det innebär att Adobe Campaign uppdaterar elementet eller skapar det om det inte finns.
   * &quot;insert&quot;: infogning. Det innebär att Adobe Campaign infogar elementet utan att kontrollera om det finns.
   * &quot;update&quot;: uppdatera. Det innebär att Adobe Campaign uppdaterar elementet eller genererar ett fel om det inte finns.
   * &quot;delete&quot;: borttagning. Det innebär att Adobe Campaign återställer och tar bort element.

* **applicableIf (string)**: villkor för att ta med indexet i beräkningen - tar emot ett XTK-uttryck.
* **label (string)**: indexetikett.
* **name (MNTOKEN)**: unikt indexnamn.
* **unik (boolesk)**: Om det här alternativet är aktiverat (@unique=&quot;true&quot;) garanterar attributet att indexet är unikt i alla fält.

## Exempel {#examples-3}

Skapande av ett index i fältet&quot;id&quot;. (attributet &quot;@unique&quot; på `<dbindex>` -element utlöser tillägg av SQL-nyckelordet &quot;UNIQUE&quot; när indexet skapas i databasen (fråga).

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

Skapa ett sammansatt index i fälten @mail och @phoneNumber:

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```
