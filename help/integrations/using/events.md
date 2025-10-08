---
product: campaign
title: Konfigurera händelser
description: Lär dig konfigurera händelser för anpassad implementering
feature: Triggers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# Konfigurera händelser för anpassad implementering {#events}



Delar av den här konfigurationen är en anpassad utveckling som kräver följande:

* Arbetskunskaper om JSON-, XML- och Javascript-parsning i Adobe Campaign.
* Arbetskunskaper i API:erna för QueryDef och Writer.
* Aktuella krypterings- och autentiseringsfunktioner med privata nycklar.

Eftersom det krävs tekniska kunskaper för att redigera Javascript-koden bör du inte försöka utan rätt förståelse.

## Bearbeta händelser i JavaScript {#events-javascript}

### JavaScript {#file-js}

Pipeline använder en JavaScript-funktion för att bearbeta varje meddelande. Den här funktionen är användardefinierad.

Den har konfigurerats i alternativet **[!UICONTROL NmsPipeline_Config]** under attributet JSConnector. Denna JavaScript anropas varje gång en händelse tas emot. Den körs av processen [!DNL pipelined].

Javascript-exempelfilen är cus:triggers.js.

### Funktionen JavaScript {#function-js}

JavaScript [!DNL pipelined] måste börja med en specifik funktion.

Den här funktionen anropas en gång för varje händelse:

```
function processPipelineMessage(xmlTrigger) {}
```

Den ska returnera som

```
<undefined/>
```

Du bör starta om [!DNL pipelined] när du har redigerat JavaScript.

### Utlös dataformat {#trigger-format}

Data [!DNL trigger] skickas till JS-funktionen i XML-format.

* Attributet **[!UICONTROL @triggerId]** innehåller namnet på [!DNL trigger].
* Elementet **enrichments** i JSON-format innehåller data som genererats av Adobe Analytics och är kopplat till utlösaren.
* **[!UICONTROL @offset]** är pekaren till meddelandet. Den anger ordningen för meddelandet i kön.
* **[!UICONTROL @partition]** är en behållare med meddelanden i kön. Förskjutningen är relativ till en partition. <br>Det finns ungefär 15 partitioner i kön.

Exempel:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Berikning av dataformat {#enrichment-format}

>[!NOTE]
>
>Det är ett specifikt exempel från olika möjliga implementeringar.

Innehållet definieras i JSON-format i Adobe Analytics för varje utlösare.
I en utlösare av typen LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** kan innehålla Shopper-ID:t i strängformat, som används för att stämma av mot Adobe Campaign-mottagare. <br>Det måste avstämas för att hitta Shopper ID:t, som är primärnyckeln.

* **[!UICONTROL timeGMT]** kan innehålla tiden för utlösaren på Adobe Analytics-sidan i UTC Epoch-format (sekunder sedan 01/01/1970 UTC).

Exempel:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### Bearbetningsordning för händelser{#order-events}

Händelserna bearbetas en i taget i förskjutningsordning. Varje tråd i [!DNL pipelined] bearbetar en annan partition.

Offset för den senaste händelsen som har hämtats lagras i databasen. Om processen stoppas startar den därför om från det sista meddelandet. Dessa data lagras i det inbyggda schemat xtk:pipelineOffset.

Den här pekaren är specifik för varje förekomst och varje konsument. När många instanser använder samma pipeline med olika konsumenter får de därför alla meddelanden och i samma ordning.

Parametern **Consumer** i pipeline-alternativet identifierar den anropande instansen.

Det finns för närvarande inget sätt att ha olika köer för olika miljöer som&quot;staging&quot; eller&quot;dev&quot;.

### Loggning och felhantering {#logging-error-handling}

Loggar som logInfo() dirigeras till loggen [!DNL pipelined]. Fel som logError() skrivs till loggen [!DNL pipelined] och gör att händelsen placeras i en ny försökskö. I det här fallet bör du kontrollera loggen i pipeline.
Felmeddelanden provas flera gånger under den varaktighet som angetts för alternativen [!DNL pipelined].

För felsökning och övervakning skrivs alla utlösande data in i utlösartabellen i fältet&quot;data&quot; i XML-format. En logInfo() som innehåller utlösardata har också samma syfte.

### Tolka data {#data-parsing}

Detta exempel på Javascript-kod tolkar eVar01 i anrikningarna.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

Var försiktig när du tolkar för att undvika fel.
Eftersom den här koden används för alla utlösare krävs de flesta data inte. Därför kan den lämnas tom om den inte finns.

### Lagra utlösaren {#storing-triggers-js}

>[!NOTE]
>
>Det är ett specifikt exempel från olika möjliga implementeringar.

Detta exempel på JS-kod sparar utlösaren i databasen.

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>;
 }
