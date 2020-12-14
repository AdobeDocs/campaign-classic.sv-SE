---
solution: Campaign Classic
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---


# metodelement {#method--element}

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

## Underordnade {#children-10}

* `<help>`
* `<parameters>`

## Beskrivning {#description-10}

Med det här elementet kan du definiera en SOAP-metod.

## Använd och använd {#use-and-context-of-use-7}

SOAP-metoder möjliggör programprocesser.

&quot;@library&quot; krävs för att deklarera en ny metod (icke-inbyggd): namnutrymmet och namnet som används för biblioteket är oberoende av namnutrymmet och namnet på schemat där deklarationen finns.

## Attributbeskrivning {#attribute-description-10}

* **access (string)**: det här attributet definierar åtkomstkontroll för metoden. Om attributet saknas är identifiering obligatorisk. Tillgängliga värden är: &#39;anonymous&#39;, &#39;admin&#39; och &#39;sql&#39;.
* **const (boolean)**: om det är aktiverat betyder det här attributet att den deklarerade metoden ändrar entiteten
* **label (string)**: metodens etikett.
* **bibliotek (sträng)**: den här metoden är inte inbyggd i programmet. Det här attributet tar värdet för det metodbibliotek där metoddefinitionen finns (nms:mylibrary.js).
* **name (MNTOKEN)**: unikt metodnamn.
* **statisk (boolesk)**: Om det här attributet aktiveras betraktas metoden som självständig, och alla parametrar måste anges för metoden när den anropas.

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
