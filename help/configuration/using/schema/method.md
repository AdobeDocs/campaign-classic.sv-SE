---
product: campaign
title: Schemaelement och attribut - metodelement
description: method-element
feature: Schema Extension
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# method-element {#method--element}


## Innehållsmodell {#content-model-10}

method:==( help | parametrar)

## Attribut {#attributes-10}

* @_operation (sträng)
* @access (sträng)
* @const (boolesk)
* @hidden (boolesk)
* @label (sträng)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolean)
* @static (boolesk)

## Överordnade {#parents-10}

`<methods>`, `<interface />`

## Barn {#children-10}

* `<help>`
* `<parameters>`

## Beskrivning {#description-10}

Med det här elementet kan du definiera en SOAP.

## Användning och användningssammanhang {#use-and-context-of-use-7}

SOAP metoder möjliggör programprocesser.

@library krävs för att deklarera en ny metod (icke-inbyggd): namnutrymmet och namnet som används för biblioteket är oberoende av namnutrymmet och namnet på schemat där deklarationen finns.

## Attributbeskrivning {#attribute-description-10}

* **access (string)**: det här attributet definierar åtkomstkontroll för användning av metoden. Om det här attributet saknas är identifiering obligatorisk. Tillgängliga värden är: &quot;anonymous&quot;, &quot;admin&quot; och &quot;sql&quot;.
* **const (boolean)**: om det aktiveras innebär det här attributet att den deklarerade metoden ändrar entiteten
* **label (string)**: metodens etikett.
* **library (string)**: den här metoden är inte inbyggd i programmet. Det här attributet tar värdet för det metodbibliotek där metoddefinitionen finns (nms:mylibrary.js).
* **name (MNTOKEN)**: unikt metodnamn.
* **static (boolean)**: Om det här attributet aktiveras betraktas metoden som självständig, alla parametrar måste anges för metoden när den anropas.

## Exempel {#examples-7}

Definition av&quot;prenumerera&quot; från kartongmetoden:

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
