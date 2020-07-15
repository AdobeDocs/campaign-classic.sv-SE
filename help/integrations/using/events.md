---
title: Konfigurera integreringen
seo-title: Konfigurera integreringen
description: Konfigurera integreringen
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 0%

---


# Utlösarhändelser {#events}

## Bearbeta händelser i JavaScript {#events-javascript}

### JavaScript-fil {#file-js}

Pipeline använder en JavaScript-funktion för att bearbeta varje meddelande. Den här funktionen är användardefinierad.

Den är konfigurerad i alternativet **[!UICONTROL NmsPipeline_Config]** under attributet JSConnector. Detta javascript anropas varje gång en händelse tas emot. Det styrs av [!DNL pipelined] processen.

JS-exempelfilen är cus:triggers.js.

### JavaScript-funktion {#function-js}

Javascript- [!DNL pipelined] filen måste börja med en viss funktion.

Den här funktionen anropas en gång för varje händelse:

```
function processPipelineMessage(xmlTrigger) {}
```

Den ska returnera som

```
<undefined/>
```

Starta om [!DNL pipelined] när du har redigerat JS.

### Utlös dataformat {#trigger-format}

Data skickas [!DNL trigger] till JS-funktionen. Det är i XML-format.

* Attributet **[!UICONTROL @triggerId]** innehåller namnet på [!DNL trigger].
* Elementet **enrichments** i JSON-format innehåller data som genererats av Analytics och är kopplat till utlösaren.
* **[!UICONTROL @offset]** är pekaren till meddelandet. Den anger ordningen för meddelandet i kön.
* **[!UICONTROL @partitio]**n är en meddelandebehållare i kön. Förskjutningen är relativ till en partition. <br>Det finns ungefär 15 partitioner i kön.

Exempel:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### Dataformat för berikning {#enrichment-format}

>[!NOTE]
>
>Det är ett specifikt exempel från olika möjliga implementeringar.

Innehållet definieras i Analytics för varje utlösare. Det är i JSON-format.
I en utlösare av typen LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** kan innehålla det Shopper-ID som används för att stämma av mot Campaign-mottagare. Det är i strängformat. <br>Den måste avstämas för att hitta Shopper ID, som är primärnyckeln.

* **[!UICONTROL timeGMT]** kan innehålla tidpunkten för utlösaren på Analytics-sidan. Det är i UTC Epoch-format (sekunder sedan 01/01/1970 UTC).

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

### Ordning för händelsebearbetning {#order-events}

Händelserna bearbetas en i taget i förskjutningsordning. Varje tråd i [!DNL pipelined] bearbetar en egen partition.

&quot;Offset&quot; för den senaste händelsen som hämtats lagras i databasen. Om processen stoppas startar den därför om från det sista meddelandet. Dessa data lagras i det inbyggda schemat xtk:pipelineOffset.

Den här pekaren är specifik för varje förekomst och varje konsument. När många instanser använder samma pipeline med olika konsumenter får de därför alla meddelanden och i samma ordning.

Parametern &quot;Consumer&quot; i pipeline-alternativet identifierar den anropande instansen.

Det finns för närvarande inget sätt att ha olika köer för olika miljöer som&quot;staging&quot; eller&quot;dev&quot;.

### Loggning och felhantering {#logging-error-handling}

Loggar som logInfo() dirigeras till [!DNL pipelined] loggen. Fel som logError() skrivs till [!DNL pipelined] loggen och gör att händelsen placeras i en ny försökskö. Kontrollera den rörliga loggen.
Felmeddelanden provas flera gånger under den varaktighet som angetts i [!DNL pipelined] alternativen.

För felsökning och övervakning skrivs alla utlösande data in i utlösartabellen. Det finns i datafältet i XML-format. En logInfo() som innehåller utlösardata har också samma syfte.

### Tolka data {#data-parsing}

Detta exempel på JS-kod tolkar eVar01 i anrikningarna.

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
 {```
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

Prestanda för den här koden måste vara optimala eftersom den körs med höga frekvenser. Det finns potentiella negativa effekter för andra marknadsföringsaktiviteter. Speciellt om mer än en miljon utlöser händelser per timme på marknadsföringsservern. Eller om den inte är rätt inställd.

Kontexten för detta JavaScript är begränsad. Alla funktioner i API:t är inte tillgängliga. getOption() eller getCurrentDate() fungerar till exempel inte.

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
| shopper_id | Sträng 32 | shopper_id | Köparens interna identifierare. Anges av avstämningsarbetsflödet. Om värdet är noll betyder det att kunden är okänd i Campaign. |
| shopper_key | Lång | shopper_key | Bugarens externa identifierare som hämtats av Analytics. |
| skapad | Datetime | Skapad | Den tid då händelsen skapades i Campaign. |
| lastModified | Datetime | Senast ändrad | Senaste gången händelsen ändrades i Adobe. |
| timeGMT | Datetime | Tidsstämpel | Den tidpunkt då händelsen genererades i Analytics. |

### Visa händelserna {#display-events}

Händelserna kan visas med ett enkelt formulär baserat på händelseschemat.

>[!NOTE]
>
>Pipeline Event-noden är inte inbyggd och måste läggas till, liksom det relaterade formuläret måste skapas i Campaign. De här åtgärderna är begränsade till expertanvändare. Mer information finns i följande avsnitt: [Navigeringshierarki](../../configuration/using/about-navigation-hierarchy.md) och [formulärredigering](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## Bearbeta händelserna {#processing-the-events}

### Avstämningsarbetsflöde {#reconciliation-workflow}

Avstämning är processen att matcha kunden från Analytics med Campaign-databasen. Kriterierna för matchning kan till exempel vara shopper_id.

Av prestandaskäl måste matchningen göras i gruppläge av ett arbetsflöde.
Frekvensen måste anges till 15 minuter för att arbetsbelastningen ska optimeras. Därför är fördröjningen mellan ett mottagningstillfälle i Adobe Campaign och dess behandling i ett marknadsföringsarbetsflöde upp till 15 minuter.

### Alternativ för enhetsavstämning i JavaScript {#options-unit-reconciliation}

Teoretiskt sett är det möjligt att köra avstämningsfrågan för varje utlösare i JavaScript. Den har högre prestandapåverkan och ger snabbare resultat. Det kan behövas för särskilda användningsfall när reaktivitet behövs.

Det kan vara svårt att göra det om inget index anges för shopper_id. Om villkoren finns på en separat databasserver än marknadsföringsservern, används en databaslänk, vilket har dålig prestanda.

### Rensa arbetsflöde {#purge-workflow}

Utlösare bearbetas inom en timme så det finns ingen anledning att behålla dem länge. Volymen kan vara cirka 1 miljon utlösare per timme. Det förklarar varför ett rensningsarbetsflöde måste införas. Rensa tar bort alla utlösare som är äldre än tre dagar och körs en gång om dagen.

### Arbetsflöde för kampanj {#campaign-workflow}

Arbetsflödet för utlösarkampanjer liknar ofta andra återkommande kampanjer som har använts.
Den kan till exempel börja med en fråga om utlösare som letar efter specifika händelser under den sista dagen. Målet används för att skicka e-postmeddelandet. Anrikningar eller data kan komma från utlösaren. Det kan användas säkert av Marketing eftersom det inte kräver någon konfiguration.
