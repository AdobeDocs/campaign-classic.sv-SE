---
product: campaign
title: Element och attribut - attributelement
description: Element och attribut
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 0%

---

# attributelement {#attribute--element}


## Innehållsmodell {#content-model}

attribute:==help

## Attribut {#attributes}

_operation (sträng), advanced (boolesk), applicableIf (sträng), autoIncrement (boolesk), beginTo (sträng), dataPolicy (sträng), dbEnum (sträng), defOnDuplicate (boolesk), default (sträng), desc (sträng), edit (sträng), enum (sträng), feature (sträng), featureDate (sträng) boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqlqll table (string), target (MNTOKEN), template (string), translatedDefault (string), translateExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

## Överordnade {#parents}

`<element>`

## Barn {#children}

`<help>`

## Beskrivning {#description}

Med `<attribute>`-element kan du definiera ett fält i databasen.

## Användning och användningssammanhang {#use-and-context-of-use}

`<attribute>` element måste deklareras i ett `<element>`-element.

Sekvensen i vilken `<attribute>`-element definieras i en `<srcschema>` påverkar inte fältgenereringssekvensen i databasen. Sekvensen som skapas kommer att vara i alfabetisk ordning.

## Attributbeskrivning {#attribute-description}

* **_operation (sträng)**: definierar typen av skrivning i databasen.

  Det här attributet används främst vid utökning av scheman som ligger utanför rutan.

  Tillgängliga värden är:

   * &quot;none&quot;: avstämning ensam. Det innebär att Adobe Campaign återställer elementet utan att uppdatera det eller genererar ett fel om det inte finns.
   * &quot;insertOrUpdate&quot;: uppdatera med infogning. Det innebär att Adobe Campaign uppdaterar elementet eller skapar det om det inte finns.
   * &quot;infoga&quot;: infogning. Det innebär att Adobe Campaign infogar elementet utan att kontrollera om det finns.
   * &quot;update&quot;: update. Det innebär att Adobe Campaign uppdaterar elementet eller genererar ett fel om det inte finns.
   * &quot;delete&quot;: delete. Det innebär att Adobe Campaign återställer och tar bort element.

* **avancerat (booleskt)**: När det här alternativet aktiveras (@advanced=&quot;true&quot;) kan du dölja attributet i listan med tillgängliga fält som kan användas för att konfigurera en lista i ett formulär.
* **applicableIf (string)**: Med det här attributet kan du göra fält valfria. Elementet `<attribute>` kommer att beaktas när databasen uppdateras när villkoret uppfylls. &quot;applicableIf&quot; tar emot ett XTK-uttryck.
* **autoIncrement (boolean)**: om det här alternativet aktiveras blir fältet en räknare. Detta gör att du kan öka ett värde (mest ID). (extern användning)
* **tillhörTo (sträng)**: tar namnet och namnutrymmet för tabellen som delar fältet och fyller i schemat där attributet har deklarerats. (används endast i en `<schema>`).
* **dataPolicy (string)**: gör att du kan ange godkännandebegränsningar för värden som tillåts i SQL- eller XML-fältet. Värdena för det här attributet är:

   * &quot;none&quot;: inget värde
   * &quot;smartCase&quot;: inledande versal
   * &quot;lowerCase&quot;: all lower case
   * &quot;upperCase&quot;: versaler
   * &quot;email&quot;: email address
   * &quot;telefon&quot;: telefonnummer
   * &quot;identifierare&quot;: identifierarnamn
   * &quot;resIdentifier&quot;: filnamn

