---
product: campaign
title: Exempel på schemautgåvor
description: Exempel på schemautgåvor
feature: Schema Extension
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: b7ee70e0-89c6-4cd3-8116-2f073d4a2f2f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---


# Exempel på schemautgåvor{#examples-of-schemas-edition}

## Utöka en tabell {#extending-a-table}

Utöka **nms:mottagare** schemats mottagartabell, använd följande procedur:

1. Skapa tilläggsschemat (**cus:tillägg**) med följande data:

   ```
   <srcSchema mappingType="sql" name="extension" namespace="cus" xtkschema="xtk:srcSchema" extendedSchema="nms:recipient">  
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>  
   
     <element name="extension">    
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>      
   
       <attribute label="Loyalty code" name="fidelity" type="long"/>    
       <element name="location">      
         <attribute name="area" label="Purchasing zone" type="string" length="50" enum="area"/>    
       </element>  </element>  
   </srcSchema>
   ```

   I det här exemplet har ett indexerat fält (**återgivning**) läggs till och **plats** element (som redan fanns i **nms:mottagare** schema) kompletteras med ett numrerat fält (**area**).

   >[!IMPORTANT]
   >
   >Kom ihåg att lägga till **extendedSchema** för att referera till tilläggsschemat.

1. Kontrollera att det utökade schemat **nms:mottagare** och att ytterligare data finns:

   ```
   <schema dependingSchemas="cus:extension" mappingType="sql" name="recipient" namespace="nms" xtkschema="xtk:schema">
     ...
     <enumeration basetype="string" default="area1" name="area">    
       <value label="Zone 1" name="area1"/>    
       <value label="Zone 2" name="area2"/>  
     </enumeration>
     ...
     <element autopk="true" name="recipient" sqltable="NmsRecipient"> 
       <dbindex name="area">      
         <keyfield xpath="location/@area"/>    
       </dbindex>
   
       ...
       <attribute belongsTo="cus:extension" label="Loyalty code" name="fidelity" sqlname="iFidelity" type="long"/>
       <element name="location">
         ...
         <attribute enum="area" label="Purchasing zone" length="50" name="area" sqlname="sArea" type="string"/>
       </element>
       ...
     </element>
   </schema>
   ```

   SQL-skriptet som genereras från databasuppdateringsguiden är följande:

   ```
   ALTER TABLE NmsRecipient ADD iFidelity INTEGER;
   UPDATE NmsRecipient SET iFidelity = 0;
   ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET NOT NULL;ALTER TABLE NmsRecipient ALTER COLUMN iFidelity SET Default 0;
   ALTER TABLE NmsRecipient ADD sArea VARCHAR(50); 
   CREATE INDEX NmsRecipient_area ON NmsRecipient(sArea);
   ```

## Länkad samlingstabell {#linked-collection-table}

I det här avsnittet beskrivs hur du skapar en ordertabell som är länkad till mottagartabellen med kardinaliteten 1-N.

Källschema för orderregister:

```
<srcSchema label="Order" name="order" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="order">    
    <compute-string expr="@number" + '(' + ToString(@date) + ')'/>    
    
    <attribute label="Number" length="128" name="number" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" type="datetime" default="GetDate()"/>    
    <attribute desc="order total" label="Total" name="total" type="double"/>    
    <element label="Recipient" name="recipient" revDesc="Orders associated with this recipient" revIntegrity="own" revLabel="Orders" target="nms:recipient" type="link"/>  
  </element>
</srcSchema>
```

Tabelltypen är **autopk** för att skapa en autogenererad primärnyckel som ska användas för kopplingen av länken till mottagartabellen.

Schema som genererats:

```
<schema label="Order" mappingType="sql" name="order" namespace="cus" xtkschema="xtk:schema">  
  <element autopk="true" label="Order" name="order" sqltable="CusOrder">    
    <compute-string expr="ToString(@date) + ' - ' + @number"/>    

    <dbindex name="id" unique="true">      
      <keyfield xpath="@id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>    

    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iOrderId" type="long"/>    
    <attribute label="Number" length="128" name="number" sqlname="sNumber" type="string"/>    
    <attribute desc="Order date" label="Date" name="date" sqlname="tsDate" type="datetime"/>    
    <attribute desc="order total" label="Total" name="total" sqlname="Total" type="double"/>    
    <element label="Recipient" name="recipient" revLink="order" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>  
   </element>
</schema>
```

SQL-skriptet för att skapa tabeller är följande:

