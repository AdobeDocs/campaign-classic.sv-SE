---
title: Element och attribut
seo-title: Element och attribut
description: Element och attribut
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a2cb740fe9b71435f602b738bd270fd3a0954901

---


# Element och attribut {#elements-and-attributes}

När du redigerar ett schema är ett godkännandesystem baserat på källschemat (xtk:srcSchema) tillgängligt. Vissa fel kan också upptäckas när databasen uppdateras med hjälp av &quot;Databasstrukturuppdatering...&quot;. guide.

Som standard är alla booleska typattribut&quot;false&quot; i Adobe Campaign-scheman. Om du vill aktivera dem måste du ange attributet i schemat och ange värdet till &quot;true&quot;.

## `<attribute>` element {#attribute--element}

### Innehållsmodell {#content-model}

attribute:==help

### Attribut {#attributes}

_operation (sträng), advanced (boolesk), applicableIf (sträng), autoIncrement (boolesk), beginTo (sträng), dataPolicy (sträng), dbEnum (sträng), defOnDuplicate (boolesk), default (sträng), desc (sträng), edit (sträng), enum (sträng), feature (sträng), featureDate (sträng) boolean), img (string), inout (string), label (string), length (string), localizable (boolean), name (MNTOKEN), notNull (boolean), pkgStatus (string), ref (string), required (boolean), sql (boolean), sqlDefault (string), sqlname (string), sqlqll table (string), target (MNTOKEN), template (string), translatedDefault (string), translateExpr (string), type (MNTOKEN), user (boolean), userEnum (string), visibleIf (string), xml (boolean)

### Överordnade {#parents}

`<element>`

### Barn {#children}

`<help>`

### Beskrivning {#description}

`<attribute>` kan du definiera ett fält i databasen.

### Användning och användningssammanhang {#use-and-context-of-use}

`<attribute>` -element måste deklareras i ett `<element>` element.

Den sekvens i vilken `<attribute>` element definieras i en `<srcschema>` påverkar inte fältgenereringssekvensen i databasen. Sekvensen skapas i alfabetisk ordning.

### Attributbeskrivning {#attribute-description}

* **_operation (sträng)**: definierar typen av skrivning i databasen.

   Det här attributet används främst vid utökning av scheman som ligger utanför boxen.

   Tillgängliga värden är:

   * &quot;none&quot;: enbart avstämning. Det innebär att Adobe Campaign återställer elementet utan att uppdatera det eller genererar ett fel om det inte finns.
   * &quot;insertOrUpdate&quot;: uppdatera med infogning. Det innebär att Adobe Campaign uppdaterar elementet eller skapar det om det inte finns.
   * &quot;insert&quot;: infogning. Det innebär att Adobe Campaign infogar elementet utan att kontrollera om det finns.
   * &quot;update&quot;: uppdatera. Det innebär att Adobe Campaign uppdaterar elementet eller genererar ett fel om det inte finns.
   * &quot;delete&quot;: borttagning. Det innebär att Adobe Campaign återställer och tar bort element.

* **avancerat (booleskt)**: när det här alternativet är aktiverat (@advanced=&quot;true&quot;) kan du dölja attributet i listan med tillgängliga fält som kan användas för att konfigurera en lista i ett formulär.
* **applicableIf (string)**: Med det här attributet kan du göra fält valfria. Elementet `<attribute>` beaktas när databasen uppdateras när villkoret uppfylls. &quot;applicableIf&quot; tar emot ett XTK-uttryck.
* **autoIncrement (boolean)**: om det här alternativet är aktiverat blir fältet räknare. Detta gör att du kan öka ett värde (mest ID). (extern användning)
* **tillhörTo (sträng)**: använder namnet och namnutrymmet för tabellen som delar fältet och fyller i schemat där attributet deklareras. (används endast i en `<schema>`).
* **dataPolicy (string)**: gör att du kan ange godkännandebegränsningar för värden som tillåts i SQL- eller XML-fältet. Värdena för det här attributet är:

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
* **default (string)**: Här kan du definiera värdet för standardfältet (anrop till en funktion, standardvärde). Det här attributet tar emot ett XTK-uttryck.
* **desc (sträng)**: I kan du infoga en beskrivning av attributet. Beskrivningen visas i gränssnittets statusfält.
* **edit (string)**: det här attributet anger vilken typ av indata som ska användas i formuläret som är länkat till schemat.
* **enum (string)**: tar emot namnet på uppräkningen som är länkad till fältet. Uppräkningen kan infogas i samma schema eller i ett fjärrschema.
* **expr (string)**: definierar ett förberäkningsuttryck för fält. Det här attributet tar emot en Xpath eller ett XTK-uttryck.
* **funktion (sträng)**: definierar ett egenskapsfält: Dessa fält används för att utöka data i en befintlig tabell, men med lagring i en bilagetabell. Godkända värden är:

   * &quot;shared&quot;: innehållet lagras i en delad tabell per datatyp
   * dedikerad: innehållet lagras i en dedikerad tabell
   SQL-egenskapstabeller byggs automatiskt baserat på den karakteristiska typen:

   * dedikerad: `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * delade: `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   Det finns två typer av egenskapsfält: enkla oà¹-fält där ett enda värde är godkänt för egenskapen och oà¹ flervalsfält där egenskapen är kopplad till ett samlingselement som kan innehålla flera värden.

   När en egenskap definieras i ett schema måste schemat ha en huvudnyckel baserad på ett enskilt fält (sammansatta nycklar tillåts inte).