* **dbEnum (sträng)**: tar emot det interna namnet för en sluten uppräkning. Uppräkningsvärdena måste definieras i `<srcschema>`.
* **defOnDuplicate (boolesk)**: om det här attributet aktiveras, används standardvärdet (definierat i @default) automatiskt på posten när en post dupliceras.
* **default (sträng)**: låter dig definiera värdet för standardfältet (anrop till en funktion, standardvärde). Attributet tar emot ett XTK-uttryck.
* **desc (sträng)**: gör att du kan infoga en beskrivning av attributet. Den här beskrivningen används för att förstå vad elementet är och vad det används för. Du kan visa det i formuläret.
* **edit (string)**: det här attributet anger vilken typ av indata som ska användas i formuläret som är länkat till schemat.
* **enum (sträng)**: tar emot namnet på uppräkningen som är länkad till fältet. Uppräkningen kan infogas i samma schema eller i ett fjärrschema.
* **expr (sträng)**: definierar ett uttryck för förberäkning av fältvärde. Attributet tar emot en Xpath eller ett XTK-uttryck.
* **funktion (sträng)**: definierar ett egenskapsfält: Dessa fält används för att utöka data i en befintlig tabell, men med lagring i en bilagetabell. Godkända värden är:

   * &quot;shared&quot;: innehållet lagras i en delad tabell per datatyp
   * dedikerad: innehållet lagras i en dedikerad tabell

  SQL-egenskapstabeller byggs automatiskt baserat på den karakteristiska typen:

   * dedikerad: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * delade: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Det finns två typer av egenskapsfält: enkla oà<sup>1</sup>-fält där ett enda värde är godkänt för egenskapen och i <sup>1</sup> flervalsfält där egenskapen är länkad till ett samlingselement som kan innehålla flera värden.

  När en egenskap definieras i ett schema måste schemat ha en huvudnyckel baserad på ett enskilt fält (sammansatta nycklar tillåts inte).

* **featureDate (booleskt)**: attribut länkat till egenskapsfältet &quot;@feature&quot;. Om värdet är &quot;true&quot; kan du ta reda på när värdet senast uppdaterades.
* **img (sträng)**: gör att du kan definiera en sökväg för en bild som är länkad till ett fält (namnområde + bildnamn) (exempel: img=&quot;cus:mypicture.jpg&quot;). Fysiskt sett måste bilden importeras till programservern.
* **label (string)**: etikett länkad till fältet, främst avsedd för användaren i gränssnittet. Du kan undvika namnbegränsningar.
* **length (string)**: max. antal tecken för ett värde av typen &quot;string&quot; i SQL-fältet. Om attributet @length inte anges skapas ett fält med 255 tecken automatiskt i Adobe Campaign.
* **lokaliserbar (booleskt)**: Om det aktiveras, anger det här attributet att samlingsverktyget ska återställa värdet för attributet @label för översättning (internt bruk).
* **name (MNTOKEN)**: namnet på attributet som kommer att matcha namnet på fältet i tabellen. Värdet för attributet &quot;@name&quot; måste vara kort, helst på engelska, och följa XML-namnbegränsningar.

  När schemat skrivs till databasen läggs prefix automatiskt till i fältnamnet av Adobe Campaign:

   * &quot;i&quot;: prefix för typen integer.
   * &quot;d&quot;: prefix för double-typen.
   * &quot;s&quot;: prefix för teckensträngstypen.
   * &quot;ts&quot;: prefix för typen &#39;date&#39;.

  Om du vill definiera namnet på fältet i tabellen ska du använda alternativet @sqlname när du definierar ett attribut.

* **notNull (booleskt)**: gör att du kan definiera om Adobe Campaign beteende för hantering av NULL-poster i databasen. Som standard är numeriska fält inte null och sträng- och datumtypsfält kan vara null.
* **pkgStatus (sträng)**: vid paketexport beaktas värden beroende på värdet för @pkgStatus:

   * &quot;always&quot;: always present
   * &quot;never&quot;: never present
   * &quot;standard (eller ingenting)&quot;: värdet exporteras förutom om det är standardvärdet eller om det inte är ett internt fält som inte är kompatibelt med andra instanser.

