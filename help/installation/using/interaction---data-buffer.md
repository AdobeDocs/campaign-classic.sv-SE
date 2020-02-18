---
title: Interaktion - databuffert
seo-title: Interaktion - databuffert
description: Interaktion - databuffert
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# Interaktion - databuffert{#interaction-data-buffer}

>[!NOTE]
>
>Vissa konfigurationer kan bara utföras av Adobe för distributioner som hanteras av Adobe. Om du till exempel vill komma åt server- och instanskonfigurationsfilerna. Mer information om de olika distributionerna finns i avsnittet [Värdmodeller](../../installation/using/hosting-models.md) eller i [den här artikeln](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

I Adobe Campaign har en **databuffertzon** introducerats i interaktionsmodulen. På så sätt kan du **öka prestanda** för inkommande interaktion genom att avsynkronisera lager och erbjuda beräkningar.

Det gäller bara inkommande interaktion, antingen via ett anrop (med eller utan anropsdata) eller via en statusuppdatering (updateStatus).

För att undvika en kö när du skriver offerter för en mottagare, genererar en ny w-process en **databuffertzon** som tillåter att förslag **skrivs asynkront**. Den här databuffertzonen läses och töms regelbundet. Standardperioden är ungefär en sekund. Därför grupperas förslagsskrivning.

Du kan **konfigurera** en databuffertzon i instansens konfigurationsfil (config-Instance.xml).

>[!NOTE]
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