* **featureDate (boolean)**: attribut länkat till egenskapsfältet &quot;@feature&quot;. Om värdet är &quot;true&quot; kan du ta reda på när värdet senast uppdaterades.
* **img (string)**: I kan du definiera en sökväg för en bild som är länkad till ett fält (namnutrymme + bildnamn) (exempel: img=&quot;cus:mypicture.jpg&quot;). I praktiken måste bilden importeras till programservern.
* **label (string)**: etikett länkad till fältet, som oftast är avsedd för användaren i gränssnittet. Du kan undvika namnbegränsningar.
* **length (string)**: max. antal tecken för ett värde av typen &quot;string&quot; i SQL-fältet. Om attributet @length inte anges skapas ett fält med 255 tecken automatiskt i Adobe Campaign.
* **lokaliserbar (boolesk)**: om det är aktiverat anger det här attributet att samlingsverktyget ska återställa värdet för attributet &quot;@label&quot; för översättning (intern användning).
* **name (MNTOKEN)**: namnet på det attribut som ska matcha namnet på fältet i tabellen. Värdet för attributet &quot;@name&quot; måste vara kort, helst på engelska, och måste uppfylla villkoren för XML-namngivning.

   När schemat skrivs till databasen läggs prefix automatiskt till i fältnamnet av Adobe Campaign:

   * &quot;i&quot;: -prefix för typen integer.
   * &quot;d&quot;: prefix för double-typen.
   * &quot;s&quot;: för teckensträngstypen.
   * &quot;ts&quot;: prefix för datatypen.
   Om du vill definiera namnet på fältet i tabellen ska du använda alternativet @sqlname när du definierar ett attribut.

* **notNull (boolean)**: Med kan ni definiera om Adobe Campaigns beteende för hantering av NULL-poster i databasen. Som standard är numeriska fält inte null och sträng- och datumtypsfält kan vara null.
* **pkgStatus (sträng)**: vid paketexport beaktas värden beroende på värdet för @pkgStatus:

   * &quot;always&quot;: finns alltid
   * &quot;never&quot;: aldrig presentera
   * &quot;standard (eller ingenting)&quot;: värdet exporteras förutom om det är standardvärdet eller om det inte är ett internt fält som inte är kompatibelt med andra instanser.

* **ref (sträng)**: det här attributet definierar en referens till ett `<attribute>` element som delas av flera scheman (definitionsfactoring). Definitionen kopieras inte till det aktuella schemat.
* **required (boolean)**: om attributet är aktiverat (@required=&quot;true&quot;) markeras fältet i gränssnittet. Fältets etikett blir röd i formulär.
* **sql (boolesk)**: om det här attributet är aktiverat (@sql=&quot;true&quot;) tvingas SQL-attributet att lagras, även om elementet som innehåller attributet har egenskapen xml=&quot;true&quot;.
* **sqlDefault (sträng)**: Med det här attributet kan du definiera standardvärdet som ska beaktas vid uppdatering av databasen om attributet @notNull aktiveras. Om det här attributet läggs till efter att attributet har skapats ändras inte schemabeteendet ens för de nya posterna. Om du vill ändra schemat och uppdatera värdet för nya poster måste du ta bort och skapa attributet igen.
* **sqlname (sträng)**: av fältet när register skapas. Om @sqlname inte anges används värdet för attributet &quot;@name&quot; som standard. När schemat skrivs i databasen läggs prefix till automatiskt beroende på fälttypen.
* **template (string)**: det här attributet definierar en referens till ett `<attribute>` element som delas av flera scheman. Definitionen kopieras automatiskt till det aktuella schemat.
* **translatedDefault (sträng)**: Om ett @default-attribut hittas kan du med &quot;@translatedDefault&quot; definiera om ett uttryck så att det matchar det som definierats i @default, som samlas in med översättningsverktyget (intern användning).
* **translatExpr (sträng)**: Om det finns ett @expr-attribut kan du med attributet @translr definiera om ett uttryck så att det matchar det som definierats i @expr, som ska samlas in med översättningsverktyget (intern användning).
* **type (MNTOKEN)**: fälttyp.

   Fälttyper är generiska. Beroende på vilken typ av databas som är installerad ändras den definierade typen i Adobe Campaign till ett värde som är specifikt för den databas som installeras under strukturuppdateringen.

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
   Om attributet @type lämnas tomt länkas en teckensträng (STRING) med längden 100 till fältet som standard.

   Om fältet är av STRING-typ och fältets namn inte anges av närvaron av attributet &quot;@sqlname&quot;, kommer namnet på fältet i databasen automatiskt att föregås av ett s. Det här operativläget liknar det för textfälten INTEGER (i), DOUBLE (d) och DATES (ts).

* **userEnum (sträng)**: tar emot det interna namnet på en open-uppräkning. Uppräkningens värden kan definieras av användaren i gränssnittet.
* **visibleIf (string)**: definierar ett villkor i form av ett XTK-uttryck som visar eller döljer attributet.

   >[!IMPORTANT]
   >
   >Attributet är dolt, men det går fortfarande att komma åt dess data.

* **xml (boolesk)**: Om det här alternativet är aktiverat har fältets värden inte något länkat SQL-fält. I Adobe Campaign skapas ett texttypsfält,&quot;mData&quot;, för postlagring. Det innebär att det inte finns någon filtrering eller sortering för dessa fält.

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

Exempel med ett &quot;@applicableIf&quot;: attributet &quot;contains&quot; skapas endast om antalet länder är större än 20.

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

## `<compute-string>` element {#compute-string--element}

### Innehållsmodell {#content-model-1}

compute-string:==EMPTY

