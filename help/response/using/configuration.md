---
product: campaign
title: Konfigurera kampanjsvarshanteraren
description: Lär dig hur du konfigurerar svarshanteraren för Campaign
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Konfigurera kampanjsvarshanteraren{#configuration}

![](../../assets/v7-only.svg)

Detta avsnitt är avsett för personer som ansvarar för att konfigurera svarshantering. Det förutsätter en viss kunskap om hur man utökar scheman, definierar arbetsflöden och SQL-programmering.

På så sätt kan du förstå hur du anpassar standarddatamodellen till den specifika karaktären hos en transaktionsregister som ligger utanför Adobe Campaign med tabellen över enskilda. Denna tabell över individer kan sammanfalla med tabellen över tillgängliga individer i Adobe Campaign eller med en annan tabell

Mäthypotesen startas av arbetsflödet för operationsprocessen ( **[!UICONTROL operationMgt]** ). Varje hypotes representerar en separat process som körs asynkront med körningsstatus (Redigeras, Väntar, Slutförd, Misslyckades osv.) och styrs av en schemaläggare som hanterar prioritetsbegränsningar, begränsning av antalet samtidiga processer, sidan med låg aktivitet och automatisk exekvering med frekvens.

## Konfigurera scheman {#configuring-schemas}

>[!CAUTION]
>
>Ändra inte de inbyggda schemana i programmet, utan använd i stället schemautbyggnadsmekanismen. I annat fall kommer ändrade scheman inte att uppdateras vid tidpunkten för framtida uppgraderingar av programmet. Detta kan leda till felfunktioner när Adobe Campaign används.

Programintegrering krävs innan reaktionsmodulen används, för att definiera de olika tabeller (transaktioner, transaktionsdetaljer) som ska mätas samt deras relation till leveranser, erbjudanden och individer.

### Standardscheman {#standard-schemas}

En färdig lösning **[!UICONTROL nms:remaMatch]** schemat innehåller reaktionsloggtabellen, dvs. relationen mellan individer, hypotes och transaktionstabell. Detta schema ska användas som arvsschema för reaktionsloggarnas slutliga destinationstabell.

The **[!UICONTROL nms:remaMatchRcp]** schemat finns också som standard och innehåller lagring av reaktionsloggar för Adobe Campaign-mottagare ( **[!UICONTROL nms:recipient]** ). För att kunna användas måste den utökas för att mappas till ett transaktionsregister (som innehåller inköp osv.).

### Transaktionsregister och transaktionsinformation {#transaction-tables-and-transaction-details}

Transaktionstabellen måste innehålla direktlänkar till personer.

Du kan också lägga till en tabell som innehåller transaktionsinformation. Detta är inte direkt kopplat till individer.

Om vi till exempel tar ett kvitto länkas ett transaktionsregister till en kontakt (inleveransregister) och ett kvittoregister länkas bara till kvittoregistret (detaljregister). Du kan sedan konfigurera hypotesen direkt på den nivå där kvittotabellen är kopplad till kvittotabellen.

>[!NOTE]
>
>Om du vill behålla den kvitto-ID som beskriver det förväntade beteendet i hypoteserna kan du utöka tabellmallen nms:remaMatchRcp för att lägga till identifieraren i den (i det här fallet är ingen ROI-beräkning kopplad till dessa fält).

Vi rekommenderar att du lägger till ett eventdatum.

I följande schema visas kopplingar mellan de olika tabellerna när konfigurationen är klar:

![](assets/response_data_model.png)

### Svarshantering och mottagare {#response-management-with-adobe-campaign-recipients}

I det här exemplet integrerar vi en tabell med inköp i svarsmodulen med den inbyggda mottagartabellen från Adobe Campaign **[!UICONTROL nms:recipient]**.

Svarstabellen loggar på en **[!UICONTROL nms:remaMatchRcp]** mottagaren utökas för att lägga till en länk till inköpstabellschemat. I följande exempel anropas inköpstabellen **demo:köp**.

1. Via Adobe Campaign Explorer väljer du **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Högerklicka **Mottagare** välj **[!UICONTROL Actions]** och **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. Du kan anpassa **[!UICONTROL Extension namespace]** i nästa fönster klickar du på **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. I **[!UICONTROL Response management]** ska du se till att **[!UICONTROL Generate a storage schema for reactions]** är markerad.

   Klicka sedan på **[!UICONTROL Define additional fields...]** om du vill välja relaterade transaktionstabeller och lägga till önskade fält i tillägget för nms:remaMatchRcp-schemat.

   ![](assets/delivery_mapping3.png)

Det skapade schemat ser ut så här:

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### Svarshantering med en anpassad mottagartabell {#response-management-with-a-personalized-recipient-table}

I det här exemplet integrerar vi en inköpstabell i svarsmodulen med hjälp av en annan tabell med personer än mottagartabellen i Adobe Campaign.

* Skapa ett nytt svarsloggsschema som härleds från **[!UICONTROL nms:remaMatch]** schema.

   Eftersom tabellen med enskilda användare skiljer sig från tabellen med Adobe Campaign-mottagare är det nödvändigt att skapa ett nytt schema med svarsloggarna baserat på **[!UICONTROL nms:remaMatch]** schema. Fyll sedan i den med länkar till leveransloggarna och inköpstabellen.

   I följande exempel använder vi **demo:broadLogPers** schema och **demo:köp** transaktionsregister:

   ```
   <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
   img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
     <element name="remaMatchPers" template="nms:remaMatch">
       <key internal="true" name="match">
         <keyfield xlink="hypothesis"/>
        <keyfield xlink="purchase"/>
       </key>
   
       <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
       <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
                target="demo:propositionPers" type="link"/>
       <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
     </element>
   </srcSchema>
   ```

* Ändra hypotesformen i **[!UICONTROL nms:remaHypothesis]** schema.

   Som standard visas svarsloggarna i mottagarloggarna. Du måste därför ändra hypotesformuläret för att kunna visa de nya svarsloggarna som skapades under det föregående steget.

   Exempel:

   ```
    <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                 <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                  toolbarCaption="Responses generated by the hypothesis" type="linklist"
                  xpath="remaMatchPers">
             <input xpath="[.]"/>
             <input xpath="@controlGroup"/>
           </input>
      </container> 
   ```

## Hantera indikatorer {#managing-indicators}

Svarshanterarmodulen innehåller en lista med fördefinierade indikatorer. Du kan dock lägga till andra personaliserade mätningsindikatorer.

För att göra detta måste du utöka tabellen med hypoteser genom att infoga två fält för varje ny indikator:

* den första för målpopulationen,
* den andra för kontrollgruppen.

Exempel:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```
