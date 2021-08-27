---
product: campaign
title: Interaktion – databuffert
description: Interaktion – databuffert
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# Interaktion – databuffert{#interaction-data-buffer}

![](../../assets/v7-only.svg)

Du kan konfigurera en databuffertzon för att öka prestanda för inkommande interaktion genom att avsynkronisera offertförslagsberäkningar. Den här konfigurationen ska utföras i instansens egen konfigurationsfil (config-Instance.xml).

I Adobe Campaign har en **databuffertzon** introducerats i interaktionsmodulen. På så sätt kan du **öka prestanda** för inkommande interaktion genom att avsynkronisera lager och erbjuda beräkningar.

Det gäller bara inkommande interaktion, antingen via ett anrop (med eller utan anropsdata) eller via en statusuppdatering (updateStatus).

För att undvika en kö när du skriver offerter för en mottagare, genererar en ny w-process en **databuffertzon** som tillåter att offerter skrivs **asynkront**. Den här databuffertzonen läses och töms regelbundet. Standardperioden är ungefär en sekund. Därför grupperas förslagsskrivning.

>[!NOTE]
>
>Den här parametern är viktig om du använder Interaction med en distribuerad arkitektur.

Databuffertzonen **konfiguration** kan göras i instansens konfigurationsfil (config-Instance.xml).

>[!CAUTION]
>
>Vissa konfigurationer kan bara utföras av Adobe för distributioner som hanteras av Adobe. Om du till exempel vill komma åt server- och instanskonfigurationsfilerna. Mer information om de olika distributionerna finns i avsnittet [Värdmodeller](../../installation/using/hosting-models.md) eller i [den här sidan](../../installation/using/capability-matrix.md).
>
>Om konfigurationen ändras måste webbservern (Apache:IIS) och Adobe Campaign-processerna startas om.\
>När du har konfigurerat databuffertzonen kontrollerar du att det finns en anpassad maskinvarukonfiguration tillgänglig. (det finns mycket minne).


När du har konfigurerat databuffertzonen kontrollerar du att det finns en anpassad maskinvarukonfiguration tillgänglig. (det finns mycket minne).

Definitionen för en daemon-skrivning (process som heter: interaktion) är följande:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Om du använder Inbound Interaction måste attributet @autostart vara true för att starta processen automatiskt när Adobe Campaign-servern startas.

Argumentinformation:

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```