```
CREATE TABLE CusOrder(dTotal DOUBLE PRECISION NOT NULL Default 0, iOrderId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, sNumber VARCHAR(128), tsDate TIMESTAMP Default NULL);
CREATE UNIQUE INDEX CusOrder_id ON CusOrder(iOrderId);
CREATE INDEX CusOrder_recipientId ON CusOrder(iRecipientId);  
INSERT INTO CusOrder (iOrderId) VALUES (0); 
```

>[!NOTE]
>
>Med SQL-kommandot INSERT INTO i slutet av skriptet kan du infoga en identifierarpost med värdet 0 för att simulera yttre kopplingar.

## Tilläggstabell {#extension-table}

Med en tilläggstabell kan du utöka innehållet i en befintlig tabell i en länkad kardinalitetstabell 1-1.

Syftet med en tilläggstabell är att undvika begränsningar av antalet fält som stöds i en tabell eller att optimera utrymmet som upptas av data, som förbrukas på begäran.

Skapar tilläggsschemat (**cus:funktion**):

```
<srcSchema mappingType="sql" name="feature" namespace="cus" xtkschema="xtk:srcSchema">  
  <element autopk="true" name="feature">    
    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
  </element>
</srcSchema>
```

Skapar ett tilläggsschema i mottagartabellen för att lägga till länken kardinalitet 1-1:

```
<srcSchema extendedSchema="nms:recipient" label="Recipient" mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="recipient">    
    <element desc="Features" integrity="own" label="Features" name="feature" revCardinality="single" revLink="recipient" target="cus:feature" type="link"/> 
  </element>
</srcSchema>
```

>[!NOTE]
>
>Definitionen av länken mellan mottagartabellen och tilläggstabellen måste fyllas i från schemat som innehåller sekundärnyckeln.

SQL-skriptet för att skapa tilläggstabellen är följande:

```
CREATE TABLE CusFeature(  iChildren NUMERIC(3) NOT NULL Default 0, iFeatureId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusFeature_id ON CusFeature(iFeatureId);  
INSERT INTO CusFeature (iFeatureId) VALUES (0); 
```

SQL-uppdateringsskriptet för mottagartabellen är följande:

```
ALTER TABLE NmsRecipient ADD iFeatureId INTEGER;
UPDATE NmsRecipient SET iFeatureId = 0;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET NOT NULL;
ALTER TABLE NmsRecipient ALTER COLUMN iFeatureId SET Default 0;
CREATE INDEX NmsRecipient_featureId ON NmsRecipient(iFeatureId);
```

## Överflödestabell {#overflow-table}

En flödestabell är en tilläggstabell (kardinalitet 1-1), men deklarationen av länken till tabellen som ska utökas fylls i schemat för flödestabellen.

Flödestabellen innehåller sekundärnyckeln till tabellen som ska utökas. Den tabell som ska utökas ändras därför inte. Relationen mellan de två tabellerna är värdet på primärnyckeln för den tabell som ska utökas.

Skapar schemat för flödestabell (**cus:spill**):

```
<srcSchema label="Overflow" name="overflow" namespace="cus" xtkschema="xtk:srcSchema">  
  <element name="overflow">    
    <key internal="true" name="id">      
      <keyfield xlink="recipient"/>    
    </key>    

    <attribute label="Children" name="children" type="byte"/>    
    <attribute label="Single" name="single" type="boolean"/>    
    <attribute label="Spouse first name" length="100" name="spouseFirstName" type="string"/>  
    <element label="Customer" name="recipient" revCardinality="single" revIntegrity="own" revExternalJoin="true" target="nms:recipient" type="link"/>  
  </element>  
</srcSchema>
```

>[!NOTE]
>
>Huvudnyckeln i flödestabellen är länken till tabellen som ska utökas (&quot;nms:mottagare&quot;-schema i vårt exempel).

SQL-skriptet för att skapa tabeller är följande:

```
CREATE TABLE CusOverflow(iChildren NUMERIC(3) NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0, iSingle NUMERIC(3) NOT NULL Default 0, sSpouseFirstName VARCHAR(100));
CREATE UNIQUE INDEX CusOverflow2_id ON CusOverflow2(iRecipientId);  
```

## Relationstabell {#relationship-table}

Med en relationstabell kan du länka två tabeller med kardinaliteten N-N. Tabellen innehåller bara sekundärnycklarna för de tabeller som ska länkas.

Exempel på en relationstabell mellan grupper (**nms:grupp**) och mottagare (**nms:mottagare**).

Relationstabellens källschema:

