---
title: Datamodeller
seo-title: Datamodeller
description: Datamodeller
seo-description: null
page-status-flag: never-activated
uuid: 9f08750a-e125-4531-8c2c-1ab218190210
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b65e8d27-f427-464e-ad42-51c0a88eee86
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Datamodeller{#data-schemas}

## Principer {#principles}

Om du vill redigera, skapa och konfigurera scheman klickar du på noden i Adobe Campaign-klientkonsolen. **[!UICONTROL Administration > Configuration > Data schemas]**

>[!NOTE]
>
>Enkla datamodeller kan bara tas bort av en administratör för Adobe Campaign Classic-konsolen.

![](assets/d_ncs_integration_schema_navtree.png)

Redigeringsfältet visar XML-innehållet i källschemat:

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>Med redigeringskontrollen &quot;Namn&quot; kan du ange schemanyckeln som består av namnet och namnutrymmet. Attributen name och namespace för schemats rotelement uppdateras automatiskt i schemats XML-redigeringszon.

Förhandsgranskningen genererar automatiskt det utökade schemat:

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>När källschemat sparas startas genereringen av det utökade schemat automatiskt.

Om du behöver kontrollera hela strukturen för ett schema kan du använda fliken Förhandsgranska. Om schemat har utökats kan du visa alla dess tillägg. Som ett komplement visar fliken Dokumentation alla schemaattribut och -element och deras egenskaper (SQL-fält, typ/längd, etikett, beskrivning). Fliken Dokumentation gäller endast för genererade scheman. Mer information finns i avsnittet [Återskapa scheman](../../configuration/using/regenerating-schemas.md) .

## Exempel: skapa en kontraktstabell {#example--creating-a-contract-table}

I följande exempel vill vi skapa en ny tabell för **kontrakt** i databasmodellen för Adobe Campaign-databasen. I den här tabellen kan du lagra förnamn och efternamn samt e-postadresser för innehavare och medarbetare för varje kontrakt.

För att göra detta måste du skapa tabellschemat och uppdatera databasstrukturen för att generera motsvarande tabell. Använd följande steg:

1. Redigera noden **[!UICONTROL Administration > Configuration > Data schemas]** i Adobe Campaign-trädet och klicka på **[!UICONTROL New]** .
1. Välj **[!UICONTROL Create a new table in the data model]** alternativet och klicka på **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. Ange ett namn för tabellen och ett namnutrymme.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >Som standard lagras scheman som skapas av användare i &#39;cus&#39;-namnutrymmet. Mer information finns i [Identifiering av ett schema](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. Skapa tabellens innehåll. Vi rekommenderar att du använder anmälningsguiden för att kontrollera att inga inställningar saknas. Det gör du genom att klicka på **[!UICONTROL Insert]** knappen och välja vilken typ av inställning som ska läggas till.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. Definiera inställningarna för kontraktstabellen:

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   Lägg till typen av kontrakt och placera ett index på kontraktsnumret.

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. Spara schemat för att generera strukturen:

   ![](assets/s_ncs_configuration_structure.png)

1. Uppdatera databasstrukturen för att skapa tabellen som schemat ska länkas till. Mer information finns i [Uppdatera databasstrukturen](../../configuration/using/updating-the-database-structure.md).

