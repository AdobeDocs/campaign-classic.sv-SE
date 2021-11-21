---
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---

# method-element {#method--element}

![](../../../assets/v7-only.svg)

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
* @pkonly (boolesk)
* @static (boolesk)

## Överordnade {#parents-10}

`<methods>`  ,  `<interface />`

## Barn {#children-10}

* `<help>`
* `<parameters>`

## Beskrivning {#description-10}

Med det här elementet kan du definiera en SOAP-metod.

## Användning och användningssammanhang {#use-and-context-of-use-7}

SOAP-metoder möjliggör programprocesser.

&quot;@library&quot; krävs för att deklarera en ny metod (icke-inbyggd): namnutrymmet och namnet som används för biblioteket är oberoende av namnutrymmet och namnet på schemat där deklarationen finns.

## Attributbeskrivning {#attribute-description-10}

* **åtkomst (sträng)**: det här attributet definierar åtkomstkontroll för metoden. Om attributet saknas är identifiering obligatorisk. Tillgängliga värden är: &#39;anonymous&#39;, &#39;admin&#39; och &#39;sql&#39;.
* **const (boolean)**: om det är aktiverat betyder det här attributet att den deklarerade metoden ändrar entiteten
* **label (string)**: metodens etikett.
* **bibliotek (sträng)**: den här metoden är inte inbyggd i programmet. Det här attributet tar värdet för det metodbibliotek där metoddefinitionen finns (nms:mylibrary.js).
* **name (MNTOKEN)**: unikt metodnamn.
* **static (boolesk)**: Om det här attributet aktiveras betraktas metoden som självständig, och alla parametrar måste anges för metoden när den anropas.

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
