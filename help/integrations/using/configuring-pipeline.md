---
product: campaign
title: Konfigurera pipeline
description: Lär dig hur du konfigurerar pipeline för integrering av Campaign - utlösare
feature: Triggers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---

# Konfigurera pipeline {#configuring-pipeline}

Autentiseringsparametrar som kund-ID, privat nyckel och autentiseringsslutpunkt konfigureras i instanskonfigurationsfilerna.

Listan med utlösare som ska bearbetas konfigureras i ett alternativ i JSON-format.

Utlösarna används för att målinrikta via ett kampanjarbetsflöde som skickar e-post. Kampanjen är konfigurerad så att en kund som har båda utlösarhändelserna får ett e-postmeddelande.

## Förhandskrav {#prerequisites}

Kontrollera att du har:

* Ett Adobe Developer-projekt
* Ett giltigt organisations-ID - Du hittar ditt organisations-ID på [den här sidan](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* En utvecklaråtkomst till din organisation
* En giltig utlösarkonfiguration i Adobe Analytics

Autentisering krävs eftersom pipeline lagras i Adobe Experience Cloud. Den använder en autentisering som stöds via ett Adobe Developer-projekt.

## Steg 1: Skapa/uppdatera ditt Adobe Developer-projekt {#creating-adobe-io-project}

Du måste aktivera din organisation med Adobe Developer Kontotoken för integreringen av utlösare.

Lär dig hur du skapar ditt Adobe Technical-konto på [den här sidan](../../integrations/using/oauth-technical-account.md). Observera att du måste välja **[!UICONTROL Adobe Analytics]** när du lägger till API i Adobe Developer-autentiseringsuppgifter.

## Steg 2: Konfigurera alternativet för pipeline {#configuring-nmspipeline}

När autentiseringen är inställd hämtas händelserna i pipeline. Den behandlar endast utlösare som har konfigurerats i Adobe Campaign. Utlösaren måste ha genererats från Adobe Analytics och skickats till pipeline, som endast kommer att bearbeta utlösare som har konfigurerats i Adobe Campaign.

Alternativet kan också konfigureras med ett jokertecken för att fånga upp alla utlösare oavsett namn.

1. Gå till Alternativ-menyn under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** i **[!UICONTROL Explorer]** i Adobe Campaign.

1. Välj alternativet **[!UICONTROL NmsPipeline_Config]**.

1. I fältet **[!UICONTROL Value (long text)]** kan du klistra in följande JSON-kod som anger två utlösare. Se till att du tar bort kommentarer.

   ```json
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
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

1. Du kan också välja att klistra in följande JSON-kod som fångar alla utlösare.

   ```json
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

### Ange parametern Consumer {#consumer-parameter}

Rörledningen fungerar som en leverantör och en konsumentmodell. Meddelanden används endast för en enskild konsument: varje konsument får sin egen kopia av meddelandena.

Parametern **Consumer** identifierar instansen som en av de här konsumenterna. Instansens identitet anropar pipelinen. Du kan fylla den med instansnamnet som finns på sidan Övervakning på klientkonsolen.

Pipeline-tjänsten håller reda på meddelanden som hämtats av varje konsument. Om du använder olika konsumenter för olika instanser kan du se till att alla meddelanden skickas till varje instans.

### Rekommendationer för försäljningsalternativ {#pipeline-option-recommendation}

Om du vill konfigurera alternativet för pipeline bör du följa dessa rekommendationer:

* Lägg till eller redigera utlösare under **[!UICONTROL Triggers]**.
* Kontrollera att JSON är giltig.
* Parametern **Name** motsvarar utlösar-ID:t. Ett jokertecken &quot;*&quot; fångar upp alla utlösare.
* Parametern **Consumer** motsvarar namnet på den anropande instansen eller det anropande programmet.
* `pipelined`processen har också stöd för avsnittet&quot;alias&quot;.
* Du bör alltid starta om `pipelined`processen när du har gjort ändringar.

## (valfritt) Steg 3: Ytterligare konfiguration {#step-optional}

Du kan ändra vissa interna parametrar utifrån dina lastkrav, men se till att testa dem innan du använder dem i produktionsmiljön.

Listan med valfria parametrar är:

| Alternativ | Beskrivning |
|:-:|:-:|
| appName(Legacy) | AppID för OAuth-programmet som är registrerat i det äldre Oath-programmet där den offentliga nyckeln överfördes. Se denna [sida](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) för mer information om detta |
| authGatewayEndpoint(Legacy) | URL för att hämta gatewaytoken. Standard: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | Den privata nyckeln, den offentliga delen som har överförts i det äldre Oath-programmet, AES som har krypterats med alternativet XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Inaktivera autentisering, anslutning utan gatewaytoken accepteras bara av vissa slutpunkter i utvecklingsfasen. |
| discoverPipelineEndpoint | URL för att hitta slutpunkten för Pipeline Services som ska användas för den här klienten. Standard: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Period mellan två dumpar av den interna tillståndsprocessen i det interna tillståndet ```var/INSTANCE/pipelined.json.``` <br> är också tillgänglig på begäran här: ```http://INSTANCE:7781/pipelined/status``` |
| forceradPipelineEndpoint | Inaktivera identifiering av PipelineServicesEndpoint för att framtvinga den |
| monitorServerPort | Processen med rörlig orientering lyssnar på den här porten för att tillhandahålla den interna tillståndsprocessen här: ```http://INSTANCE:PORT/pipelined/status```. <br>Standardvärdet är 7781 |
| pointerFlushMessageCount | När det här antalet meddelanden bearbetas sparas förskjutningarna i databasen. <br> Standard är 1000 |
| pekareFlushPeriodSec | Efter den här perioden sparas förskjutningarna i databasen. <br>Standardvärdet är 5 (sekunder) |
| processingJSThreads | Antal dedikerade trådar som bearbetar meddelanden med anpassade JS-anslutningar. <br> Standardvärdet är 4 |
| processingThreads | Antal dedikerade trådar som bearbetar meddelanden med inbyggd kod. <br>Standardvärdet är 4 |
| retryPeriodSec | Fördröjning mellan återförsök vid fel vid bearbetning. <br>Standardvärdet är 30 (sekunder) |
| retryValiditySec | Ignorera meddelandet om det inte har bearbetats korrekt efter den här perioden (för många försök). <br>Standardvärdet är 300 (sekunder) |

### Automatisk processstart i pipeline {#pipelined-process-autostart}

Processen `pipelined` måste startas automatiskt.

För detta anger du elementet `<`pipelined`>` i konfigurationsfilen som autostart=&quot;true&quot;:

```sql
 <pipelined autoStart="true" ... "/>
```

### Omstart av process i pipeline {#pipelined-process-restart}

En omstart krävs för att ändringarna ska börja gälla:

```sql
nlserver restart pipelined@instance
```

## Steg 4: Validering {#step-validation}

Följ stegen nedan för att validera pipeline-konfigurationen för etablering:

* Kontrollera att processen `pipelined` körs.
* Kontrollera om det finns anslutningsloggar för pipeline i `pipelined.log`.
* Kontrollera anslutningen och om ping-filer tas emot. Värdkunder kan använda övervakning från klientkonsolen.
