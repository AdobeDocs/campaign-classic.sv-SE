---
product: campaign
title: Schemaegenskaper
description: Schemaegenskaper
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# Schemaegenskaper{#schema-characteristics}



Egenskaperna för ett schema som refererar till en befintlig tabell är följande:

* Adobe Campaign får inte ändra SQL-objekt i förhållande till befintliga tabeller.
* Namnen på tabeller och kolumner måste anges explicit.
* Index måste deklareras.

>[!IMPORTANT]
>
>Ta inte bort fält i den inbyggda mottagartabellen, även om de är värdelösa. Detta kan orsaka beteendefel i Adobe Campaign-databasen.

## Attributet view {#the-view-attribute}

Källscheman accepterar **visa** attribut för **srcSchema** rotelement. Den måste användas när Adobe Campaign hanteras i anpassade tabeller. The **view=&quot;true&quot;** -attributet instruerar databasstrukturuppdateringsguiden att ignorera det här schemat. Programmet tillåts därför inte att synkronisera tabellen, dess kolumner och index med motsvarande schema.

När det här attributet är inställt på **true** används schemat bara för att generera SQL-frågor för att komma åt data i den här tabellen.

## Namn på tabeller och kolumner {#names-of-tables-and-columns}

När tabeller skapas med tabelluppdateringsguiden genereras namnen på tabeller och kolumner automatiskt baserat på namnen på respektive schema och attribut. Du kan dock tvinga SQL-namnen att användas genom att ange följande attribut:

* **sqltable** i schemats huvudelement för att specificera tabellen,
* **sqlname** för att ange kolumnerna i varje attribut.

**Exempel**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

I det här exemplet skulle programmet ha använt om namnen på tabellerna och kolumnerna inte hade angetts explicit **CusIndividual** för tabellen, **lastName** och **firstName** för kolumnerna.

I ett schema går det bara att fylla en del av kolumnerna i en befintlig tabell. Ej ifyllda kolumner är inte tillgängliga för användaren.

## Indexerade fält {#indexed-fields}

När du sorterar poster i en lista från klientkonsolen får du bättre prestanda genom att sortera efter indexerade fält. När ett index deklareras i ett schema visas de indexerade fälten med en röd linje under sorteringsordningen till vänster om kolumnetiketten, vilket visas nedan:

![](assets/s_ncs_integration_mapping_index.png)

I ett schema definieras ett index på följande sätt:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

Därför är det viktigt att deklarera befintliga index för den anpassade tabellen i det matchande schemat.

Ett index deklareras implicit för varje nyckel- och länkdeklaration i källschemat. Indexdeklarationen kan förhindras genom att ange **noDbIndex=&quot;true&quot;** attribute:

**Exempel**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