### Attribut {#attributes-1}

@expr

### Överordnade {#parents-1}

`<element>`

### Barn {#children-1}

Ingen

### Beskrivning {#description-1}

Med elementet kan du generera en sträng baserat på ett XTK-uttryck som visar en&quot;inbyggd&quot; etikett i gränssnittet baserat på flera värden. `<compute-string>`

### Användning och användningssammanhang {#use-and-context-of-use-1}

När inget `<compute-string>` är definierat anges ett `<compute-string>` element som standard med värdena för primärnyckeln i schemat.

### Attributbeskrivning {#attribute-description-1}

* **expr (string)**: XTK och/eller Xpath-uttryck

### Exempel {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

Resultat av strängen som beräknats på en mottagare: &quot;John Doe (john.doe@aol.com)&quot;:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` element {#condition--element}

### Innehållsmodell {#content-model-2}

villkor:==TOM

### Attribut {#attributes-2}

* @boolOperator (sträng)
* @enabledIf (sträng)
* @expr (sträng)

### Överordnade {#parents-2}

`<sysfilter>`

### Barn {#children-2}

Ingen

### Beskrivning {#description-2}

Med det här elementet kan du definiera ett filtervillkor.

### Användning och användningssammanhang {#use-and-context-of-use-2}

Ett `<sysfiler>` element kan innehålla flera filtervillkor.

### Attributbeskrivning {#attribute-description-2}

* **boolOperator (sträng)**: om flera `<conditions>` är definierade inom samma `<sysfilter>` element kan du kombinera dem med det här attributet. Som standard är den logiska länken mellan `<condition>` elementen&quot;AND&quot;. Med attributet @boolOperator kan du kombinera länkarna OR och AND.
* **enabledIf (string)**: aktiveringstest.
* **expr (string)**: ett XTK-uttryck.

### Exempel {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` element {#dbindex--element}

### Innehållsmodell {#content-model-3}

dbindex:==nyckelfält

### Attribut {#attributes-3}

* @_operation (sträng)
* @applicableIf (sträng)
* @label (sträng)
* @name (MNTOKEN)
* @unique (boolean)

### Överordnade {#parents-3}

`<element>`

### Barn {#children-3}

`<keyfield>`

### Beskrivning {#description-3}

Med det här elementet kan du definiera ett index som är länkat till en tabell.

### Användning och användningssammanhang {#use-and-context-of-use-3}

Du kan definiera flera index. Ett index kan referera till ett eller flera fält i tabellen. Indexdeklarationen följer vanligtvis definitionen för huvudschemaelementet.

Ordningen på `<keyfield>` elementen som definieras i en `<dbindex>` är mycket viktig. Det första `<keyfield>` måste vara indexeringskriteriet som frågorna huvudsakligen bygger på.

Indexnamnet i databasen beräknas genom att sammanfoga tabellnamnet och indexnamnet. Till exempel: Tabellnamnet &quot;Sample&quot;, Namespace &quot;Cus&quot;, indexnamnet &quot;MyIndex&quot;-> namnet på indexfältet när en indexfråga skapas: &quot;CusSample_myIndex&quot;.

### Attributbeskrivning {#attribute-description-3}

* **_operation (sträng)**: definierar typen av skrivning i databasen.

   Det här attributet används främst vid utökning av scheman som ligger utanför boxen.

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

### Exempel {#examples-3}

Skapande av ett index i fältet&quot;id&quot;. (attributet &quot;@unique&quot; i elementet utlöser tillägg av SQL-nyckelordet &quot;UNIQUE&quot; när indexet skapas i databasen (frågan). `<dbindex>`

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

## `<element>` element {#element--element}

### Innehållsmodell {#content-model-4}

element:==(attribute) | compute-string | dbindex | standard | element | hjälp | join | nyckel | sysFilter | translatDefault)

### Attribut {#attributes-4}

_operation (string), advanced (boolean), aggregate (string), applicableIf (string), autopk (boolean), beginTo (string), convDate (string), dataPolicy (string), dataSource (string), dbEnum (string), defOnDuplicate (boolean), default (string), desc (string), displayAsField (boobox) lean), doesNotSupportDiff (boolesk), edit (string), emptyKeyValue (string), enum (string), enumImage (string), expandSchemaTarget (string), expr (string), externalJoin (boolean), feature (string), featureDate (boolean), filterPath (string), folderLink (string), folderModelModel (string) string), folderProcess (string), fullLoad (boolesk), hierarkisk (boolesk), hierarkisk sökväg (sträng), img (sträng), inout (sträng), integritet (sträng), label (sträng), labelSingular (sträng), length (sträng), localizable (boolesk), name (MNTOKEN), noDbIndex (boolesk), no Nyckel (booleskt), sorterad (booleskt), överflödig (booleskt), pkSequence (sträng), pkgStatus (sträng), ref (sträng), obligatoriskt (booleskt), revAdvanced (booleskt), revCardinality (sträng), revDesc (sträng), revExternalJoin (booleskt), revIntegrity (sträng) sträng), revLink (sträng), revTarget (sträng), revVisibleIf (sträng), sql (booleskt), sqlname (sträng), sqltable (sträng), tableSpace (sträng), tableSpaceIndex (sträng), target (MNTOKEN), template (sträng), temporaryTable (booleskt), translatedDefault (sträng), translateExpr (sträng) sträng), type (MNTOKEN), unbound (boolean), user (boolean), userEnum (string), visibleIf (string), xml (boolean), xmlChildren (boolean)

### Överordnade {#parents-4}

`<srcschema>`

`<element>`

### Barn {#children-4}

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

