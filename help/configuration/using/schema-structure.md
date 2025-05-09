---
product: campaign
title: Förstå schemastrukturen i Adobe Campaign
description: Schemastruktur
feature: Custom Resources
role: Data Engineer, Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '1511'
ht-degree: 1%

---

# Förstå schemastruktur {#schema-structure}

Grundstrukturen för ett schema beskrivs nedan.

## Datascheman  {#data-schema}

För en `<srcschema>`är strukturen följande:

```sql
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

XML-dokumentet för ett dataschema måste innehålla rotelementet **`<srcschema>`** med attributen **name** och **namespace** för att schemanamnet och dess namnutrymme ska kunna fyllas i.

```sql
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Låt oss använda följande XML-innehåll för att illustrera strukturen för ett dataschema:

```sql
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Med motsvarande dataschema:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## Beskrivning {#description}

Startpunkten för schemat är dess huvudelement. Det är enkelt att identifiera eftersom det har samma namn som schemat och bör vara underordnat rotelementet. Beskrivningen av innehållet börjar med det här elementet.

I det här exemplet representeras huvudelementet av följande rad:

```
<element name="recipient">
```

Elementen **`<attribute>`** och **`<element>`** som följer huvudelementet används för att definiera platser och namn för dataobjekten i XML-strukturen.

I vårt exempelschema är följande:

```sql
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Följande regler gäller:

* Varje **`<element>`** och **`<attribute>`** måste identifieras med namn via attributet **name**.

  >[!IMPORTANT]
  >
  >Elementets namn ska vara kortfattat, helst på engelska, och endast innehålla tecken som tillåts i XML-namnregler.

* Endast **`<element>`** element kan innehålla **`<attribute>`** element och **`<element>`** element i XML-strukturen.
* Ett **`<attribute>`**-element måste ha ett unikt namn i en **`<element>`**.
* Du bör använda **`<elements>`** i flerradiga datasträngar.

## Datatyper {#data-types}

Datatypen anges via attributet **type** i elementen **`<attribute>`** och **`<element>`** .

En detaljerad lista finns i beskrivningen av elementet [`<attribute>`](../../configuration/using/schema/attribute.md) och elementet[`<element>`](../../configuration/using/schema/element.md).

När det här attributet inte är ifyllt **är sträng** standarddatatypen om inte elementet innehåller underordnade element. Om det gör det används det bara för att strukturera elementen hierarkiskt (**`<location>`** element i vårt exempel).

Följande datatyper stöds i scheman:

* **sträng**: teckensträng. Exempel: förnamn, stad osv.

  Storleken kan anges via attributet **length** (valfritt, standardvärde 255).

* **boolesk**: Booleskt fält. Exempel på möjliga värden: true/false, 0/1, yes/no, osv.
* **byte**, **short**, **long**: heltal (1 byte, 2 byte, 4 byte). Exempel: ålder, kontonummer, antal poäng osv.
* **double**: flyttal med dubbel precision. Exempel: ett pris, en kurs, osv.
* **Datum**, Datum/ **Tid**: Datum och Datum + Tider. Exempel: ett födelsedatum, ett inköpsdatum osv.
* **datetimenotz**: Datum + tid utan tidszonsdata.
* **Tidsspann**: varaktigheter. Exempel: senioritet.
* **PM**: långa textfält (flera rader). Exempel: en beskrivning, en kommentar, osv.
* **uid**: Uniqueidentifier-fält som stöder ett GUID (stöds endast i Microsoft SQL Server).

  >[!NOTE]
  >
  >Om du vill innehålla ett **uid**-fält i andra RDBMS än Microsoft SQL Server, måste `the newuuid()`-funktionen läggas till och slutföras med standardvärdet.

Här är vårt exempelschema med de angivna typerna:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### Mappa typer av Adobe Campaign-/DBMS-data {#mapping-the-types-of-adobe-campaign-dbms-data}

