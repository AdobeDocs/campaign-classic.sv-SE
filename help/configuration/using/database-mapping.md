---
product: campaign
title: Databasmappning
description: Databasmappning
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 4a29c189e1e438bbb90067ece63ced0196c618ec
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 4%

---

# Databasmappning{#database-mapping}

SQL-mappningen för exempelschemat som beskrivs [på den här sidan](schema-structure.md) genererar följande XML-dokument:

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

Rotelementet i schemat har ändrats till **`<srcschema>`** till **`<schema>`**.

Den andra typen av dokument genereras automatiskt från källschemat och kallas helt enkelt för schema.

SQL-namnen bestäms automatiskt utifrån elementnamn och typ.

Namnreglerna för SQL är följande:

* **table**: sammanfogning av schemanamnrymden och namnet

  I det här exemplet anges namnet på tabellen via huvudelementet i schemat i **sqltable** attribute:

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **fält**: elementets namn föregås av ett prefix som definierats enligt typ: &#39;i&#39; för heltal, &#39;d&#39; för double, &#39;s&#39; för sträng, &#39;ts&#39; för datum, osv.

  Fältnamnet anges via **sqlname** attribut för varje typ **`<attribute>`** och **`<element>`**:

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>SQL-namn kan överladdas från källschemat. Det gör du genom att fylla i attributen &quot;sqltable&quot; eller &quot;sqlname&quot; för det berörda elementet.

SQL-skriptet som skapar tabellen som genereras från det utökade schemat är följande:

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL-fältbegränsningarna är följande:

* inga null-värden i numeriska fält och datumfält
* numeriska fält initieras till 0

## XML-fält {#xml-fields}

Som standard är alla  **`<attribute>`** och **`<element>`** -typed-element mappas till ett SQL-fält i databchematabellen. Du kan emellertid referera till det här fältet i XML i stället för SQL, vilket betyder att data lagras i ett PM-fält (&quot;mData&quot;) i tabellen som innehåller värdena för alla XML-fält. Lagringen av dessa data är ett XML-dokument som observerar schemastrukturen.

Om du vill fylla i ett fält i XML måste du lägga till **xml** ett attribut med värdet &quot;true&quot; för det berörda elementet.

**Exempel**: här är två exempel på hur XML-fält används.

* Flerradskommentarfält:

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* Databeskrivning i HTML-format:

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  Med typen html kan du lagra HTML-innehåll i en CDATA-tagg och visa en speciell HTML edit check i Adobe Campaign klientgränssnitt.

Använd XML-fält för att lägga till nya fält utan att ändra databasens fysiska struktur. En annan fördel är att du använder mindre resurser (storlek som tilldelas SQL-fält, gräns för antalet fält per tabell osv.). Observera dock att du inte kan indexera eller filtrera ett XML-fält.

## Indexerade fält {#indexed-fields}

Med index kan du optimera prestanda för de SQL-frågor som används i programmet.

Ett index deklareras från huvudelementet i dataschemat.

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

Indexen följer följande regler:

* Ett index kan referera till ett eller flera fält i tabellen
* Ett index kan vara unikt (för att undvika dubbletter) i alla fält om **unik** -attributet innehåller värdet &quot;true&quot;
* Indexets SQL-namn bestäms av tabellens SQL-namn och indexets namn

>[!NOTE]
>
>* Som standard är index de första elementen som deklareras från schemats huvudelement.
>
>* Index skapas automatiskt vid tabellmappning (standard eller FDA).

**Exempel**:

* Lägga till ett index till e-postadressen och staden:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* Lägga till ett unikt index i namnfältet&quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## Läs mer

Klicka på följande länkar om du vill veta mer:

* [Kom igång med scheman](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Nyckelhantering](database-keys.md)
* [Länkhantering](database-links.md)
* [Kampanjdatamodell](about-data-model.md)