---
product: campaign
title: Element och attribut
description: Element och attribut
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---

# element {#element--element}

![](../../../assets/v7-only.svg)

## Innehållsmodell {#content-model-4}

element:==(attribute) | compute-string | dbindex | standard | element | hjälp | join | nyckel | sysFilter | translatDefault)

## Attribut {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), beginTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boobox) lean), doesNotSupportDiff (booleskt), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (booleskt), feature (string), featureDate (booleskt), filterPath (string), folderLink (string), folderModelModel (string) string), folderProcess (string), fullLoad (boolesk), hierarkisk (boolesk), hierarkisk sökväg (sträng), img (sträng), inout (sträng), integritet (sträng), label (sträng), labelSingular (sträng), length (sträng), localizable (boolesk), name (MNTOKEN), noDbIndex (boolesk), no Nyckel (booleskt), sorterad (booleskt), överflödig (booleskt), pkSequence (sträng), pkgStatus (sträng), ref (sträng), obligatoriskt (booleskt), revAdvanced (booleskt), revCardinality (sträng), revDesc (sträng), revExternalJoin (booleskt), revIntegrity (sträng) sträng), revLink (sträng), revTarget (sträng), revVisibleIf (sträng), sql (booleskt), sqlname (sträng), sqltable (sträng), tableSpace (sträng), tableSpaceIndex (sträng), target (MNTOKEN), template (sträng), temporaryTable (booleskt), translatedDefault (sträng), translateExpr (sträng) sträng), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

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

Det finns fyra typer av `<element>`  element i Adobe Campaign:

* Rot `<element>`  : definierar namnet på den SQL-tabell som matchar schemat.
* Struktur `<element>`  : definierar en grupp med  `<element>`   eller   `<attribute>`    -element.
* Länk `<element>`  : definierar en länk. Elementen måste innehålla attributet &quot;@type=link&quot;.
* XML `<element>`  : definierar ett texttypsfält, &quot;mData&quot;. Det här elementet måste innehålla attributet &quot;@type=xml&quot;.

## Attributbeskrivning {#attribute-description-4}

* **operation (sträng)**: definierar typen av skrivning i databasen.

   Det här attributet används främst vid utökning av scheman som ligger utanför rutan.

   Tillgängliga värden är:

   * &quot;none&quot;: enbart avstämning. Det innebär att Adobe Campaign återställer elementet utan att uppdatera det eller genererar ett fel om det inte finns.
   * &quot;insertOrUpdate&quot;: uppdatera med infogning. Det innebär att Adobe Campaign uppdaterar elementet eller skapar det om det inte finns.
   * &quot;insert&quot;: infogning. Det innebär att Adobe Campaign infogar elementet utan att kontrollera om det finns.
   * &quot;update&quot;: uppdatera. Det innebär att Adobe Campaign uppdaterar elementet eller genererar ett fel om det inte finns.
   * &quot;delete&quot;: borttagning. Det innebär att Adobe Campaign återställer och tar bort element.

* **avancerat (booleskt)**: när det här alternativet är aktiverat (@advanced=&quot;true&quot;) kan du dölja attributet i listan med tillgängliga fält som kan användas för att konfigurera en lista i ett formulär.
* **mängd (sträng)**: låter dig kopiera definitionen av en `<element>`  via ett annat schema. Det här attributet tar emot en schemadeklaration i form av en &quot;namespace:name&quot;.
* **applicableIf (string)**: villkor för att använda indexet. Det här attributet tar emot ett XTK-uttryck.
* **autopk (boolesk)**: Om det här alternativet är aktiverat (autopk=&quot;true&quot;) definieras en unik nyckel automatiskt. Det här alternativet kan bara användas på schemats huvudelement. Varning! Adobe Campaign garanterar bara att nyckeln som genereras är unik. Det är inte säkert att nyckelvärdena är sekventiella och inkrementella.
* **dataPolicy (sträng)**: gör att du kan ange godkännandebegränsningar för värden som tillåts i SQL-fältet. Värdena för det här attributet är:

   * &quot;none&quot;: inget värde
   * &quot;smartCase&quot;: versaler
   * &quot;lowerCase&quot;: gemener
   * &quot;upperCase&quot;: versaler
   * &quot;email&quot;: e-postadress
   * &quot;phone&quot;: telefonnummer
   * &quot;identifierare&quot;: identifierarnamn
   * &quot;resIdentifier&quot;: filnamn

