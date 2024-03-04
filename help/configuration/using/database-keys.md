---
product: campaign
title: Nyckelhantering i datamodeller
description: Förstå nyckelhantering i datamodeller
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
source-git-commit: 46220dcfdddb8f6f1e7026cafc503aaeecb7e0fa
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 2%

---


# Nyckelhantering i scheman {#management-of-keys}

Varje tabell som är associerad med ett dataschema måste ha minst en nyckel för att identifiera en post i en tabell.

En nyckel deklareras från huvudelementet i dataschemat.

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

En nyckel kallas för &#39;primärnyckel&#39; när den är den första i schemat som ska fyllas i, eller om den innehåller `internal` -attributet har värdet &quot;true&quot;.


Följande regler gäller för nycklar:

* En nyckel kan referera till ett eller flera fält i tabellen
* Ett unikt index deklareras implicit för varje nyckeldefinition. Det går inte att skapa ett index på nyckeln genom att ange `noDbIndex` -attributet är &quot;true&quot;.

>[!NOTE]
>
>* Som standard är nycklar de element som deklarerats från huvudelementet i schemat efter att index har definierats.
>
>* Tangenter skapas vid tabellmappning (standard eller FDA). Adobe Campaign hittar unika index.

**Exempel**:

* Lägga till en nyckel till e-postadressen och staden:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  Schemat som genererats:

  ```sql
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
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* Lägga till en primär eller intern nyckel i namnfältet&quot;id&quot;:

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  Schemat som genererats:

  ```sql
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
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## Automatisk inkrementell nyckel {#auto-incremental-key}

Huvudnyckeln i de flesta Adobe Campaign-tabeller är ett 32-bitars heltal som genereras automatiskt av databasmotorn. Beräkningen av nyckelvärdet beror på en sekvens (som standard är **XtkNewId** SQL-funktion) som genererar ett tal som är unikt i hela databasen. Innehållet i nyckeln anges automatiskt när posten infogas.

Fördelen med en inkrementell nyckel är att den ger en icke-modifierbar teknisk nyckel för kopplingarna mellan tabellerna. Dessutom tar den här nyckeln inte upp så mycket minne eftersom ett heltal med dubbla byte används.

I källschemat kan du ange namnet på den sekvens som ska användas med **pkSequence** -attribut. Om attributet inte anges i källschemat **XtkNewId** standardsekvens används. Programmet använder dedikerade sekvenser för **nms:broadLog** och **nms:trackingLog** scheman (**NmsBroadLogId** och **NmsTrackingLogId** eftersom dessa är de tabeller som innehåller flest poster.

Från ACC 18.10, **XtkNewId** är inte längre standardvärdet för sekvensen i scheman som är klara att användas. Du kan nu skapa ett schema eller utöka ett befintligt schema med en dedikerad sekvens.

>[!IMPORTANT]
>
>När du skapar ett nytt schema eller under ett schematillägg måste du behålla samma sekvensvärde för primärnyckeln (@pkSequence) för hela schemat.

En sekvens som refereras i ett Adobe Campaign-schema (**NmsTrackingLogId** t.ex.) måste associeras med en SQL-funktion som returnerar antalet ID:n i parametrarna, avgränsade med kommatecken. Den här funktionen måste anropas **GetNew** XXX **ID**, där **XXX** är namnet på sekvensen (**GetNewNmsTrackingLogIds** till exempel). Visa **postgres-nms.sql**, **mssql-nms.sql** eller **oracle-nms.sql** filer som ingår i programmet i **datakit/nms/eng/sql/** för att återställa exemplet på en NmsTrackingLogId-sekvensgenerering för varje databasmotor.

Om du vill deklarera en unik nyckel fyller du i **autopk** attribute (with value &quot;true&quot;) on the main element of the data schema.

**Exempel**:

Deklarera en inkrementell nyckel i källschemat:

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

Schemat som genererats:

```sql
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


## Läs mer

Klicka på följande länkar om du vill veta mer:

* [Kom igång med scheman](about-schema-reference.md)
* [Schemastruktur](schema-structure.md)
* [Databasmappning](database-mapping.md)
* [Länkhantering](database-links.md)
* [Kampanjdatamodell](about-data-model.md)