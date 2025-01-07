---
product: campaign
title: Schemaelement och attribut - elementelement
description: element
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '2029'
ht-degree: 0%

---

# element {#element--element}


## Innehållsmodell {#content-model-4}

element:==(attribute) | compute-string | dbindex | standard | element | help | join | key | sysFilter | translatDefault)

## Attribut {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), beginTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boobox) lean), doesNotSupportDiff (booleskt), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (booleskt), feature (string), featureDate (booleskt), filterPath (sträng), folderLink (sträng), folderModelModel (model string), folderProcess (string), fullLoad (boolesk), hierarkisk (boolesk), hierarkisk sökväg (sträng), img (sträng), inout (sträng), integritet (sträng), label (sträng), labelSingular (sträng), length (sträng), localizable (boolesk), name (MNTOKEN), noDbIndex (boolesk), no Nyckel (booleskt), sorterad (booleskt), överflödig (booleskt), pkSequence (sträng), pkgStatus (sträng), ref (sträng), obligatoriskt (booleskt), revAdvanced (booleskt), revCardinality (sträng), revDesc (sträng), revExternalJoin (booleskt), revIntegrity (sträng) sträng), revLink (sträng), revTarget (sträng), revVisibleIf (sträng), sql (booleskt), sqlname (sträng), sqltable (sträng), tableSpace (sträng), tableSpaceIndex (sträng), target (MNTOKEN), template (sträng), temporaryTable (booleskt), translatedDefault (sträng), translateExpr (sträng) sträng), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

## Överordnade {#parents-4}

`<srcschema>`

`<element>`

## Barn {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

## Beskrivning {#description-4}

Det finns fyra typer av `<element>`-element i Adobe Campaign:

* Roten `<element>` : definierar namnet på SQL-tabellen som matchar schemat.
* Struktur `<element>` : definierar en grupp av `<element>`   eller   `<attribute>`    -element.
* Länken `<element>` : definierar en länk. Elementen måste innehålla attributet &quot;@type=link&quot;.
* XML `<element>` : definierar texttypsfältet mData. Det här elementet måste innehålla attributet &quot;@type=xml&quot;.

## Attributbeskrivning {#attribute-description-4}

* **_operation (sträng)**: definierar typen av skrivning i databasen.

  Det här attributet används främst vid utökning av scheman som ligger utanför rutan.

  Tillgängliga värden är:

   * &quot;none&quot;: avstämning ensam. Det innebär att Adobe Campaign återställer elementet utan att uppdatera det eller genererar ett fel om det inte finns.
   * &quot;insertOrUpdate&quot;: uppdatera med infogning. Det innebär att Adobe Campaign uppdaterar elementet eller skapar det om det inte finns.
   * &quot;infoga&quot;: infogning. Det innebär att Adobe Campaign infogar elementet utan att kontrollera om det finns.
   * &quot;update&quot;: update. Det innebär att Adobe Campaign uppdaterar elementet eller genererar ett fel om det inte finns.
   * &quot;delete&quot;: delete. Det innebär att Adobe Campaign återställer och tar bort element.

* **avancerat (booleskt)**: När det här alternativet aktiveras (@advanced=&quot;true&quot;) kan du dölja attributet i listan med tillgängliga fält som kan användas för att konfigurera en lista i ett formulär.
* **aggregat (sträng)**: gör att du kan kopiera definitionen för en `<element>` via ett annat schema. Det här attributet tar emot en schemadeklaration i form av en &quot;namespace:name&quot;.
* **applicableIf (string)**: villkor för att tillämpa indexet. Attributet tar emot ett XTK-uttryck.
* **autopk (booleskt)**: Om det här alternativet aktiveras (autopk=&quot;true&quot;) definieras en unik nyckel automatiskt. Det här alternativet kan bara användas på schemats huvudelement. Varning! Adobe Campaign garanterar bara att nyckeln som genereras är unik. Det är inte säkert att nyckelvärdena är sekventiella och inkrementella.
* **dataPolicy (string)**: gör att du kan ange godkännandebegränsningar för värden som tillåts i SQL-fältet. Värdena för det här attributet är:

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
* **default (sträng)**: låter dig definiera elementbeteende (anrop till en funktion, standardvärde). Attributet tar emot ett XTK-uttryck.
* **desc (sträng)**: gör att du kan infoga en beskrivning av elementet. Den här beskrivningen används för att förstå vad elementet är och vad det används för. Du kan visa det i formuläret.
* **displayAsField (booleskt)**: Om det här attributet aktiveras visas en länktyp `<element>` som ett fält i trädvyn för scheman (&quot;Fliken Struktur&quot;). På så sätt kan du visa en länk som ett lokalt fält och ändra dess beteende under en fråga. När elementet hittas i SELECT för en fråga används värdet för länkmålet. När elementet hittas i WHERE för en fråga används länkens underliggande nyckel.
* **edit (string)**: det här attributet anger vilken typ av indata som ska användas i formuläret som är länkat till schemat.
* **enum (sträng)**: tar emot namnet på uppräkningen som är länkad till fältet. Uppräkningen kan infogas i samma schema eller i ett fjärrschema.
* **expr (string)**: det här attributet definierar ett beräkningsfält för vilket ingen definition lagras i tabellen. Det tar emot en Xpath eller ett XTK-uttryck (sträng).
* **externalJoin (booleskt)**: externt join in a &quot;link&quot; type element.
* **funktion (sträng)**: definierar ett egenskapsfält: Dessa fält används för att utöka data i en befintlig tabell, men med lagring i en bilagetabell. Godkända värden är:

   * &quot;shared&quot;: innehållet lagras i en delad tabell per datatyp
   * dedikerad: innehållet lagras i en dedikerad tabell

  SQL-egenskapstabeller byggs automatiskt baserat på den karakteristiska typen:

   * dedikerad: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * delade: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  Det finns två typer av egenskapsfält: enkla fält där ett enda värde är godkänt för egenskapen, och flervalsfält där egenskapen är länkad till ett samlingselement som kan innehålla flera värden.

  När en egenskap definieras i ett schema måste schemat ha en huvudnyckel baserad på ett enskilt fält (sammansatta nycklar tillåts inte).