```
<srcSchema name="rcpGrpRel" namespace="cus">
  <element name="rcpGrpRel">
    <key internal="true" name="id">      
      <keyfield xlink="rcpGroup"/>      
      <keyfield xlink="recipient"/>    
    </key>

    <element integrity="neutral" label="Recipient" name="recipient" revDesc="Groups to which this recipient belongs" revIntegrity="own" revLabel="Groups" target="nms:recipient" type="link"/>    
    <element integrity="neutral" label="Group" name="rcpGroup" revDesc="Recipients in the group" revIntegrity="own" revLabel="Recipients" revLink="rcpGrpRel" target="nms:group" type="link"/>
  </element>
</srcSchema>
```

Det genererade schemat är följande:

```
<schema mappingType="sql" name="rcpGrpRel" namespace="cus" xtkschema="xtk:schema">  
  <element name="rcpGrpRel" sqltable="CusRcpGrpRel">    
    <compute-string expr="ToString([@rcpGroup-id]) + ',' + ToString([@recipient-id])"/>    
    <dbindex name="id" unique="true">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <key internal="true" name="id">      
      <keyfield xpath="@rcpGroup-id"/>      
      <keyfield xpath="@recipient-id"/>    
    </key>    

    <dbindex name="rcpGroupId">      
      <keyfield xpath="@rcpGroup-id"/>    
    </dbindex>    
    <dbindex name="recipientId">      
      <keyfield xpath="@recipient-id"/>    
    </dbindex>    

    <element integrity="neutral" label="Recipient" name="recipient" revLink="rcpGrpRel" target="nms:recipient" type="link">      
      <join xpath-dst="@id" xpath-src="@recipient-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Recipient' link ('id' field)" name="recipient-id" sqlname="iRecipientId" type="long"/>    

    <element integrity="neutral" label="Group" name="rcpGroup" revLink="rcpGrpRel" target="nms:group" type="link">      
      <join xpath-dst="@id" xpath-src="@rcpGroup-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Group' link ('id' field)" name="rcpGroup-id" sqlname="iRcpGroupId" type="long"/>  
  </element>
</schema>
```

SQL-skriptet för att skapa tabeller är följande:

```
CREATE TABLE CusRcpGrpRel( iRcpGroupId INTEGER NOT NULL Default 0, iRecipientId INTEGER NOT NULL Default 0);
CREATE UNIQUE INDEX CusRcpGrpRel_id ON CusRcpGrpRel(iRcpGroupId, iRecipientId);
CREATE INDEX CusRcpGrpRel_recipientId ON CusRcpGrpRel(iRecipientId);
```

## Använd skiftläge: länka ett fält till en befintlig referenstabell {#uc-link}

I det här exemplet visas hur du kan använda en befintlig referenstabell som ett alternativ till inbyggda uppräkningsmekanismer för Adobe Campaign (enum, userEnum eller dbEnum).

Du kan också använda en befintlig referenstabell som uppräkning i dina scheman. Detta kan du göra genom att skapa en länk mellan en tabell och referenstabellen, och genom att lägga till attributet **displayAsField=&quot;true&quot;**.

I det här exemplet innehåller referenstabellen en lista med banknamn och identifierare:

```
<srcSchema entitySchema="xtk:srcSchema" img="cus:bank16x16.png" label="Bank" mappingType="sql" name="bank" namespace="cus"
xtkschema="xtk:srcSchema">
    <element img="cus:bank16x16.png" label="Banks" name="bank">
        <compute-string expr="@name"/>
        <key name="id">
            <keyfield xpath="@id"/>
        </key>
        <attribute label="Bank Id" name="id" type="short"/>
        <attribute label="Name" length="64" name="name" type="string"/>
     </element> 
</srcSchema>
```

Definiera en länk och lägg till **displayAsField=&quot;true&quot;** -attribut.

```
<element displayAsField="true" label="Bank" name="bank" target="cus:bank" type="link" noDbIndex="true"/>
```

Användargränssnittet visar inte en länk utan ett fält. När användarna väljer det fältet kan de välja ett värde i referenstabellen eller använda funktionen Komplettera automatiskt.

![](assets/schema-edition-ex.png)

* För att den ska kunna slutföras automatiskt måste du definiera en beräkningssträng i referenstabellen.

* Lägg till **noDbIndex=&quot;true&quot;** i länkdefinitionen för att förhindra att Adobe Campaign skapar ett index för de värden som lagras i länkens källtabell.

## Relaterade ämnen

* [Arbeta med uppräkningar](../../platform/using/managing-enumerations.md)

* [Kom igång med kampanjscheman](../../configuration/using/about-schema-edition.md)

* [Uppdatera databasstrukturen](../../configuration/using/updating-the-database-structure.md)