* **dbEnum (sträng)**: tar emot det interna namnet på en sluten uppräkning. Uppräkningsvärdena måste definieras i `<srcschema>`.
* **defOnDuplicate (boolesk)**: om det här attributet aktiveras, kommer standardvärdet (definierat i @default) automatiskt att tillämpas på posten när en post dupliceras.
* **default (sträng)**: I kan du definiera elementbeteende (anrop till en funktion, standardvärde). Det här attributet tar emot ett XTK-uttryck.
* **desc (sträng)**: I kan du infoga en beskrivning av elementet. Beskrivningen visas i gränssnittets statusfält.
* **displayAsField (boolesk)**: om attributet är aktiverat, en &quot;link&quot;-typ `<element>`  visas som ett fält i trädvyn över scheman (&quot;fliken Struktur&quot;). På så sätt kan du visa en länk som ett lokalt fält och ändra dess beteende under en fråga. När elementet hittas i SELECT för en fråga används värdet för länkmålet. När elementet hittas i WHERE för en fråga används länkens underliggande nyckel.
* **edit (string)**: det här attributet anger vilken typ av indata som ska användas i formuläret som är länkat till schemat.
* **enum (sträng)**: tar emot namnet på uppräkningen som är länkad till fältet. Uppräkningen kan infogas i samma schema eller i ett fjärrschema.
* **expr (sträng)**: det här attributet definierar ett beräkningsfält för vilket ingen definition har lagrats i tabellen. Det tar emot en Xpath eller ett XTK-uttryck (sträng).
* **externalJoin (boolesk)**: externt join in a &quot;link&quot; type element.
* **funktion (sträng)**: definierar ett egenskapsfält: Dessa fält används för att utöka data i en befintlig tabell, men med lagring i en bilagetabell. Godkända värden är:

   * &quot;shared&quot;: innehållet lagras i en delad tabell per datatyp
   * dedikerad: innehållet lagras i en dedikerad tabell

   SQL-egenskapstabeller byggs automatiskt baserat på den karakteristiska typen:

   * dedikerad: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * delade: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   Det finns två typer av egenskapsfält: enkla fält där ett enda värde är godkänt för egenskapen, och flervalsfält där egenskapen är länkad till ett samlingselement som kan innehålla flera värden.

   När en egenskap definieras i ett schema måste schemat ha en huvudnyckel baserad på ett enskilt fält (sammansatta nycklar tillåts inte).

* **featureDate (boolean)**: attribut länkat till egenskapsfältet &quot;@feature&quot;. Om värdet är &quot;true&quot; kan du ta reda på när värdet senast uppdaterades.
* **filterPath (sträng)**: det här attributet tar emot en Xpath och låter dig definiera ett filter för ett fält.
* **folderLink (sträng)**: det här attributet får namnet på länken som gör att du kan återställa filerna som innehåller entiteter.
* **folderModel (sträng)**: definierar den typ av mapp som aktiverar entitetslagring. Det här attributet definieras bara om @folderLink finns.
* **folderProcess (sträng)**: definierar länken där entitetsmodellinstanser lagras. Det här attributet definieras bara om @folderLink finns.
* **fullLoad (boolean)**: det här attributet framtvingar visning av alla poster i en tabell under fältval i ett formulär.
* **img (sträng)**: tar emot sökvägen till en bild som är länkad till ett element. Attributets värde är av typen &quot;namespace:image name&quot;. Till exempel: img=&quot;cus:myImage.jpg&quot;. I praktiken måste bilden importeras till programservern.
* **integritet (sträng)**: källtabellens referensintegritet i förhållande till måltabellen.

   Tillgängliga värden är:

   * &quot;define&quot;: Adobe Campaign tar inte bort enheten om den refereras via länken
   * &quot;normal&quot;: om du tar bort källförekomsten initieras länkens nycklar på målförekomsten (standardläge), initierar den här typen av integritet alla sekundärnycklar
   * &quot;own&quot;: borttagning av källförekomsten utlöser borttagning av målförekomsten
   * &quot;owncopy&quot;: liknar&quot;egen&quot; (vid borttagning) eller dubblerar förekomster (vid duplicering)
   * &quot;neutral&quot;: gör ingenting

* **label (string)**: element label.
* **labelSingular (string)**: etikett (singular form) för elementet som används i vissa delar av gränssnittet.
* **length (sträng)**: max. Antal tecken som är tillåtna för ett värde av typen &quot;string&quot; i SQL-fältet.
* **lokaliserbar (boolesk)**: om det är aktiverat anger det här attributet att samlingsverktyget ska återställa värdet för attributet &quot;@label&quot; för översättning (intern användning).
* **name (MNTOKEN)**: internt namn på det element som matchar tabellens namn. Värdet för attributet &quot;@name&quot; måste vara kort, helst på engelska, och måste uppfylla de namnbegränsningar som är kopplade till XML.

   När schemat skrivs till databasen läggs prefix automatiskt till i fältnamnet av Adobe Campaign.

   * &quot;i&quot;: -prefix för typen integer.
   * &quot;d&quot;: prefix för double-typen.
   * &quot;s&quot;: för teckensträngstypen.
   * &quot;ts&quot;: prefix för datatypen.

   Om du vill definiera namnet på tabellen på ett självständigt sätt måste du använda attributet &quot;@sqltable&quot; i definitionen av huvudschemaelementet.

