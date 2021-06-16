---
product: campaign
title: Skapa skriptet
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 4%

---

# Skapa skriptet {#step-5--creating-the-script}

Valet av leveransinnehåll som är avsett för den återstående populationen beräknas av ett skript. Det här skriptet återställer information om leveransen med det högsta antalet öppningar och kopierar innehållet till den slutliga leveransen.

## Exempel på ett skript {#example-of-a-script}

Följande skript kan användas på samma sätt som i målarbetsflödet. Mer information om detta finns i [det här avsnittet](#implementation).

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

En detaljerad förklaring av skriptet finns i [det här avsnittet](#details-of-the-script).

## Implementering {#implementation}

1. Öppna din **[!UICONTROL JavaScript code]**-aktivitet.
1. Kopiera skriptet som finns i [Exempel på ett skript](#example-of-a-script) till fönstret **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_configscript_002.png)

1. I fältet **[!UICONTROL Label]** anger du namnet på skriptet, dvs.

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Stäng aktiviteten **[!UICONTROL JavaScript code]**.
1. Spara arbetsflödet.

## Information om skriptet {#details-of-the-script}

I det här avsnittet beskrivs de olika delarna av skriptet och deras operativsystem.

* Den första delen av skriptet är en fråga. Med kommandot **queryDef** kan du från tabellen **NmsDelivery** återställa leveranser som skapats genom att målinriktningsarbetsflödet har körts och sortera dem baserat på deras beräknade öppningsfrekvens. Informationen från leveransen med den högsta öppningsfrekvensen återställs.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* Leveransen med den högsta öppningsfrekvensen dupliceras.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* Etiketten för den duplicerade leveransen ändras och ordet **final** läggs till i den.

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* Leveransen kopieras till kampanjinstrumentpanelen.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* Leveransen sparas i databasen.

   ```
   // save the delivery in database
   delivery.save()
   ```

* Den unika identifieraren för den duplicerade leveransen lagras i arbetsflödesvariabeln.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

## Andra urvalskriterier {#other-selection-criteria}

I exemplet ovan kan du välja innehållet i en leverans baserat på öppningshastigheten för e-postmeddelanden. Du kan anpassa den efter andra leveransspecifika indikatorer:

* Bästa klickfrekvens: `[indicators/@recipientClickRatio]`,
* Högsta reaktivitetsfrekvens (öppna e-post och klickningar i meddelandet): `[indicators/@reactivity]`,
* Lägsta antal klagomål: `[indicators/@refusedRatio]` (använd false-värdet för attributet sortDesc),
* Högsta konverteringsgrad: `[indicators/@transactionRatio]`,
* Antal sidor som besökts efter att ett meddelande tagits emot: `[indicators/@totalWebPage]`,
* Lägsta prenumerationsavgift: `[indicators/@optOutRatio]`,
* Transaktionsbelopp: `[indicators/@amount]`.

Nu kan du definiera den slutliga leveransen. [Läs mer](a-b-testing-uc-final-delivery.md).
