---
title: Schemastruktur
seo-title: Schemastruktur
description: Schemastruktur
seo-description: null
page-status-flag: never-activated
uuid: 9be70907-6154-4890-91e8-fd0fac30ab05
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: b5c8faf7-d0ae-4d95-b7fe-6ef9674a33d2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Schemastruktur{#schema-structure}

Grundstrukturen för en `<srcschema>` bild är följande:

```
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

XML-dokumentet i ett dataschema måste innehålla **`<srcschema>`** rotelementet med attributen **name** och **namespace** för att schemanamnet och dess namnutrymme ska kunna fyllas i.

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

Låt oss använda följande XML-innehåll för att illustrera strukturen i ett dataschema:

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

Med motsvarande dataschema:

```
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

Med elementen **`<attribute>`** och **`<element>`** de som följer huvudelementet kan du definiera plats och namn för dataobjekten i XML-strukturen.

I vårt exempelschema är följande:

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

Följande regler måste följas:

* Varje **`<element>`** och **`<attribute>`** måste identifieras med namn via **name** -attributet.

   >[!IMPORTANT]
   >
   >Elementets namn ska vara kortfattat, helst på engelska, och endast innehålla tillåtna tecken i enlighet med XML-reglerna för namngivning.

* Endast **`<element>`** element kan innehålla **`<attribute>`** element och **`<element>`** element i XML-strukturen.
* Ett **`<attribute>`** element måste ha ett unikt namn i en **`<element>`**.
* Vi rekommenderar att du använder **`<elements>`** i flerradiga datasträngar.

## Datatyper {#data-types}

Datatypen anges via **type** -attributet i **`<attribute>`** elementen och **`<element>`** .

En detaljerad lista finns i beskrivningen av [`<attribute>` elementet](../../configuration/using/elements-and-attributes.md#attribute--element) och [`<element>` elementet](../../configuration/using/elements-and-attributes.md#element--element).

När det här attributet inte är ifyllt är **strängen** standarddatatyp om inte elementet innehåller underordnade element. Om den gör det används den bara för att strukturera elementen hierarkiskt (elementet i vårt exempel **`<location>`** ).

Följande datatyper stöds i scheman:

* **sträng**: teckensträng. Exempel: ett förnamn, en stad osv.

   Storleken kan anges via attributet **length** (valfritt, standardvärde &quot;255&quot;).

* **boolesk**: Booleskt fält. Exempel på möjliga värden: true/false, 0/1, yes/no, etc.
* **byte**, **short**, **long**: heltal (1 byte, 2 byte, 4 byte). Exempel: en ålder, ett kontonummer, ett antal poäng osv.
* **dubbel**: flyttal med dubbel precision. Exempel: ett pris, en kurs, osv.
* **date**, **datetime**: datum och datum + tider. Exempel: födelsedatum, inköpsdatum osv.
* **datetimenotz**: datum + tid utan tidszonsdata.
* **tidsintervall**: varaktighet. Exempel: tjänsteålder.
* **PM**: långa textfält (flera rader). Exempel: en beskrivning, en kommentar osv.
* **uuid**: &quot;uniqueidentifier&quot;-fält som stöder ett GUID (stöds endast i Microsoft SQL Server).

   >[!NOTE]
   >
   >Om du vill innehålla ett **uuid** -fält i andra motorer än Microsoft SQL Server måste funktionen &quot;newuid()&quot; läggas till och fyllas i med standardvärdet.

Här är vårt exempelschema med de angivna typerna:

```
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

Tabellen nedan visar mappningarna för de typer av data som genereras av Adobe Campaign för de olika databashanteringssystemen.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Sträng<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 (NVARCHAR2 om unicode används)<br /> </td> 
   <td> VARCHAR (VARCHAR CHARACTER SET UNICODE if Unicode)<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR (NVARCHAR if unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolean<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Byte<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Kort<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Dubbel<br /> </td> 
   <td> DUBBEL PRECISION<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DUBBELT<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Lång<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> NUMERIC(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> TIDSSTÄMPEL<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> Tid<br /> </td> 
   <td> TID<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> TID<br /> </td> 
   <td> TID<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> TIDSSTÄMPEL<br /> </td> 
   <td> TIDSSTÄMPEL<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATUM<br /> </td> 
   <td> TIDSSTÄMPEL<br /> </td> 
   <td> TIDSSTÄMPEL<br /> </td> 
   <td> MS SQL &lt; 2008: DATETIME<br /> MS SQL &gt;= 2012: DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Tidsintervall<br /> </td> 
   <td> DUBBEL PRECISION<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DUBBELT<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> PM<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB (NCLOB if Unicode)<br /> </td> 
   <td> CLOB (CLOB CHARACTER SET UNICODE if Unicode)<br /> </td> 
   <td> CLOB(6 MB)<br /> </td> 
   <td> TEXT (NTEXT om Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> BILD<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Egenskaper {#properties}

Elementen **`<elements>`** och **`<attributes>`** elementen i dataschemat kan berikas med olika egenskaper. Du kan fylla i en etikett för att beskriva det aktuella elementet.

### Etiketter och beskrivningar {#labels-and-descriptions}

* Med egenskapen **label** kan du ange en kort beskrivning.

   >[!NOTE]
   >
   >Etiketten är associerad med instansens aktuella språk.

   **Exempel**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   Etiketten visas i indataformuläret för Adobe Campaign-klientkonsolen:

   ![](assets/d_ncs_integration_schema_label.png)

* Med egenskapen **desc** kan du ange en lång beskrivning.

   Beskrivningen visas från indataformuläret i statusfältet i huvudfönstret i Adobe Campaign-klientkonsolen.

   >[!NOTE]
   >
   >Beskrivningen är associerad med instansens aktuella språk.

   **Exempel**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### Standardvärden {#default-values}

Med **standardegenskapen** kan du definiera ett uttryck som returnerar ett standardvärde när innehåll skapas.

Värdet måste vara ett uttryck som är kompatibelt med XPath-språket. Mer information finns i [Referera med XPath](../../configuration/using/schema-structure.md#referencing-with-xpath).

**Exempel**:

* Aktuellt datum: **default=&quot;GetDate()&quot;**
* Räknare: **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   I det här exemplet skapas standardvärdet med sammanfogningen av en sträng och anropet av funktionen **CounterValue** med ett fritt räknarnamn. Det returnerade talet ökas med ett steg vid varje infogning.

   >[!NOTE]
   >
   >I Adobe Campaign-klientkonsolen används noden för att hantera räknare **[!UICONTROL Administration>Counters]** .

Om du vill länka ett standardvärde till ett fält kan du använda `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` : gör att du kan fylla i fältet i förväg med ett standardvärde när du skapar enheter. Värdet kommer inte att vara ett standard-SQL-värde.

`<sqldefault>` : ger dig ett mervärde när du skapar ett fält. Värdet visas som ett SQL-resultat. Under en schemauppdatering påverkas bara de nya posterna av det här värdet.

### Uppräkningar {#enumerations}

#### Kostnadsfri uppräkning {#free-enumeration}

Med egenskapen **userEnum** kan du definiera en kostnadsfri uppräkning för att memorera och visa de värden som anges i det här fältet. Syntaxen är följande:

**userEnum=&quot;uppräkningens namn&quot;**

Det namn som anges för uppräkningen kan väljas fritt och delas med andra fält.

Dessa värden visas i en nedrullningsbar lista från indataformuläret:

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>I Adobe Campaign-klientkonsolen används noden för att hantera uppräkningar **[!UICONTROL Administration > Enumerations]** .

#### Ange uppräkning {#set-enumeration}

Med **enum** -egenskapen kan du definiera en fast uppräkning som används när listan med möjliga värden är känd i förväg.

Attributet **enum** refererar till definitionen av en uppräkningsklass som är ifylld i schemat utanför huvudelementet.

Uppräkningar gör att användaren kan välja ett värde i en nedrullningsbar lista i stället för att ange värdet i ett vanligt inmatningsfält:

![](assets/d_ncs_integration_schema_enum.png)

Exempel på en uppräkningsdeklaration i dataschemat:

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

En uppräkning deklareras utanför huvudelementet via **`<enumeration>`** elementet.

Uppräkningsegenskaperna är följande:

* **baseType**: Typ av data som är kopplade till värdena.
* **label**: beskrivning av uppräkningen,
* **namn**: Uppräkningens namn.
* **standard**: uppräkningens standardvärde.

Uppräkningsvärdena deklareras i **`<value>`** elementet med följande attribut:

* **namn**: Namnet på det internt lagrade värdet.
* **label**: etikett som visas via det grafiska gränssnittet.

#### dbenum-uppräkning {#dbenum-enumeration}

* Med egenskapen **dbenum** kan du definiera en uppräkning vars egenskaper liknar egenskaperna för egenskapen **enum** .

   Attributet **name** lagrar emellertid inte värdet internt, utan lagrar en kod som gör att du kan utöka de berörda tabellerna utan att ändra deras schema.

   Värdena definieras via **[!UICONTROL Administration>Enumerations]** noden.

   Den här uppräkningen används till exempel för att ange kampanjens karaktär.

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### Exempel {#example}

Här är vårt exempelschema med egenskaperna ifyllda:

```
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

Med det **obundna** attributet med värdet &quot;true&quot; kan du fylla i ett samlingselement.

**Exempel**: definition av samlingselementet **`<group>`** i schemat.

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

Med projektion av XML-innehållet:

```
<group label="Group1"/>
<group label="Group2"/>
```

## Referera med XPath {#referencing-with-xpath}

XPath-språket används i Adobe Campaign för att referera till ett element eller attribut som tillhör ett dataschema.

XPath är en syntax som gör att du kan hitta en nod i trädet i ett XML-dokument.

Elementen anges med sitt namn och attributen anges med namnet före tecknet&quot;@&quot;.

**Exempel**:

* **@email**: markerar e-postmeddelandet,
* **location/@city**: markerar attributet &quot;city&quot; under **`<location>`** elementet
* **../@email**: väljer e-postadressen från det överordnade elementet i det aktuella elementet
* **grupp`[1]/@label`**: väljer attributet &quot;label&quot; som är underordnat det första **`<group>`**mängdelementet
* **grupp`[@label='test1']`**: markerar attributet &quot;label&quot; som är underordnat elementet och innehåller värdet &quot;test1&quot;**`<group>`**

>[!NOTE]
>
>En ytterligare begränsning läggs till när banan korsar ett underelement. I det här fallet måste följande uttryck placeras inom hakparenteser:
>
>* **location/@city** is not valid; använd **`[location/@city]`**
>* **`[@email]`** och **@email** är likvärdiga
>



Det går också att definiera komplexa uttryck, till exempel följande aritmetiska operationer:

* **@kön+1**: lägger till 1 i innehållet i **könsattributet** ,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**: skapar en sträng genom att använda värdet för den e-postadress som lagts till i skapandedatumet mellan parenteser (för strängtypen anger du konstanten inom citattecken).

Funktioner på hög nivå har lagts till i uttrycken för att berika detta språks potential.

Du kommer åt listan över tillgängliga funktioner via en uttrycksredigerare i Adobe Campaign-klientkonsolen:

![](assets/d_ncs_integration_schema_function.png)

**Exempel**:

* **GetDate()**: returnerar aktuellt datum
* **År(@skapat)**: returnerar året för datumet som finns i attributet &quot;created&quot;.
* **GetEmailDomain(@email)**: returnerar e-postadressens domän.

## Bygga en sträng via beräkningssträngen {#building-a-string-via-the-compute-string}

En **beräkningssträng** är ett XPath-uttryck som används för att konstruera en sträng som representerar en post i en tabell som är associerad med schemat. **Beräkningssträngen** används huvudsakligen i det grafiska gränssnittet för att visa etiketten för en markerad post.

Beräkningssträngen **definieras via** **`<compute-string>`** elementet under huvudelementet i dataschemat. Ett **expr** -attribut innehåller ett XPath-uttryck för att beräkna visningen.

**Exempel**: beräkningssträng för mottagartabellen.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

Resultat av beräknad sträng för en mottagare: **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>Om schemat inte innehåller någon beräkningssträng fylls en beräkningssträng i som standard med värdena för schemats primärnyckel.