* **noDbIndex (boolesk)**: gör att du kan ange att elementet inte ska indexeras.
* **beställd (boolesk)**: om attributet är aktiverat (ordered=&quot;true&quot;), behåller Adobe Campaign elementdeklarationssekvensen i ett XML-samlingselement.
* **pkSequence (sträng)**: tar emot namnet på den sekvens som ska användas för att beräkna en automatisk inkrementell nyckel. Det här attributet kan bara användas om en autoinkrementell nyckel har definierats för schemats rotelement.
* **pkgStatus (sträng)**: Vid paketexport kommer värden att beaktas som en funktion av värdet för det här attributet:

   * &quot;always&quot;: elementet alltid finns
   * &quot;never&quot;: elementet kommer aldrig att finnas
   * &quot;standard (eller ingenting)&quot;: elementet exporteras såvida det inte är standardelementet eller om det inte är ett internt fält och inte är kompatibelt med andra förekomster

* **ref (sträng)**: det här attributet definierar en referens till ett >element>-element som delas av flera scheman (definitionsfactoring). Definitionen kopieras inte till det aktuella schemat.
* **required (boolean)**: om attributet är aktiverat (@required=&quot;true&quot;) markeras fältet i gränssnittet. Fältets etikett blir röd i formulär.
* **revAdvanced (boolean)**: när det är aktiverat anger det här attributet att den motsatta länken är en &quot;avancerad&quot; länk.
* **revCardinality (sträng)**: det här attributet definierar kardinaliteten för en länk mellan två tabeller. Den används i en länktyp `<element>`.

   Möjliga värden är:

   * &quot;single&quot; : Enkel länk av typen 1-1
   * obunden: Länk för 1-N-typsamling

   Om attributet inte anges när länken skapas blir kardinaliteten 1-N som standard.

* **revDesc (sträng)**: det här attributet får en beskrivning som är länkad till den motsatta länken.
* **revExternalJoin (boolean)**: när det är aktiverat kan du med det här attributet tvinga det externa hörnet på motsatt länk.
* **revIntegrity (sträng)**: det här attributet definierar integriteten för målschemat. Samma värden som attributet &quot;@integrity&quot; tillåts. Som standard ger Adobe Campaign attributet&quot;normal&quot;.
* **revLabel (sträng)**: den motsatta länkens etikett.
* **revLink (sträng)**: namnet på motsatt länk. Om värdet är &quot;_INGEN_&quot;, ingen motsatt länk skapas i målschemat.
* **revTarget (sträng)**: mål för motsatt länk.
* **sql (boolesk)**: om det här attributet är aktiverat (@sql=&quot;true&quot;) tvingas SQL-elementet att lagras, även om elementet har egenskapen xml=&quot;true&quot;.
* **sqlname (sträng)**: fältets namn när registret skapas. Om @sqlname inte anges används värdet för attributet @name som standard. När du skriver schemat till tabellen läggs prefix till automatiskt beroende på fälttypen.
* **sqltable (sträng)**: för huvudelementet i schemat, överför det här attributet namnet på SQL-tabellen som genereras som standard. Om @sqltable inte anges kommer standardnamnet att struktureras så här: namespace (first letter upper case) följt av värdet för SrcSchema &quot;@name&quot;.
* **tableSpace (sträng)**: Med det här attributet kan du ange ett nytt tabellutrymme för datalagring för en tabell (giltigt i roten) `<element>`).
* **tableSpaceIndex (sträng)**: Med det här attributet kan du ange ett nytt indexlagringsutrymme för en tabell (giltigt på roten) `<element>`).
* **target (MNTOKEN)**: får namnet på målschemat när en länk mellan tabeller skapas. Det här attributet är bara aktivt för länkelement.
* **template (string)**: this-attributet definierar en referens till en `<element>` element som delas av flera scheman. Definitionen kopieras automatiskt till det aktuella schemat.
* **translatedDefault (sträng)**: Om ett @default-attribut hittas kan du med &quot;@translatedDefault&quot; definiera om ett uttryck så att det matchar det som definierats i @default, som samlas in med översättningsverktyget (intern användning).
* **translateExpr (sträng)**: Om ett @expr-attribut hittas kan du med attributet @translr definiera om ett uttryck som matchar det som definierats i @expr och som samlas in med översättningsverktyget (internt bruk).
* **type (MNTOKEN)**: definierar vilken typ av data som lagras i elementet.

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

* **obunden (boolesk)**: om attributet är aktiverat (unbound=&quot;true&quot;) deklareras länken som ett samlingselement för en 1-N-kardinalitet.
* **userEnum (sträng)**: tar emot det interna namnet på en open-uppräkning. Uppräkningsvärden kan definieras av användaren i gränssnittet.
* **xml (boolesk)**: Om det här alternativet är aktiverat lagras alla värden som definieras i elementet i XML i ett texttypsfält, &quot;mData&quot;. Det innebär att det inte kommer att finnas någon filtrering eller sortering för dessa fält.
* **xmlChildren (boolean)**: tvingar lagring för varje underordnat objekt ( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
