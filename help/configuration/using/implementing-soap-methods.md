---
title: Implementera SOAP-metoder
seo-title: Implementera SOAP-metoder
description: Implementera SOAP-metoder
seo-description: null
page-status-flag: never-activated
uuid: c9366f4e-460d-4087-88f7-9cc6d0de597a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 76984d9d-7759-4e0f-a275-09cca27589fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Implementera SOAP-metoder{#implementing-soap-methods}

## Introduktion {#introduction}

Det går att skapa SOAP-metoder i JavaScript. Den här funktionen aktiverar helt enkelt tillämpande processer och kan undvika att utveckla JSP:er och anrop till dem i formulären.

Dessa SOAP-metoder fungerar på samma sätt som de som definierats internt i programmet. Samma attribut stöds: static, key only and const.

## Definiera ett metodbibliotek {#defining-a-method-library}

När du skapar ett metodbibliotek ingår två faser:

* SOAP-metoddeklarationen,
* Definition (eller implementering) i JavaScript.

### Deklaration {#declaration}

Börja med att deklarera metoderna i scheman (mer information om hur du skapar och redigerar scheman finns i [det här avsnittet](../../configuration/using/about-schema-edition.md)).

Deras deklaration liknar den för inbyggda metoder, förutom att du måste lägga till attributet &#39;library&#39; som anger namnet på det metodbibliotek där definitionen finns.

Det här namnet sammanfaller med namnet (med namnutrymmet) för typen JavaScript-kod.

Exempel:

Metoden testLog(msg) deklareras i tillägget nms:mottagare

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>Namnutrymmet och namnet som används för biblioteket är oberoende av namnutrymmet och schemanamnet där deklarationen finns.

### Definition {#definition}

SOAP-metoder implementeras i form av JavaScript-funktioner grupperade i ett skript som representerar ett bibliotek.

>[!NOTE]
>
>Ett metodbibliotek kan gruppera funktioner för olika scheman eller vice versa, och funktionerna i ett schema kan definieras i separata bibliotek.

Skriptet kan innehålla kod som ska köras under den initiala biblioteksinläsningen.

**1. Namn**

Namnet på funktionen måste vara i följande format:

```
 <schema-namespace>_<schema-name>_<method-name>
```

Exempel:

Följande JavaScript-funktion är implementeringen av den metod som beskrivs ovan. Den ska definieras i typen JavaScript-kod med hjälp av namnet cus:test.

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. Signatur**

Funktionens signatur måste innehålla ett argument för varje in- eller inout-parameter i deklarationen.

Specialfall:

* **icke-statiska metoder**: funktionen måste innehålla ett extra argument först, som sammanfaller med den XML-entitet som skickas i form av ett XML-typobjekt (E4X).
* **Typmetoder** av typen&quot;endast nyckel&quot;: funktionen måste innehålla ytterligare ett argument först, som sammanfaller med den tangent som skickas i form av teckensträngar.

**3. Returnerade värden**

Funktionen måste returnera ett värde för varje parameter av typen out eller inout. Specialfall: Om metoden deklareras utan något av attributen&quot;static&quot;,&quot;key only&quot; eller&quot;const&quot; måste det första returnerade värdet sammanfalla med den ändrade entiteten. Du kan returnera ett nytt objekt eller returnera den första ändrade parametern.

Till exempel:

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

När flera värden ska returneras måste de visas i en tabell.

Exempel:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