```

### Begränsningar {#constraints}

Prestanda för denna kod måste vara optimala eftersom den körs med höga frekvenser och kan orsaka potentiella negativa effekter för andra marknadsföringsaktiviteter. Speciellt om mer än en miljon utlöser händelser per timme på marknadsföringsservern eller om det inte är korrekt justerat.

Kontexten för detta JavaScript är begränsad. Alla funktioner i API är inte tillgängliga. getOption() eller getCurrentDate() fungerar till exempel inte.

För att möjliggöra snabbare bearbetning körs flera trådar i det här skriptet samtidigt. Koden måste vara trådsäker.

## Lagra händelser {#store-events}

>[!NOTE]
>
>Det är ett specifikt exempel från olika möjliga implementeringar.

### Pipeline-händelseschema {#pipeline-event-schema}

Händelser lagras i en databastabell. Det används av marknadsföringskampanjer för att rikta sig till kunder och berika e-postmeddelanden med hjälp av triggers.
Även om varje utlösare kan ha en distinkt datastruktur, kan alla utlösare hållas i en enda tabell.
Fältet triggerType identifierar varifrån data kommer.

Här följer ett exempel på schemakod för den här tabellen:

| Attribut | Typ | Etikett | Beskrivning |
|:-:|:-:|:-:|:-:|
| pipelineEventId | Lång | Primär nyckel | Utlösarens interna primärnyckel. |
| data | PM | Utlösardata | Det fullständiga innehållet i utlösande data i XML-format. För felsökning och revision. |
| triggerType | Sträng 50 | TriggerType | Namnet på utlösaren. Identifierar kundens beteende på webbplatsen. |
| shopper_id | Sträng 32 | shopper_id | Köparens interna identifierare. Anges av avstämningsarbetsflödet. Om noll betyder det att kunden är okänd i Campaign. |
| shopper_key | Lång | shopper_key | Bugarens externa identifierare enligt Analytics. |
| skapad | Datetime | Skapad | Den tid då händelsen skapades i Campaign. |
| lastModified | Datetime | Senast ändrad | Den senaste gången händelsen ändrades i Adobe. |
| timeGMT | Datetime | Tidsstämpel | Den tid då händelsen genererades i Analytics. |

### Visa händelserna {#display-events}

Händelserna kan visas med ett enkelt formulär baserat på händelseschemat.

>[!NOTE]
>
>Pipeline Event-noden är inte inbyggd och måste läggas till, liksom det relaterade formuläret måste skapas i Campaign. De här åtgärderna är begränsade till expertanvändare. Mer information finns i [Redigera formulär](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Bearbeta händelserna {#processing-the-events}

### Avstämningsarbetsflöde {#reconciliation-workflow}

Avstämning är processen att matcha kunden från Adobe Analytics med Adobe Campaign-databasen. Kriterierna för matchning kan till exempel vara shopper_id.

Av prestandaskäl måste matchningen göras i gruppläge av ett arbetsflöde.
Frekvensen måste vara inställd på 15 minuter för att arbetsbelastningen ska optimeras. Därför är fördröjningen mellan en mottagning i Adobe Campaign och dess bearbetning i ett marknadsföringsarbetsflöde upp till 15 minuter.

### Alternativ för enhetsavstämning i JavaScript {#options-unit-reconciliation}

Det går att köra avstämningsfrågan för varje utlösare i JavaScript. Den har högre prestandapåverkan och ger snabbare resultat. Det kan behövas för särskilda användningsfall när reaktivitet behövs.

Det kan vara svårt att implementera om inget index anges för shopper_id. Om villkoren finns på en separat databasserver än marknadsföringsservern, används en databaslänk, vilket har dålig prestanda.

### Rensa arbetsflöde {#purge-workflow}

Utlösare bearbetas inom en timme. Volymen kan vara cirka 1 miljon utlösare per timme. Det förklarar varför ett rensningsarbetsflöde måste införas. Tömningen körs en gång per dag och alla utlösare som är äldre än tre dagar tas bort.

### Arbetsflöde för kampanj {#campaign-workflow}

Arbetsflödet för utlösarkampanjer liknar ofta andra återkommande kampanjer som har använts.
Den kan till exempel börja med en fråga om utlösare som letar efter specifika händelser under den sista dagen. Det målet används för att skicka e-postmeddelandet. Anrikningar eller data kan komma från utlösaren. Det kan användas säkert av Marketing eftersom det inte kräver någon konfiguration.