### Beskrivning {#description-4}

Det finns fyra typer av `<element>` element i Adobe Campaign:

* Rot `<element>` : definierar namnet på den SQL-tabell som matchar schemat.
* Struktur `<element>` : definierar en grupp av `<element>` eller `<attribute>` element.
* Länk `<element>` : definierar en länk. Elementen måste innehålla attributet &quot;@type=link&quot;.
* XML `<element>` : definierar ett texttypsfält, &quot;mData&quot;. Det här elementet måste innehålla attributet &quot;@type=xml&quot;.

### Attributbeskrivning {#attribute-description-4}

* **_operation (sträng)**: definierar typen av skrivning i databasen.

   Det här attributet används främst vid utökning av scheman som ligger utanför boxen.

   Tillgängliga värden är:

   * &quot;none&quot;: enbart avstämning. Det innebär att Adobe Campaign återställer elementet utan att uppdatera det eller genererar ett fel om det inte finns.
   * &quot;insertOrUpdate&quot;: uppdatera med infogning. Det innebär att Adobe Campaign uppdaterar elementet eller skapar det om det inte finns.
   * &quot;insert&quot;: infogning. Det innebär att Adobe Campaign infogar elementet utan att kontrollera om det finns.
   * &quot;update&quot;: uppdatera. Det innebär att Adobe Campaign uppdaterar elementet eller genererar ett fel om det inte finns.
   * &quot;delete&quot;: borttagning. Det innebär att Adobe Campaign återställer och tar bort element.

* **avancerat (booleskt)**: när det här alternativet är aktiverat (@advanced=&quot;true&quot;) kan du dölja attributet i listan med tillgängliga fält som kan användas för att konfigurera en lista i ett formulär.
* **mängd (sträng)**: Med kan du kopiera definitionen av ett `<element>` schema. Det här attributet tar emot en schemadeklaration i form av en &quot;namespace:name&quot;.
* **applicableIf (string)**: villkor för att använda indexet. Det här attributet tar emot ett XTK-uttryck.
* **autopk (boolesk)**: Om det här alternativet är aktiverat (autopk=&quot;true&quot;) definieras en unik nyckel automatiskt. Det här alternativet kan bara användas på schemats huvudelement. Varning! Adobe Campaign garanterar bara att nyckeln som genereras är unik. Det är inte säkert att nyckelvärdena är sekventiella och inkrementella.
* **dataPolicy (string)**: gör att du kan ange godkännandebegränsningar för värden som tillåts i SQL-fältet. Värdena för det här attributet är:

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
* **default (string)**: I kan du definiera elementbeteende (anrop till en funktion, standardvärde). Det här attributet tar emot ett XTK-uttryck.
* **desc (sträng)**: I kan du infoga en beskrivning av elementet. Beskrivningen visas i gränssnittets statusfält.
* **displayAsField (boolean)**: Om det här attributet är aktiverat `<element>` visas en länktyp som ett fält i trädvyn över scheman (&quot;fliken Struktur&quot;). På så sätt kan du visa en länk som ett lokalt fält och ändra dess beteende under en fråga. När elementet hittas i SELECT för en fråga används värdet för länkmålet. När elementet hittas i WHERE för en fråga används länkens underliggande nyckel.
* **edit (string)**: det här attributet anger vilken typ av indata som ska användas i formuläret som är länkat till schemat.
* **enum (string)**: tar emot namnet på uppräkningen som är länkad till fältet. Uppräkningen kan infogas i samma schema eller i ett fjärrschema.
* **expr (string)**: det här attributet definierar ett beräkningsfält för vilket ingen definition har lagrats i tabellen. Det tar emot en Xpath eller ett XTK-uttryck (sträng).
* **externalJoin (boolean)**: externt join in a &quot;link&quot; type element.
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
* **folderLink (string)**: det här attributet får namnet på länken som gör att du kan återställa filerna som innehåller entiteter.
* **folderModel (sträng)**: definierar den typ av mapp som aktiverar entitetslagring. Det här attributet definieras bara om @folderLink finns.
* **folderProcess (string)**: definierar länken där entitetsmodellinstanser lagras. Det här attributet definieras bara om @folderLink finns.
* **fullLoad (boolean)**: det här attributet framtvingar visning av alla poster i en tabell under fältval i ett formulär.
* **img (string)**: tar emot sökvägen till en bild som är länkad till ett element. Attributets värde är av typen &quot;namespace:image name&quot;. Till exempel: img=&quot;cus:myImage.jpg&quot;. I praktiken måste bilden importeras till programservern.
* **integritet (sträng)**: källtabellens referensintegritet i förhållande till måltabellen.

   Tillgängliga värden är:

   * &quot;define&quot;: Enheten tas inte bort i Adobe Campaign om länken refererar till den
   * &quot;normal&quot;: om du tar bort källförekomsten initieras länkens nycklar på målförekomsten (standardläge), initierar den här typen av integritet alla sekundärnycklar
   * &quot;own&quot;: borttagning av källförekomsten utlöser borttagning av målförekomsten
   * &quot;owncopy&quot;: liknar&quot;egen&quot; (vid borttagning) eller dubblerar förekomster (vid duplicering)
   * &quot;neutral&quot;: gör ingenting

