---
title: Databasmappning
seo-title: Databasmappning
description: Databasmappning
seo-description: null
page-status-flag: never-activated
uuid: a51df3eb-cae6-4e8d-8386-d62defc1b610
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: bc06c00d-f421-452e-bde0-b4ecc12c72c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Databasmappning{#database-mapping}

SQL-mappningen i vårt exempelschema ger följande XML-dokument:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## Beskrivning {#description}

Schemats rotelement är inte längre **`<srcschema>`** utan **`<schema>`**.

Detta tar oss till en annan typ av dokument, som genereras automatiskt från källschemat, som helt enkelt kallas schema. Det här schemat kommer att användas av Adobe Campaign-programmet.

SQL-namnen bestäms automatiskt utifrån elementnamn och typ.

Namnreglerna för SQL är följande:

* tabell: sammanfogning av schemanamnrymden och namnet

   I det här exemplet anges namnet på tabellen via huvudelementet i schemat i **sqltable** -attributet:

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* fält: namnet på elementet föregås av ett prefix som definierats enligt typ (&#39;i&#39; för heltal, &#39;d&#39; för double, &#39;s&#39; för sträng, &#39;ts&#39; för datum, osv.)

   Fältnamnet anges via attributet **sqlname** för varje typ **`<attribute>`** och **`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL-namn kan överladdas från källschemat. Det gör du genom att fylla i attributen &quot;sqltable&quot; eller &quot;sqlname&quot; för det berörda elementet.

SQL-skriptet som skapar tabellen som genereras från det utökade schemat är följande:

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL-fältbegränsningarna är följande:

* inga null-värden i numeriska fält och datumfält,
* numeriska fält initieras till 0.

## XML-fält {#xml-fields}

Som standard mappas alla typer **`<attribute>`** och **`<element>`** element till ett SQL-fält i datarapporten. Du kan emellertid referera till det här fältet i XML i stället för SQL, vilket betyder att data lagras i ett PM-fält (&quot;mData&quot;) i tabellen som innehåller värdena för alla XML-fält. Lagringen av dessa data är ett XML-dokument som observerar schemastrukturen.

Om du vill fylla i ett fält i XML måste du lägga till **xml** -attributet med värdet &quot;true&quot; till det aktuella elementet.

**Exempel**: Här är två exempel på hur XML-fält används.

* Flerradskommentarfält:

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* Beskrivning av data i HTML-format:

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   Med typen html kan du lagra HTML-innehållet i en CDATA-tagg och visa en speciell HTML-redigeringskontroll i Adobe Campaign-klientgränssnittet.

Med hjälp av XML-fält kan du lägga till fält utan att behöva ändra databasens fysiska struktur. En annan fördel är att du använder mindre resurser (storlek som tilldelas SQL-fält, gräns för antalet fält per tabell osv.).

Den största nackdelen är att det är omöjligt att indexera eller filtrera ett XML-fält.

## Indexerade fält {#indexed-fields}

Med index kan du optimera prestanda för de SQL-frågor som används i programmet.

Ett index deklareras från huvudelementet i dataschemat.

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indexen följer följande regler:

* Ett index kan referera till ett eller flera fält i tabellen.
* Ett index kan vara unikt (för att undvika dubbletter) i alla fält om det **unika** attributet innehåller värdet &quot;true&quot;.
* Indexets SQL-namn bestäms av tabellens SQL-namn och indexets namn.

>[!NOTE]
>
>Som standard är index de första elementen som deklareras från schemats huvudelement.

>[!NOTE]
>
>Index skapas automatiskt vid tabellmappning (standard eller FDA).

**Exempel**:

* Lägga till ett index till e-postadressen och staden:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* Lägga till ett unikt index i namnfältet&quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="id" unique="true">
         <keyfield xpath="@id"/> 
       </dbindex>
   
       <dbindex name="email">
         <keyfield xpath="@email"/> 
       </dbindex>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## Nyckelhantering {#management-of-keys}

En tabell måste ha minst en nyckel för att identifiera en post i tabellen.

En nyckel deklareras från huvudelementet i dataschemat.

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Tangenter följer följande regler:

* En nyckel kan referera till ett eller flera fält i tabellen.
* En nyckel kallas&quot;primär&quot; (eller&quot;prioritet&quot;) när den är den första i schemat som ska fyllas i eller om den innehåller attributet **internal** med värdet &quot;true&quot;.
* Ett unikt index deklareras implicit för varje nyckeldefinition. Det går inte att skapa ett index för nyckeln genom att lägga till attributet **noDbIndex** med värdet &quot;true&quot;.

>[!NOTE]
>
>Som standard är nycklar de element som deklarerats från huvudelementet i schemat efter att index har definierats.

>[!NOTE]
>
>Tangenter skapas vid tabellmappning (standard eller FDA). Adobe Campaign hittar unika index.

**Exempel**:

* Lägga till en nyckel till e-postadressen och staden:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

   Schemat som genererats:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
      <dbindex name="email" unique="true">      
        <keyfield xpath="@email"/>      
        <keyfield xpath="location/@city"/>    
      </dbindex>    
   
      <key name="email">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
      </key>    
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* Lägga till en primär eller intern nyckel i namnfältet&quot;id&quot;:

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="id" internal="true">
         <keyfield xpath="@id"/> 
       </key>
   
       <key name="email" noDbIndex="true">
         <keyfield xpath="@email"/> 
       </key>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

   Schemat som genererats:

   ```
   <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
     <element name="recipient" sqltable="CusRecipient">    
       <key name="email">      
         <keyfield xpath="@email"/>    
       </key>    
   
       <dbindex name="id" unique="true">      
         <keyfield xpath="@id"/>    
       </dbindex>    
   
       <key internal="true" name="id">      
        <keyfield xpath="@id"/>    
       </key>    
   
       <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### Automatisk inkrementell nyckel {#auto-incremental-key}

Huvudnyckeln i de flesta Adobe Campaign-tabeller är ett 32-bitars långt heltal som genereras automatiskt av databasmotorn. Beräkningen av nyckelvärdet beror på en sekvens (som standard SQL-funktionen **XtkNewId** ) som genererar ett tal som är unikt i hela databasen. Innehållet i nyckeln anges automatiskt när posten infogas.

Fördelen med en inkrementell nyckel är att den ger en icke-modifierbar teknisk nyckel för kopplingarna mellan tabellerna. Dessutom tar den här nyckeln inte upp så mycket minne eftersom ett heltal med dubbla byte används.

I källschemat kan du ange namnet på den sekvens som ska användas med **pkSequence** -attributet. Om det här attributet inte anges i källschemat används **XtkNewId** -standardsekvensen. Programmet använder dedikerade sekvenser för schemana **nms:broadLog** och **nms:trackingLog** (**NmsBroadLogId** respektive **NmsTrackingLogId** ) eftersom det här är de register som innehåller de flesta poster.

Från ACC 18.10 är **XtkNewId** inte längre standardvärdet för sekvensen i de körklara scheman. Du kan nu skapa ett schema eller utöka ett befintligt schema med en dedikerad sekvens.

>[!IMPORTANT]
>
>När du skapar ett nytt schema eller under ett schematillägg måste du behålla samma sekvensvärde för primärnyckeln (@pkSequence) för hela schemat.

>[!NOTE]
>
>En sekvens som refereras i ett Adobe Campaign-schema (till exempel **NmsTrackingLogId** ) måste associeras med en SQL-funktion som returnerar antalet ID:n i parametrarna, avgränsade med kommatecken. Den här funktionen måste kallas ******GetNewXXXIds**, där **XXX** är sekvensens namn (till exempel **GetNewNmsTrackingLogIds** ). Visa **postgres-nms.sql**-, **mssql-nms.sql** - eller **oracle-nms.sql** -filer som ingår i programmet i **datakit/nms/eng/sql/** -katalogen för att återställa exemplet på att skapa en NmsTrackingLogId-sekvens för varje databasmotor.

Om du vill deklarera en unik nyckel fyller du i **autopk** -attributet (med värdet &quot;true&quot;) i dataschemats huvudelement.

**Exempel**:

Deklarera en inkrementell nyckel i källschemat:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Schemat som genererats:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

Förutom definitionen av nyckeln och dess index har ett numeriskt fält med namnet&quot;id&quot; lagts till i det utökade schemat för att innehålla den automatiskt genererade primärnyckeln.

>[!IMPORTANT]
>
>När tabellen skapas infogas automatiskt en post med primärnyckeln 0. Den här posten används för att undvika yttre kopplingar, som inte gäller för volymtabeller. Som standard initieras alla sekundärnycklar med värdet 0 så att ett resultat alltid kan returneras vid kopplingen när dataobjektet inte fylls i.

## Länkar: relation mellan tabeller {#links--relation-between-tables}

En länk beskriver kopplingen mellan en tabell och en annan.

De olika sammanslutningarna (så kallade kardinaliteter) är följande:

* Kardinalitet 1-1: en förekomst av källtabellen kan ha högst en motsvarande förekomst av måltabellen.
* Kardinalitet 1-N: en förekomst av källtabellen kan ha flera motsvarande förekomster av måltabellen, men en förekomst av måltabellen kan ha högst en motsvarande förekomst av källtabellen.
* Kardinalitet N-N: en förekomst av källtabellen kan ha flera motsvarande förekomster av måltabellen och vice versa.

I gränssnittet kan du enkelt skilja mellan olika typer av relationer tack vare deras ikoner.

För anslutningsrelationer med en campingtabell/databas:

* ![](assets/join_with_campaign11.png) : Kardinalitet 1-1. Till exempel mellan en mottagare och en aktuell order. En mottagare kan bara vara relaterad till en förekomst av den aktuella ordertabellen åt gången.
* ![](assets/externaljoin11.png) : Kardinalitet 1-1, extern koppling. Till exempel mellan en mottagare och deras land. En mottagare kan bara vara relaterad till en förekomst av registerlandet. Innehållet i landstabellen sparas inte.
* ![](assets/join_with_campaign1n.png) : Kardinalitet 1-N. Till exempel mellan en mottagare och prenumerationstabellen. En mottagare kan vara relaterad till flera förekomster i prenumerationstabellen.

För anslutningsrelationer med Federated Database Access:

* ![](assets/join_fda_11.png) : Kardinalitet 1-1
* ![](assets/join_fda_1m.png) : Kardinalitet 1-N

Mer information om FDA-tabeller finns i [Åtkomst till en extern databas](../../platform/using/about-fda.md).

En länk måste deklareras i schemat som innehåller sekundärnyckeln för tabellen som är länkad via huvudelementet:

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

Länkarna följer följande regler:

* Definitionen av en länk anges på en **länktyp****`<element>`** med följande attribut:

   * **namn**: Namnet på länken från källtabellen.
   * **mål**: målschemats namn,
   * **label**: länketikett,
   * **revLink** (valfritt): Namn på omvänd länk från målschemat (dras automatiskt som standard).
   * **integritet** (valfritt): referensintegritet för källtabellens förekomst till måltabellens förekomst. Möjliga värden är följande:

      * **definiera**: det är möjligt att ta bort källförekomsten om den inte längre refereras av en målförekomst,
      * **normal**: Om du tar bort källförekomsten initieras nycklarna för länken till målförekomsten (standardläge), initierar den här typen av integritet alla sekundärnycklar.
      * **egen**: Om du tar bort källförekomsten tas målförekomsten bort.
      * **owncopy**: samma som **eget** (vid borttagning) eller dubblerar förekomsterna (vid duplicering),
      * **neutral**: gör ingenting.
   * **revIntegrity** (valfritt): integritet i målschemat (valfritt, &quot;normal&quot; som standard),
   * **revCardinality** (valfritt): med värdet &quot;single&quot; fylls kardinaliteten med typ 1-1 (1-N som standard).
   * **externalJoin** (valfritt): tvingar det yttre hörnet
   * **revExternalJoin** (valfritt): tvingar det yttre hörnet på den omvända länken


* En länk refererar till ett eller flera fält från källtabellen till måltabellen. Fälten som utgör sammanfogningen ( `<join>` elementet) behöver inte fyllas i eftersom de automatiskt dras av som standard med målschemats interna nyckel.
* Ett index läggs automatiskt till i länkens sekundärnyckel i det utökade schemat.
* En länk består av två halvlänkar, där den första deklareras från källschemat och den andra skapas automatiskt i målschemats utökade schema.
* En join kan vara en yttre join om attributet **externalJoin** läggs till, med värdet &quot;true&quot; (stöds i PostgreSQL).

>[!NOTE]
>
>Som standard är länkar de element som deklarerats i slutet av schemat.

### Exempel 1 {#example-1}

1-N-relation till schematabellen&quot;cus:company&quot;:

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Schemat som genererats:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

Länkdefinitionen kompletteras av fälten som utgör kopplingen, dvs. primärnyckeln med XPath (&quot;@id&quot;) i målschemat och sekundärnyckeln med XPath (&quot;@company-id&quot;) i schemat.

Sekundärnyckeln läggs automatiskt till i ett element som använder samma egenskaper som det associerade fältet i måltabellen, med följande namnkonvention: målschemats namn följt av namnet på det associerade fältet (&quot;företag-id&quot; i vårt exempel).

Utökat schema för målet (&quot;cus:company&quot;):

```
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

En omvänd länk till tabellen&quot;cus:mottagare&quot; lades till med följande parametrar:

* **namn**: dras automatiskt från källschemats namn (kan framtvingas med attributet &quot;revLink&quot; i länkdefinitionen i källschemat)
* **revLink**: namn på omvänd länk
* **mål**: nyckel för länkat schema (&quot;cus:mottagare&quot;-schema)
* **obunden**: länken deklareras som ett samlingselement för en 1-N-kardinalitet (som standard)
* **integritet**: &quot;define&quot; som standard (kan framtvingas med attributet &quot;revIntegrity&quot; i länkdefinitionen i källschemat).

### Exempel 2 {#example-2}

I det här exemplet deklarerar vi en länk till schematabellen &quot;nms:address&quot;. Kopplingen är en yttre koppling och fylls i explicit med mottagarens e-postadress och fältet &quot;@address&quot; i den länkade tabellen (&quot;nms:address&quot;).

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### Exempel 3 {#example-3}

1-1 relation till schematabellen &quot;cus:extension&quot;:

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Exempel 4 {#example-4}

Länka till en mapp (&quot;xtk:folder&quot;-schema):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Standardvärdet returnerar identifieraren för den första giltiga parametertypfilen som anges i funktionen &quot;DefaultFolder(&#39;nmsFolder&#39;)&quot;.

### Exempel 5 {#example-5}

I det här exemplet vill vi skapa en nyckel för en länk (&quot;företag&quot; till&quot;cus:company&quot;-schema) med **xlink** -attributet och ett fält i tabellen (&quot;e-post&quot;):

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

Schemat som genererats:

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

Definitionen av namnnyckeln&quot;companyEmail&quot; utökades med sekundärnyckeln för länken&quot;company&quot;. Den här nyckeln genererar ett unikt index för båda fälten.
