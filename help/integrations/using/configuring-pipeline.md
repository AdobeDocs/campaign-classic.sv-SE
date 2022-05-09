---
product: campaign
title: Konfigurera pipeline
description: Lär dig hur du konfigurerar pipeline
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Konfigurera pipeline {#configuring-pipeline}

![](../../assets/common.svg)

Autentiseringsparametrar som kund-ID, privat nyckel och autentiseringsslutpunkt konfigureras i instanskonfigurationsfilerna.
Listan med utlösare som ska bearbetas konfigureras i ett alternativ i JSON-format.
Utlösarna används för målanpassning av ett kampanjarbetsflöde som skickar e-post. Kampanjen är konfigurerad så att en kund som har båda utlösarhändelserna får ett e-postmeddelande.

## Förhandskrav {#prerequisites}

Kontrollera att du använder:

* Minst en av följande Adobe Campaign-byggen:
   * 19.1.8.9039
   * 19.1.4.9032 - Gold Standard 11
   * 20.2.4.9187
   * 20.3.1
* Adobe Analytics Standard

Du behöver också:

* Adobe I/O projektautentisering
* ett giltigt organisations-ID - Om du vill hitta ditt organisations-ID, se [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}
* en utvecklaråtkomst till din organisation
* utlöser konfiguration som gjorts i Adobe Analytics

## Autentiserings- och konfigurationsfiler {#authentication-configuration}

Autentisering krävs eftersom pipeline lagras i Adobe Experience Cloud.
Den använder ett par offentliga och privata nycklar. Den här processen har samma funktion som en användare/ett lösenord, men är säkrare.
Autentisering stöds för Marketing Cloud via Adobe I/O Project.

## Steg 1: Skapa/uppdatera Adobe I/O-projekt {#creating-adobe-io-project}

För kunder med värdtjänst kan du skapa en kundtjänstbiljett som gör att din organisation kan använda Adobe I/O Technical Account Tokens för integrering av utlösare.

För On Premise-kunder, se [Konfigurera Adobe I/O för Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) sida. Observera att du måste välja **[!UICONTROL Adobe Analytics]** när API lades till i Adobe I/O-autentiseringsuppgifterna.

## Steg 2: Konfigurerar alternativet för NmsPipeline_Config-pipeline {#configuring-nmspipeline}

När autentiseringen är klar hämtas händelserna. Det bearbetar bara utlösare som har konfigurerats i Adobe Campaign. Utlösaren måste ha genererats från Adobe Analytics och skickats till pipeline, som endast kommer att bearbeta utlösare som har konfigurerats i Adobe Campaign.
Alternativet kan också konfigureras med ett jokertecken för att fånga upp alla utlösare oavsett namn.

1. I Adobe Campaign finns alternativmenyn under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**  > **[!UICONTROL Options]** i **[!UICONTROL Explorer]**.

1. Välj **[!UICONTROL NmsPipeline_Config]** alternativ.

1. I **[!UICONTROL Value (long text)]** kan du klistra in följande JSON-kod som anger två utlösare. Du måste se till att ta bort kommentarer.

   ```
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

### Parametern Consumer {#consumer-parameter}

Rörledningen fungerar som en leverantör och en konsumentmodell. Meddelanden används endast för enskilda konsumenter: varje konsument får en egen kopia av budskapen.

The **Konsument** parameter identifierar förekomsten som en av dessa konsumenter. Instansens identitet anropar pipeline. Du kan fylla den med instansnamnet som finns på sidan Övervakning på klientkonsolen.

Pipeline-tjänsten håller reda på meddelanden som hämtats av varje konsument. Om du använder olika konsumenter för olika instanser kan du se till att alla meddelanden skickas till varje instans.

### Rekommendationer för försäljningsalternativ {#pipeline-option-recommendation}

Så här konfigurerar du alternativet för pipeline:

* Lägg till eller redigera utlösare under **[!UICONTROL Triggers]** ska du inte redigera resten.
* Kontrollera att JSON är giltig. Du kan använda en JSON-validerare, se [webbplats](https://jsonlint.com/) till exempel.
* &quot;name&quot; motsvarar utlösar-ID:t. Ett jokertecken &quot;*&quot; fångar upp alla utlösare.
* &quot;Consumer&quot; motsvarar namnet på den anropande instansen eller det anropande programmet.
* Pipelined har också stöd för ämnet&quot;alias&quot;.
* Du bör alltid starta om pipelined när du har gjort ändringar.

## Steg 3: Valfri konfiguration {#step-optional}

Du kan ändra vissa interna parametrar utifrån dina lastkrav, men se till att testa dem innan du sätter dem i produktion.

Listan med valfria parametrar finns nedan:

| Option | Beskrivning |
|:-:|:-:|
| appName(Legacy) | AppID för OAuth-programmet som är registrerat i det äldre Oath-programmet där den offentliga nyckeln överfördes. Se denna [sida](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) för mer information om detta |
| authGatewayEndpoint(Legacy) | URL för att hämta gatewaytoken. Standard: ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | Den privata nyckeln, den offentliga delen som överförts i det äldre Oath-programmet, AES som krypterats med alternativet XtkKey: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(Legacy) | Inaktivera autentisering, anslutning utan gatewaytoken accepteras bara av vissa slutpunkter i utvecklingsfasen. |
| discoverPipelineEndpoint | URL för att hitta slutpunkten för Pipeline Services som ska användas för den här klienten. Standard: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | Period mellan två dumpar av den interna tillståndsprocessen i ```var/INSTANCE/pipelined.json.``` <br> Den interna statusen är även tillgänglig på begäran här: ```http://INSTANCE:7781/pipelined/status``` |
| forceradPipelineEndpoint | Inaktivera identifiering av PipelineServicesEndpoint för att framtvinga den |
| monitorServerPort | Den rörliga processen avlyssnar den här porten för att tillhandahålla den interna tillståndsprocessen här: ```http://INSTANCE:PORT/pipelined/status```. <br>Standardvärdet är 7781 |
| pointerFlushMessageCount | När det här antalet meddelanden bearbetas sparas förskjutningarna i databasen. <br> Standardvärdet är 1000 |
| pekareFlushPeriodSec | Efter den här perioden sparas förskjutningarna i databasen. <br>Standardvärdet är 5 (sek) |
| processingJSThreads | Antal dedikerade trådar som bearbetar meddelanden med anpassade JS-anslutningar. <br> Standard är 4 |
| processingThreads | Antal dedikerade trådar som bearbetar meddelanden med inbyggd kod. <br>Standard är 4 |
| retryPeriodSec | Fördröjning mellan återförsök vid fel vid bearbetning. <br>Standardvärdet är 30 (sekunder) |
| retryValiditySec | Ignorera meddelandet om det inte har bearbetats korrekt efter den här perioden (för många försök). <br>Standardvärdet är 300 (sekunder) |

### Automatisk processstart i pipeline {#pipelined-process-autostart}

Processen med rörlig orientering måste startas automatiskt.

För detta anger du elementet &lt; pipelined > i konfigurationsfilen som autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### Omstart av process i pipeline {#pipelined-process-restart}

En omstart krävs för att ändringarna ska börja gälla:

```
nlserver restart pipelined@instance
```

## Steg 4: Validering {#step-validation}

Följ stegen nedan för att validera pipeline-konfigurationen för etablering:

* Se till att [!DNL pipelined] processen körs.
* Kontrollera om det finns anslutningsloggar för pipeline i filen pipelined.log.
* Kontrollera anslutningen och om ping-filer tas emot. Värdkunder kan använda övervakning från klientkonsolen.