* **ref (sträng)**: det här attributet definierar en referens till ett `<attribute>`-element som delas av flera scheman (definitionsfactoring). Definitionen kopieras inte till det aktuella schemat.
* **obligatoriskt (booleskt)**: Om det här attributet aktiveras (@required=&quot;true&quot;) markeras fältet i gränssnittet. Fältets etikett blir röd i formulär.
* **sql (booleskt)**: Om det här attributet aktiveras (@sql=&quot;true&quot;) tvingas lagring av SQL-attributet att användas, även om elementet som innehåller attributet har egenskapen xml=&quot;true&quot;.
* **sqlDefault (sträng)**: Med det här attributet kan du definiera det standardvärde som ska beaktas vid uppdatering av databasen om attributet @notNull aktiveras. Om det här attributet läggs till efter att attributet har skapats ändras inte schemabeteendet ens för de nya posterna. Om du vill ändra schemat och uppdatera värdet för nya poster måste du ta bort och skapa attributet igen.
* **sqlname (sträng)**: för fältet när tabellen skapas. Om @sqlname inte anges används värdet för attributet &quot;@name&quot; som standard. När schemat skrivs i databasen läggs prefix till automatiskt beroende på fälttypen.
* **template (string)**: det här attributet definierar en referens till ett `<attribute>`-element som delas av flera scheman. Definitionen kopieras automatiskt till det aktuella schemat.
* **translatedDefault (sträng)**: om ett @default-attribut hittas kan du med &quot;@translatedDefault&quot; definiera om ett uttryck så att det matchar det som definierats i @default, som ska samlas in av översättningsverktyget (intern användning).
* **translrExpr (sträng)**: om det finns ett @expr-attribut kan du med attributet @translr definiera om ett uttryck så att det matchar det som definierats i @expr, som ska samlas in av översättningsverktyget (intern användning).
* **type (MNTOKEN)**: fälttyp.

  Fälttyper är generiska. Beroende på vilken typ av databas som är installerad, ändrar Adobe Campaign den definierade typen till ett värde som är specifikt för den databas som är installerad under strukturuppdateringen.

  Lista över tillgängliga typer:

   * VALFRITT
   * bin
   * blob
   * boolesk
   * byte
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * datum
   * double
   * enum
   * float
   * html
   * int64
   * link
   * long
   * PM
   * MNTOKEN
   * procent
   * primarykey
   * kort
   * string
   * tid
   * tidsintervall
   * uuid

  Om attributet &quot;@type&quot; lämnas tomt länkas en teckensträng (STRING) med längden 100 till fältet som standard.

  Om fältet är av STRING-typ och fältets namn inte anges av närvaron av attributet &quot;@sqlname&quot;, kommer namnet på fältet i databasen automatiskt att föregås av ett s. Det här operativläget liknar det för textfälten INTEGER (i), DOUBLE (d) och DATES (ts).

* **userEnum (sträng)**: tar emot det interna namnet för en öppen uppräkning. Uppräkningens värden kan definieras av användaren i gränssnittet.
* **visibleIf (string)**: definierar ett villkor i form av ett XTK-uttryck för att visa eller dölja attributet.

  >[!IMPORTANT]
  >
  >Attributet är dolt, men det går fortfarande att komma åt dess data.

* **xml (booleskt)**: Om det här alternativet aktiveras har fältets värden inte något länkat SQL-fält. Adobe Campaign skapar ett texttypsfält, &quot;mData&quot;, för postlagring. Det innebär att det inte finns någon filtrering eller sortering för dessa fält.

### Exempel {#examples}

Exempel på uppräkningsvärden vars värden lagras i databasen:

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

Deklaration för ett XML-fält med &quot;@datapolicy&quot;:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

Exempel med ett &quot;@applicableIf&quot;: attributet &quot;contains&quot; skapas bara om antalet länder är större än 20.

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

Exempel med &quot;@feature&quot; av typen &quot;shared&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

Exempel med &quot;@feature&quot; av typen &quot;dedikerad&quot;:

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