* **label (string)**: element label.
* **labelSingular (string)**: etikett (singular form) för elementet som används i vissa delar av gränssnittet.
* **length (string)**: max. Antal tecken som är tillåtna för ett värde av typen &quot;string&quot; i SQL-fältet.
* **lokaliserbar (boolesk)**: om det är aktiverat anger det här attributet att samlingsverktyget ska återställa värdet för attributet &quot;@label&quot; för översättning (intern användning).
* **name (MNTOKEN)**: internt namn på elementet som matchar tabellens namn. Värdet för attributet &quot;@name&quot; måste vara kort, helst på engelska, och måste uppfylla de namnbegränsningar som är kopplade till XML.

   När schemat skrivs till databasen läggs prefix automatiskt till i fältnamnet av Adobe Campaign.

   * &quot;i&quot;: -prefix för typen integer.
   * &quot;d&quot;: prefix för double-typen.
   * &quot;s&quot;: för teckensträngstypen.
   * &quot;ts&quot;: prefix för datatypen.
   Om du vill definiera namnet på tabellen på ett självständigt sätt måste du använda attributet &quot;@sqltable&quot; i definitionen av huvudschemaelementet.

* **noDbIndex (boolesk)**: gör att du kan ange att elementet inte ska indexeras.
* **ordnad (boolesk)**: om attributet är aktiverat (ordered=&quot;true&quot;) behåller Adobe Campaign elementdeklarationssekvensen i ett XML-samlingselement.
* **pkSequence (sträng)**: tar emot namnet på den sekvens som ska användas för att beräkna en automatisk inkrementell nyckel. Det här attributet kan bara användas om en autoinkrementell nyckel har definierats för schemats rotelement.
* **pkgStatus (sträng)**: Vid paketexport kommer värden att beaktas som en funktion av värdet för det här attributet:

   * &quot;always&quot;: elementet alltid finns
   * &quot;never&quot;: elementet kommer aldrig att finnas
   * &quot;standard (eller ingenting)&quot;: elementet exporteras såvida det inte är standardelementet eller om det inte är ett internt fält och inte är kompatibelt med andra förekomster

* **ref (sträng)**: det här attributet definierar en referens till ett >element>-element som delas av flera scheman (definitionsfactoring). Definitionen kopieras inte till det aktuella schemat.
* **required (boolean)**: om attributet är aktiverat (@required=&quot;true&quot;) markeras fältet i gränssnittet. Fältets etikett blir röd i formulär.
* **revAdvanced (boolean)**: när det är aktiverat anger det här attributet att den motsatta länken är en &quot;avancerad&quot; länk.
* **revCardinality (string)**: det här attributet definierar kardinaliteten för en länk mellan två tabeller. Den används i en länktyp `<element>`.

   Möjliga värden är:

   * &quot;single&quot; : Enkel länk av typen 1-1
   * obunden: Länk för 1-N-typsamling
   Om attributet inte anges när länken skapas blir kardinaliteten 1-N som standard.

* **revDesc (sträng)**: det här attributet får en beskrivning som är länkad till den motsatta länken.
* **revExternalJoin (boolean)**: när det är aktiverat kan du med det här attributet tvinga det externa hörnet på motsatt länk.
* **revIntegrity (string)**: det här attributet definierar integriteten för målschemat. Samma värden som attributet &quot;@integrity&quot; tillåts. Som standard ger Adobe Campaign det&quot;normala&quot; värdet till det här attributet.
* **revLabel (sträng)**: den motsatta länkens etikett.
* **revLink (sträng)**: namnet på motsatt länk. Om värdet är &quot;_NONE_&quot; skapas ingen motsatt länk i målschemat.
* **revTarget (string)**: mål för motsatt länk.
* **sql (boolesk)**: om det här attributet är aktiverat (@sql=&quot;true&quot;) tvingas SQL-elementet att lagras, även om elementet har egenskapen xml=&quot;true&quot;.
* **sqlname (sträng)**: fältets namn när registret skapas. Om @sqlname inte anges används värdet för attributet @name som standard. När du skriver schemat till tabellen läggs prefix till automatiskt beroende på fälttypen.
* **sqltable (string)**: för huvudelementet i schemat, överför det här attributet namnet på SQL-tabellen som genereras som standard. Om @sqltable inte anges kommer standardnamnet att struktureras så här: namespace (first letter upper case) följt av värdet för SrcSchema &quot;@name&quot;.
* **tableSpace (sträng)**: Med det här attributet kan du ange ett nytt datalagringstabellutrymme för en tabell (giltigt i roten `<element>`).
* **tableSpaceIndex (sträng)**: Med det här attributet kan du ange ett nytt indexlagringsutrymme för en tabell (giltigt i roten `<element>`).
* **target (MNTOKEN)**: får namnet på målschemat när en länk mellan tabeller skapas. Det här attributet är bara aktivt för länkelement.
* **template (string)**: det här attributet definierar en referens till ett `<element>` element som delas av flera scheman. Definitionen kopieras automatiskt till det aktuella schemat.
* **translatedDefault (sträng)**: Om ett @default-attribut hittas kan du med &quot;@translatedDefault&quot; definiera om ett uttryck så att det matchar det som definierats i @default, som samlas in med översättningsverktyget (intern användning).
* **translatExpr (sträng)**: Om ett @expr-attribut hittas kan du med attributet @translr definiera om ett uttryck som matchar det som definierats i @expr och som samlas in med översättningsverktyget (internt bruk).
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

## `<enumeration>` element {#enumeration--element}

### Innehållsmodell {#content-model-5}

uppräkning:==(help| value)

### Attribut {#attributes-5}

* @basetype (sträng)
* @default (sträng)
* @desc (sträng)
* @label (sträng)
* @name (sträng)
* @template (sträng)

### Överordnade {#parents-5}

`<srcschema>`

### Barn {#children-5}

* `<help>`
* `<value>`