* **featureDate (booleskt)**: attribut länkat till egenskapsfältet &quot;@feature&quot;. Om värdet är &quot;true&quot; kan du ta reda på när värdet senast uppdaterades.
* **filterPath (sträng)**: det här attributet tar emot en Xpath och låter dig definiera ett filter för ett fält.
* **folderLink (string)**: det här attributet tar emot namnet på länken som gör att du kan återställa filerna som innehåller entiteter.
* **folderModel (sträng)**: definierar den typ av mapp som aktiverar entitetslagring. Det här attributet definieras bara om @folderLink finns.
* **folderProcess (string)**: definierar länken där entitetsmodellinstanser lagras. Det här attributet definieras bara om @folderLink finns.
* **fullLoad (booleskt)**: det här attributet tvingar visningen av alla poster i en tabell under fältval i ett formulär.
* **img (sträng)**: tar emot sökvägen till en bild som är länkad till ett element. Attributets värde är av typen &quot;namespace:image name&quot;. Exempel: img=&quot;cus:myImage.jpg&quot;. Fysiskt sett måste bilden importeras till programservern.
* **integritet (sträng)**: källtabellens referensintegritet gentemot måltabellen.

  Tillgängliga värden är:

   * &quot;define&quot;: Adobe Campaign tar inte bort enheten om den refereras via länken
   * &quot;normal&quot;: om du tar bort källförekomsten initieras länkens nycklar på målförekomsten (standardläge), den här typen av integritet initierar alla sekundärnycklar
   * &quot;own&quot;: om du tar bort källförekomsten tas målförekomsten bort
   * &quot;owncopy&quot;: liknar &quot;own&quot; (vid borttagning) eller dubblerar förekomster (vid duplicering)
   * &quot;neutral&quot;: gör ingenting

* **label (string)**: elementetikett.
* **labelSingular (string)**: label (singular form) of the element used in some parts of the interface.
* **length (string)**: max. Antal tecken som är tillåtna för ett värde av typen &quot;string&quot; i SQL-fältet.
* **lokaliserbar (booleskt)**: Om det aktiveras, anger det här attributet att samlingsverktyget ska återställa värdet för attributet @label för översättning (internt bruk).
* **name (MNTOKEN)**: internt namn på elementet som matchar namnet på tabellen. Värdet för attributet &quot;@name&quot; måste vara kort, helst på engelska, och måste uppfylla de namnbegränsningar som är kopplade till XML.

  När schemat skrivs till databasen läggs prefix automatiskt till i fältnamnet av Adobe Campaign.

   * &quot;i&quot;: prefix för typen integer.
   * &quot;d&quot;: prefix för double-typen.
   * &quot;s&quot;: prefix för teckensträngstypen.
   * &quot;ts&quot;: prefix för typen &#39;date&#39;.

  Om du vill definiera namnet på tabellen på ett självständigt sätt måste du använda attributet &quot;@sqltable&quot; i definitionen av huvudschemaelementet.

