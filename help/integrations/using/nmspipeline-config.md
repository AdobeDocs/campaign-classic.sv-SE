---
solution: Campaign Classic
product: campaign
title: Konfigurera integreringen
description: Konfigurera integreringen
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 2%

---


# Pipelinealternativet NmsPipeline_Config {#nmspipeline_config}

När autentiseringen fungerar kan [!DNL pipelined] hämta händelserna och bearbeta dem. Den behandlar endast utlösare som har konfigurerats i Adobe Campaign och ignorerar de andra. Utlösaren måste ha genererats från Analytics och flyttats till pipeline i förväg.
Alternativet kan också konfigureras med ett jokertecken för att fånga upp alla utlösare oavsett namn.

Konfigurationen av utlösarna görs i ett alternativ, under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Alternativnamnet är **[!UICONTROL NmsPipeline_Config]**. Datatypen är&quot;lång text&quot; i JSON-format.

I det här exemplet anges två utlösare.

Klistra in JSON-koden från den här mallen i alternativvärdet. Se till att du tar bort kommentarer.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
            "triggers": [ // Array of triggers. 
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}
```

Det andra exemplet fångar upp alla utlösare.

```
{
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }
```

>[!NOTE]
>
>UID-värdet [!DNL Trigger] till ett specifikt utlösarnamn i Analytics-gränssnittet finns som en del av URL-frågesträngsparametrarna i utlösargränssnittet. triggerType-UID skickas i pipeline-dataströmmen och kod kan skrivas till pipeline.JS för att mappa utlösar-UID till en användarvänlig etikett som kan lagras i en utlösarnamnskolumn i pipelineEvents-schemat.

## Konsumentparametern {#consumer-parameter}

Rörledningen fungerar med en modell som&quot;leverantör och konsument&quot;. Det kan finnas många konsumenter i samma kö. Meddelanden&quot;förbrukas&quot; endast av en enskild kund. Varje konsument får sin egen&quot;kopia&quot; av budskapen.

Parametern&quot;Consumer&quot; identifierar förekomsten som en av dessa konsumenter. Det är identiteten på instansen som anropar pipelinen. Du kan fylla den med instansnamnet. Pipeline-tjänsten håller reda på meddelanden som hämtats av varje konsument. Genom att använda olika konsumenter för olika instanser ser du till att alla meddelanden skickas till varje instans.

## Konfigurera alternativet för pipeline {#configure-pipeline-option}

Lägg till eller redigera Experience Cloud-utlösare under arrayen&quot;triggers&quot;, redigera inte resten.
Kontrollera att JSON är giltig med hjälp av denna [webbplats](http://jsonlint.com/).

* &quot;name&quot; är utlösar-ID. Ett jokertecken (*) fångar upp alla utlösare.
* &quot;Consumer&quot; är en unik sträng som unikt identifierar nlserver-instansen. Det kan vanligtvis vara själva instansnamnet. För flera miljöer (dev/stage/prod) måste du se till att det är unikt för var och en av dem så att varje instans får en kopia av meddelandet.
* [!DNL Pipelined] har också stöd för avsnittet&quot;alias&quot;.

Starta om [!DNL pipelined] när du har gjort ändringarna.