### Beskrivning {#description-5}

Med det här elementet kan vi definiera en värdeuppräkning. En uppräkning tillhör schemat som den är definierad i, men är tillgänglig via ett annat schema.

### Användning och användningssammanhang {#use-and-context-of-use-4}

Uppräkningar definieras i början av ett schema (innan huvudelementet definieras).

### Attributbeskrivning {#attribute-description-5}

* **basetype (sträng)**: typ av värden som lagras i uppräkningen.

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
   * DOMDocument
   * DOMElement
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

* **default (string)**: Standardvärde. Standardvärdet kan också vara ett av de värden som definieras i uppräkningen.
* **desc (sträng)**: uppräkningsbeskrivning.
* **label (string)**: uppräkningsetikett.
* **name (string)**: uppräkningens interna namn.
* **template (string)**: det här attributet definierar en referens till ett `<enumeration>` element som delas av flera scheman. Definitionen kopieras automatiskt till det aktuella schemat.

### Exempel {#examples-4}

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

Definition av en uppräkning med ett standardvärde:

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` element {#help--element}

### Innehållsmodell {#content-model-6}

help:==EMPTY

### Attribut {#attributes-6}

Ingen

### Överordnade {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### Barn {#children-6}

Ingen

### Beskrivning {#description-6}

Med det här elementet kan du beskriva ett `<element>` - eller `<attribute>` -element. Den kan bara innehålla text och lagras i XML i databasen.

### Attributbeskrivning {#attribute-description-6}

Det här elementet har inga attribut.

### Exempel {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` element {#join--element}

### Innehållsmodell {#content-model-7}

join:==EMPTY

### Attribut {#attributes-7}

* @dstFilterExpr (sträng)
* @xpath-dst (sträng)
* @xpath-src (sträng)

### Överordnade {#parents-7}

`<element>`

### Barn {#children-7}

Ingen

### Beskrivning {#description-7}

Här kan du definiera de fält som skapar en koppling mellan SQL-tabeller.

### Användning och användningssammanhang {#use-and-context-of-use-5}

Ett `<join>` element kan bara användas om det överordnade `<element>` elementet är av typen link. Det innebär att det överordnade elementet måste ha attributet &quot;@type=link&quot; deklarerat.

Du behöver inte ange namnet och namnutrymmet för fjärrtabellen i `<join>` elementet. De måste anges i det överordnade objektet `<element>`.

Länkar definieras som regel i slutet av schemat.

Om `<join>` elementet inte anges när länktypselementet definieras, placeras länken automatiskt på primärnycklarna för båda tabellerna.

### Attributbeskrivning {#attribute-description-7}

* **dstFilterExpr (sträng)**: Med det här attributet kan du begränsa antalet giltiga värden i fjärrtabellen.
* **xpath-dst (string)**: this-attributet tar emot en Xpath (@name-attribut för fjärrtabellen).
* **xpath-src (sträng)**: det här attributet tar emot ett Xpath-attribut (@name-attribut i det aktuella schemat).

### Exempel {#examples-6}

Länk mellan e-postfältet i den aktuella tabellen och fältet @compagny-id i fjärrtabellen:

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

Filtrerad länk till tabellen &quot;cus:Country&quot; baserat på innehållet i fältet &quot;@country&quot; som måste innehålla värdet &quot;EN&quot;:

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` element {#key--element}

### Innehållsmodell {#content-model-8}

nyckel:==nyckelfält

### Attribut {#attributes-8}

* @allowEmptyPart (boolesk)
* @applicableIf (sträng)
* @internal (boolesk)
* @label (sträng)
* @name (MNTOKEN)
* @noDbIndex (boolesk)

### Överordnade {#parents-8}

`<element>`

### Barn {#children-8}

`<keyfield>`

### Beskrivning {#description-8}

Med det här elementet kan du definiera en nyckel för att identifiera en post i tabellen.

En tabell måste ha minst en nyckel.

### Användning och användningssammanhang {#use-and-context-of-use-6}

Nycklar deklareras som regel efter huvudelementet i schemat och indexen.

En tangent kallas för sammansatt om den innehåller flera fält (t.ex. flera `<keyfield>` underordnade). Använd inte en sammansatt nyckel för att definiera en primärnyckel.

Om huvudelementet i schemat innehåller attributet &quot;@autopk=true&quot; är primärnyckeln unik. Vi kan bara ha en primärnyckel per schema.

De första 1000 identifierarna är reserverade, så om ett intervall med värden måste definieras för nycklar börjar du med 1000.

### Attributbeskrivning {#attribute-description-8}

* **allowEmptyPart (boolean)**: om det här attributet är aktiverat, anses nyckeln vara giltig om minst en av dess nycklar inte är tom. Om så är fallet är det tomma konceptvärdet &quot;0&quot; (booleskt eller för alla typer av numeriska data). Som standard måste alla tangenter som utgör en sammansatt nyckel anges.
* **applicableIf (string)**: Med det här attributet kan du göra nyckeln valfri. Den definierar det villkor som nyckeldefinitionen ska tillämpas på. Det här attributet tar emot ett XTK-uttryck.
* **internal (boolean)**: om det är aktiverat, talar det här attributet om för Adobe Campaign att nyckeln är primär.
* **label (string)**: nyckelns etikett.
* **name (MNTOKEN)**: nyckelns interna namn.
* **noDbIndex (boolesk)**: om den är aktiverad (noDbIndex=&quot;true&quot;) kommer fältet som matchar nyckeln inte att indexeras.

### Exempel {#examples-------}

Deklaration av en sammansatt nyckel som tillåter att antingen fältet &quot;@expr&quot; eller &quot;alias&quot; är tomt:

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

Deklaration av en primärnyckel i fältet &quot;Namn&quot; av STRING-typ i en `<srcschema>` och den matchande SQL-frågan:

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` element {#keyfield--element}

### Innehållsmodell {#content-model-9}

nyckelfält:==EMPTY

### Attribut {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

### Överordnade {#parents-9}

`<key>`  ,  `<dbindex />`

### Barn {#children-9}

Ingen

### Beskrivning {#description-9}

Det här elementet definierar de fält som ska integreras i ett index eller en nyckel.

### Attributbeskrivning {#attribute-description-9}

* **xlink (MNTOKEN)**: I kan du automatiskt referera till sekundärnycklar som definieras i kopplingen för en relationstabell (N-N-länk).
* **xpath (MNTOKEN)**: definition av ett index eller en nyckel för ett `<attribute>` element. Det här attributet tar emot en Xpath som definierar sökvägen till schemaattributet som definierar nyckeln eller indexet.

### Exempel {#examples-}

Markering av fältet &quot;sName&quot; i ett index med en Xpath på &quot;@name&quot;:

```
<keyfield xpath="@name"/>
```

## `<method>` element {#method--element}

### Innehållsmodell {#content-model-10}

method:==( help | parametrar)

### Attribut {#attributes-10}

* @_operation (sträng)
* @access (sträng)
* @const (boolesk)
* @hidden (boolesk)
* @label (sträng)
* @library (string)
* @name (MNTOKEN)
* @pkonly (boolesk)
* @static (boolesk)

### Överordnade {#parents-10}

`<methods>`  ,  `<interface />`

### Barn {#children-10}

* `<help>`
* `<parameters>`

### Beskrivning {#description-10}

Med det här elementet kan du definiera en SOAP-metod.

### Användning och användningssammanhang {#use-and-context-of-use-7}

SOAP-metoder möjliggör programprocesser.

&quot;@library&quot; krävs för att deklarera en ny metod (icke-inbyggd): namnutrymmet och namnet som används för biblioteket är oberoende av namnutrymmet och namnet på schemat där deklarationen finns.

### Attributbeskrivning {#attribute-description-10}

* **access (string)**: det här attributet definierar åtkomstkontroll för metoden. Om attributet saknas är identifiering obligatorisk. Tillgängliga värden är: &#39;anonymous&#39;, &#39;admin&#39; och &#39;sql&#39;.
* **const (boolean)**: om det är aktiverat betyder det här attributet att den deklarerade metoden ändrar entiteten
* **label (string)**: metodens etikett.
* **bibliotek (sträng)**: den här metoden är inte inbyggd i programmet. Det här attributet tar värdet för det metodbibliotek där metoddefinitionen finns (nms:mylibrary.js).
* **name (MNTOKEN)**: unikt metodnamn.
* **statisk (boolesk)**: Om det här attributet aktiveras betraktas metoden som självständig, och alla parametrar måste anges för metoden när den anropas.

### Exempel {#examples-7}

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

## `<methods>` element {#methods--element}

### Innehållsmodell {#content-model-11}

metoder:==metod

### Attribut {#attributes-11}

Ingen

### Överordnade {#parents-11}

`<srcschema>`

### Barn {#children-11}

method

### Beskrivning {#description-11}

Med det här elementet kan du definiera ett `<method>` element. Det är obligatoriskt för deklaration av en metod.

### Attributbeskrivning {#attribute-description-11}

Det här elementet har inga attribut.

### Exempel {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` element {#param--element}

### Innehållsmodell {#content-model-12}

param:==help

### Attribut {#attributes-12}

* @_operation (sträng)
* @desc (sträng)
* @enum (sträng)
* @inout (sträng)
* @label (sträng)
* @localizable (sträng)
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type (sträng)

### Överordnade {#parents-12}

`<parameters>`

### Barn {#children-12}

`<help>`

### Beskrivning {#description-12}

Med det här elementet kan du definiera en parameter för att anropa en SOAP-metod.

### Attributbeskrivning {#attribute-description-12}

* **desc (sträng)**: beskrivning som rör `<param>` elementet.
* **inout (sträng)**: det här attributet definierar om parametern finns vid indata (in) eller utdata (ut) för SOAP-anropet eller inte. Om det här attributet inte anges används standardparametern (&quot;@inout=in&quot;).
* **label (string)**: `<param>` label
* **localizable (string)**: om det är aktiverat anger det här attributet att samlingsverktyget ska återställa värdet för attributet &quot;@label&quot; för översättning (intern användning).
* **name (MNTOKEN)**: internt namn på `<param>`
* **type (string)**: this-attributet definierar typen av `<param>` element

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
   * DOMDocument
   * DOMElement
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

### Exempel {#examples-9}

Definition av den inkommande inställningen &quot;serviceName&quot; av teckensträngstyp:

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` element {#parameters--element}

### Innehållsmodell {#content-model-13}

parametrar:==param

### Attribut {#attributes-13}

Ingen

### Överordnade {#parents-13}

`<method>`

### Barn {#children-13}

`<param>`

### Beskrivning {#description-13}

Det här elementet definierar en grupp med `<parameter>` element.

### Användning och användningssammanhang {#use-and-context-of-use-8}

Det här elementet är obligatoriskt, även för ett enskilt `<param>` underordnat element till `<method>` elementet.

### Attributbeskrivning {#attribute-description-13}

Ingen

### Exempel {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` element {#srcschema--element}

### Innehållsmodell {#content-model-14}

srcSchema:=(attribut) | createdBy | data | element | uppräkning | hjälp | gränssnitt | metoder | modifiedBy)

### Attribut {#attributes-14}

created (datetime), createdBy-id (long), desc (string), entitySchema (string), extendedSchema (sträng), img (sträng), implements (sträng), label (sträng), labelSingular (sträng), lastModified (datetime), library (boolean), mappingType (sträng), modifiedBy-id (long), name (string), namespace (string), useRecycleBin (boolean), view (boolean), xtkschema (string)

### Överordnade {#parents-14}

Ingen

### Barn {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### Beskrivning {#description-14}

Detta `<srcschema>` är rotelementet i ett schema. Det är indatapunkten för definitionen av schemat.

### Användning och användningssammanhang {#use-and-context-of-use-9}

Schemapresentation är tillgänglig i [Om schemareferens](../../configuration/using/about-schema-reference.md) och [schemastruktur](../../configuration/using/schema-structure.md).

### Attributbeskrivning {#attribute-description-14}

* **skapat (datetime)**: det här attributet innehåller information om datum och tid då scheman skapades. Den har ett&quot;Date Time&quot;-formulär. De värden som visas hämtas från servern. Tiden visas i UTC-format.
* **createdBy-id (long)**: är identifieraren för den operator som skapade schemat.
* **desc (sträng)**: schemabeskrivning
* **entitySchema (sträng)**: grundschema som syntax och godkännande baseras på (som standard för Adobe Campaign: xtk:srcSchema). När du sparar det aktuella schemat kommer Adobe Campaign att godkänna dess grammatik med det schema som deklarerats i attributet @xtkschema.
* **extendedSchema (sträng)**: tar emot namnet på det schema som är utanför rutan och som det aktuella schematillägget baseras på. Formuläret är &quot;namespace:name&quot;.
* **img (string)**: ikon länkad till schemat (kan definieras i guiden för att skapa schema).
* **label (string)**: schemaetikett.
* **labelSingular (string)**: label (singular) for display in the interface.
* **lastModified (datetime)**: det här attributet innehåller information om datum och tid för den senaste ändringen. Den har ett&quot;Date Time&quot;-formulär. De värden som visas hämtas från servern. Tiden visas i UTC-format.
* **bibliotek (booleskt)**: användning av schemat som ett bibliotek och inte som en entitet. Andra scheman kan därför referera till det här schemat tack vare attributen @ref och @template.
* **mappingType (sträng)**:

   * &quot;sql&quot;: databasmappning
   * &quot;textFile&quot;: textfilsmappning
   * &quot;xmlFile&quot;: Textfilsmappning i XML-format
   * &quot;binaryFile&quot;: binär filmappning

* **modifiedBy-id (long)**: matchar identifieraren för den operator som ändrade schemat.
* **name (string)**: unikt schemanamn.
* **namespace (string)**: schemats namnrymd (standard: nms, xtk, nl). När du skapar ett nytt schema för ett projekt rekommenderar vi att du använder ett dedikerat namnutrymme.
* **useRecycleBin (boolesk)**: aktiverar papperskorgen i programmet. Borttagna poster placeras i papperskorgen innan de tas bort. Den här funktionen är bara tillgänglig i läget &quot;Leverans&quot;.
* **vy (boolesk)**: om den är aktiverad (@view=&quot;true&quot;) används schemat som vy. Databasstrukturuppdateringsguiden tar inte hänsyn till schemat. Det här alternativet används främst för att referera till externa tabeller.
* **xtkschema (sträng)**: namnet på schemat som definierar schemagrammatik (xtk:srcSchema som standard).

### Exempel {#examples-11}

`<srcschema>` elementet i &quot;nms:delivery&quot; ur kartongschemat

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` element {#sysfilter--element}

### Innehållsmodell {#content-model-15}

sysFilter:==villkor

### Attribut {#attributes-15}

Ingen

### Överordnade {#parents-15}

`<element>`

### Barn {#children-15}

`<condition>`

### Beskrivning {#description-15}

Med det här elementet kan du definiera ett filter.

### Attributbeskrivning {#attribute-description-15}

Det här elementet har inga attribut.

### Exempel {#examples-12}

Definition av ett filter med ett villkor i @name-attributet:

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` element {#value--element}

### Innehållsmodell {#content-model-16}

value:==help

### Attribut {#attributes-16}

* @applicableIf (sträng)
* @desc (sträng)
* @enabledIf (sträng)
* @img (sträng)
* @label (sträng)
* @name (sträng)
* @value (sträng)

### Överordnade {#parents-16}

`<enumeration>`

### Barn {#children-16}

`<help>`

### Beskrivning {#description-16}

Med det här elementet kan du definiera de värden som lagras i en uppräkning.

### Attributbeskrivning {#attribute-description-16}

* **applicableIf (string)**: Med det här attributet kan du göra ett uppräkningsvärde valfritt. Det tar emot ett XTK-uttryck.
* **desc (sträng)**: beskrivning av uppräkningsvärdet.
* **enabledIf (string)**: villkor för aktivering av uppräkningsvärdet.
* **img (string)**: bild länkad till uppräkningen i formuläret &quot;namespace:image_name&quot;. Bilden måste importeras till programservern.
* **label (string)**: uppräkningsvärdets etikett.
* **name (string)**: uppräkningsvärdets interna namn.
* **value (string)**: uppräkningsvärdets värde. Värdetypen definieras baserat på uppräkningstypen. Om uppräkningen är av strängtyp kan den bara innehålla teckensträngtypsvärden.

### Exempel {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