I tabellen nedan visas mappningarna för de typer av data som genereras av Adobe Campaign för de olika databashanteringssystemen.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Sträng<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 om unicode används)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolesk<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> ANTAL(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Kort<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Dubbel<br /> </td> 
   <td> DUBBEL PRECISION<br /> </td> 
   <td> FLYTA<br /> </td> 
  </tr> 
  <tr> 
   <td> Lång<br /> </td> 
   <td> HELTAL<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> ANTAL(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> Tid<br /> </td> 
   <td> TID<br /> </td> 
   <td> FLYTTA <br /> </td> 
  </tr> 
  <tr> 
   <td> DatumTid<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATUM<br /> </td> 
  </tr> 
  <tr> 
   <td> Tidsintervall <br /> </td> 
   <td> DUBBELPRECISION<br /> </td> 
   <td> FLYTA<br /> </td> 
  </tr> 
  <tr> 
   <td> Pm<br /> </td> 
   <td> SMS<br /> </td> 
   <td> CLOB (NCLOB om Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blobb<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Egenskaper {#properties}

Elementen **`<elements>`** och **`<attributes>`** i dataschemat kan berikas med olika egenskaper. Du kan fylla i en etikett för att beskriva det aktuella elementet.

### Etiketter och beskrivningar {#labels-and-descriptions}

* Med **egenskapen label** kan du ange en kort beskrivning.

  >[!NOTE]
  >
  >Etiketten är associerad med det aktuella språket i instansen.

  **Exempel**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  Etiketten visas i indataformuläret för Adobe Campaign klientkonsol:

  ![](assets/d_ncs_integration_schema_label.png)

* Med **egenskapen desc** kan du ange en lång beskrivning.

  Beskrivningen visas i indataformuläret i statusfältet i huvudfönstret i Adobe Campaign-klientkonsolen.

  >[!NOTE]
  >
  >Beskrivningen är associerad med instansens aktuella språk.

  **Exempel**:

  ```sql
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### Standardvärden {#default-values}

**Använd egenskapen default** för att definiera ett uttryck som returnerar ett standardvärde när du skapar innehåll.

Värdet måste vara ett uttryck som är kompatibelt med XPath-språket. Mer information finns i [Referera med XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Exempel**:

* Aktuellt datum: **default=&quot;GetDate()&quot;**
* Räknare: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  I det här exemplet skapas standardvärdet med hjälp av sammanfogningen av en sträng och anropet av funktionen **CounterValue** med ett kostnadsfritt räknarnamn. Det returnerade talet ökas med ett steg vid varje infogning.

  >[!NOTE]
  >
  >I Adobe Campaign klientkonsol bläddrar du till mappen **[!UICONTROL Administration > Counters]** i Utforskaren för att hantera räknare.

Om du vill länka ett standardvärde till ett fält kan du använda `<default>` eller `<sqldefault>`   fält.

`<default>` : Gör att du kan fylla i fältet i förväg med ett standardvärde när du skapar enheter. Värdet kommer inte att vara ett standardvärde för SQL.

`<sqldefault>` : gör att du kan ha ett mervärde när du skapar ett fält. Det här värdet visas som ett SQL-resultat. Under en schemauppdatering påverkas endast de nya posterna av det här värdet.

### Uppräkningar {#enumerations}

#### Öppna uppräkning {#free-enumeration}

Med egenskapen **userEnum** kan du definiera en öppen uppräkning för att lagra och visa de värden som anges i det här fältet.

Syntaxen är följande:

`userEnum="name of enumeration"`

Dessa värden visas i en nedrullningsbar lista från indataformuläret:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>I Adobe Campaign klientkonsol bläddrar du till mappen **[!UICONTROL Administration > Enumerations]** i Utforskaren för att hantera uppräkningar.

#### Ange uppräkning {#set-enumeration}

Med **egenskapen enum** kan du definiera en fast uppräkning som används när listan över möjliga värden är känd i förväg.

Attributet **enum** refererar till definitionen av en uppräkningsklass som fylls i i schemat utanför huvudelementet.

Uppräkningar gör att användaren kan välja ett värde i en nedrullningsbar lista i stället för att ange värdet i ett vanligt inmatningsfält:

![](assets/d_ncs_integration_schema_enum.png)

Exempel på en uppräkningsdeklaration i dataschemat:

```sql
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

En uppräkning deklareras utanför huvudelementet via elementet **`<enumeration>`**.

Uppräkningsegenskaperna är följande:

* **baseType**: typ av data som är associerade med värdena
* **label**: Beskrivning av uppräkningen
* **name**: namnet på uppräkningen
* **Standard**: Standardvärde för uppräkningen

Uppräkningsvärdena deklareras i elementet **`<value>`** med följande attribut:

* **namn**: namnet på värdet som lagras internt
* **label**: etikett visas i det grafiska gränssnittet

#### dbenum-uppräkning {#dbenum-enumeration}

*Med egenskapen **dbenum** kan du definiera en uppräkning vars egenskaper liknar egenskaperna för egenskapen **enum**.

Attributet **name** lagrar dock inte värdet internt, utan lagrar en kod som gör att du kan utöka de berörda tabellerna utan att ändra deras schema.

Den här uppräkningen används till exempel för att ange kampanjens karaktär.

![](assets/d_ncs_configuration_schema_dbenum.png)

### Exempel {#example}

Här är vårt exempelschema med egenskaperna ifyllda:

```sql
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## Samlingar {#collections}

En samling är en lista med element med samma namn och samma hierarkiska nivå.

Med **attributet unbound** med värdet &quot;true&quot; kan du fylla i ett samlingselement.

**Exempel**: definition av samlingselementet **`<group>`** i schemat.

```sql
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Med projektion av XML-innehållet:

```sql
<group label="Group1"/>
<group label="Group2"/>
```

## Referera med XPath {#referencing-with-xpath}

Språket XPath används i Adobe Campaign för att referera till ett element eller attribut som tillhör ett dataschema.

XPath är en syntax som gör att du kan hitta en nod i trädet i ett XML-dokument.

Elementen anges med sitt namn och attributen anges med namnet före tecknet&quot;@&quot;.

**Exempel**:

* **@email**: markerar e-postmeddelandet,
* **location/@city**: väljer attributet &quot;city&quot; under elementet **`<location>`**
* **../@email**: väljer e-postadressen från det överordnade elementet för det aktuella elementet
* **group`[1]/@label`**: markerar attributet &quot;label&quot; som är underordnat det första **`<group>`**-samlingselementet
* **group`[@label='test1']`**: markerar attributet &quot;label&quot; som är underordnat elementet **`<group>`** och innehåller värdet &quot;test1&quot;

>[!NOTE]
>
>En ytterligare begränsning läggs till när banan korsar ett underelement. I det här fallet måste följande uttryck placeras inom hakparenteser:
>
>* **location/@city** är inte giltig. Använd **`[location/@city]`**
>* **`[@email]`** och **@email** är likvärdiga
>

Det går också att definiera komplexa uttryck, till exempel följande aritmetiska operationer:

* **@gender+1**: lägger till 1 till innehållet i könsattributet **&#x200B;**,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: konstruerar en sträng genom att ta värdet för e-postadressen som läggs till i skapandedatumet mellan parenteser (för strängtypen sätter du konstanten inom citattecken).

Högnivåfunktioner har lagts till i uttrycken för att berika potentialen i detta språk.

Du kan komma åt listan över tillgängliga funktioner via valfri uttrycksredigerare i Adobe Campaign klientkonsol:

![](assets/d_ncs_integration_schema_function.png)

**Exempel**:

* **GetDate()**: returnerar aktuellt datum
* **Year(@created)**: returnerar året för datumet som finns i attributet &quot;created&quot;
* **GetEmailDomain(@email)**: returnerar domänen för e-postadressen

## Skapa en sträng via beräkningssträngen {#building-a-string-via-the-compute-string}

En **beräkningssträng** är ett XPath-uttryck som används för att konstruera en sträng som representerar en post i en tabell som är associerad med schemat. **Beräkningssträngen** används främst i det grafiska gränssnittet för att visa etiketten för en markerad post.

**Beräkningssträngen** definieras via elementet **`<compute-string>`** under huvudelementet i dataschemat. Ett uttr-attribut **innehåller ett XPath-uttryck för att beräkna visningen**.

**Exempel**: beräkningssträng för mottagartabellen.

```sql
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultatet av den beräknade strängen för en mottagare: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Om schemat inte innehåller en beräkningssträng fylls en beräkningssträng i som standard med värdena för schemats primärnyckel.


## Läs mer

Klicka på följande länkar om du vill veta mer:

* [Kom igång med scheman](about-schema-reference.md)
* [Databasmappning](database-mapping.md)
* [Länkhantering](database-links.md)
* [Nyckelhantering](database-keys.md)
* [Modell för kampanjdata](about-data-model.md)