* **noDbIndex (booleskt)**: gör att du kan ange att elementet inte ska indexeras.
* **ordered (boolean)**: Om attributet är aktiverat (ordered=&quot;true&quot;) behåller Adobe Campaign elementdeklarationssekvensen i ett XML-samlingselement.
* **pkSequence (sträng)**: tar emot namnet på den sekvens som ska användas för att beräkna en automatisk inkrementell nyckel. Det här attributet kan bara användas om en autoinkrementell nyckel har definierats för schemats rotelement.
* **pkgStatus (sträng)**: under paketexporter kommer värden att tas med som en funktion av värdet för det här attributet:

   * &quot;always&quot;: elementet finns alltid
   * &quot;never&quot;: elementet kommer aldrig att finnas
   * &quot;standard (eller ingenting)&quot;: elementet exporteras såvida det inte är standardelementet eller om det inte är ett internt fält och inte är kompatibelt med andra instanser

* **ref (sträng)**: det här attributet definierar en referens till ett >element>-element som delas av flera scheman (definitionsfactoring). Definitionen kopieras inte till det aktuella schemat.
* **obligatoriskt (booleskt)**: Om det här attributet aktiveras (@required=&quot;true&quot;) markeras fältet i gränssnittet. Fältets etikett blir röd i formulär.
* **revAdvanced (boolean)**: När det här attributet aktiveras anges att den motsatta länken är en avancerad länk.
* **revCardinality (sträng)**: det här attributet definierar kardinaliteten för en länk mellan två tabeller. Den används i en länktyp `<element>`.

  Möjliga värden är:

   * &quot;single&quot; : enkel länk av typen 1-1
   * &quot;unbound&quot;: 1-N type collection link

  Om attributet inte anges när länken skapas blir kardinaliteten 1-N som standard.

* **revDesc (sträng)**: det här attributet tar emot en beskrivning som är länkad till motsatt länk.
* **revExternalJoin (booleskt)**: När det här attributet aktiveras kan du tvinga det externa hörnet på motsatt länk.
* **revIntegrity (string)**: det här attributet definierar integriteten i målschemat. Samma värden som attributet &quot;@integrity&quot; tillåts. Som standard ger Adobe Campaign attributet&quot;normal&quot;.
* **revLabel (sträng)**: etikett för motsatt länk.
* **revLink (sträng)**: namnet på motsatt länk. Om värdet är _INGEN_ skapas ingen motsatt länk i målschemat.
* **revTarget (sträng)**: mål för motsatt länk.
* **sql (booleskt)**: Om det här attributet aktiveras (@sql=&quot;true&quot;) tvingas lagret för SQL-elementet att användas, även om elementet har egenskapen xml=&quot;true&quot;.
* **sqlname (sträng)**: fältets namn när tabellen skapas. Om @sqlname inte anges används värdet för attributet @name som standard. När du skriver schemat till tabellen läggs prefix till automatiskt beroende på fälttypen.
* **sqltable (string)**: för schemats huvudelement överläser det här attributet namnet på SQL-tabellen som genereras som standard. Om @sqltable inte anges kommer standardnamnet att struktureras så här: namespace (first letter upper case) följt av värdet för SrcSchema &quot;@name&quot;.
* **tableSpace (string)**: Med det här attributet kan du ange ett nytt datalagringstabellutrymme för en tabell (giltigt i roten `<element>`).
* **tableSpaceIndex (sträng)**: Med det här attributet kan du ange ett nytt indexlagringstabellutrymme för en tabell (giltigt i roten `<element>`).
* **target (MNTOKEN)**: tar emot namnet på målschemat när en länk mellan tabeller skapas. Det här attributet är bara aktivt för länkelement.
* **template (string)**: det här attributet definierar en referens till ett `<element>`-element som delas av flera scheman. Definitionen kopieras automatiskt till det aktuella schemat.
* **translatedDefault (sträng)**: om ett @default-attribut hittas kan du med &quot;@translatedDefault&quot; definiera om ett uttryck så att det matchar det som definierats i @default, som ska samlas in av översättningsverktyget (intern användning).
* **translrExpr (sträng)**: om ett @expr-attribut hittas kan du med attributet @translr definiera om ett uttryck som matchar det som definierats i @expr och som samlas in av översättningsverktyget (intern användning).
* **type (MNTOKEN)**: definierar den typ av data som lagras i elementet.

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

* **unbound (boolean)**: Om attributet är aktiverat (unbound=&quot;true&quot;) deklareras länken som ett samlingselement för en 1-N-kardinalitet.
* **userEnum (sträng)**: tar emot det interna namnet för en öppen uppräkning. Uppräkningsvärden kan definieras av användaren i gränssnittet.
* **xml (booleskt)**: Om det här alternativet aktiveras lagras alla värden som definieras i elementet i XML i ett fält av typen &quot;mData&quot; i TEXT. Det innebär att det inte kommer att finnas någon filtrering eller sortering för dessa fält.
* **xmlChildren (boolesk)**: tvingar lagring för varje underordnad ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
