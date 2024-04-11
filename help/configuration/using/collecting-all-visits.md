---
product: campaign
title: Samla in alla besök
description: Samla in alla besök
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 3%

---

# Samla in alla besök{#collecting-all-visits}

Med webbspårningsmodulen som tillhandahålls av Adobe Campaign kan du samla in besök på vissa sidor av webbplatsen som utförs av en mottagare i samband med webbplatsspårning efter ett klick i ett meddelande.

Du kan dock konfigurera plattformen så att den samlar in alla besök på sidor med en webbspårningstagg från en användare som är känd för plattformen.

En användare som är känd för plattformen är en mottagare som redan har fått målet av en leverans och som har klickat i ett mottaget meddelande minst en gång. En permanent cookie används för att identifiera den här mottagaren.

>[!IMPORTANT]
>
>Adobe Campaign-plattformen är inte avsedd att användas som ett verktyg för webbplatsspårning, förutom när man besöker webbplatsen efter ett klick i ett meddelande. När det här alternativet är aktiverat kan det leda till mycket hög användning av resurser på de datorer som är värdar för dina servrar (omdirigering, program och databas). Vi rekommenderar att du ser till att maskinvaruarkitekturen kan hantera den här inläsningen och undviker att placera webbspårningstaggar på de mest besökta sidorna, till exempel hemsidan.

## Serverkonfiguration {#server-configuration}

Servrarna konfigureras genom att överlagra vissa element i **serverConf.xml** -fil. Dessa filer sparas i **conf** underkatalogen till Adobe Campaign installationskatalog.

### Omdirigeringsserver {#redirection-server}

Ange **trackWebVisitors** attributet för **omdirigering** element till **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Konfigurera en standardmatchningskampanj {#configuring-a-default-matching-campaign}

Om du vill visa spårningsinformation via klientkonsolen måste du:

* Skapa en **provleverans** (leveransmappningen måste vara identisk med mappningen av målschemat),
* Ange **internt namn** av leveransen i **NmsTracking_WebTrackingDelivery** alternativ.

All information om webbplatsspårning som inte kommer direkt efter ett klick i ett e-postmeddelande kan visas i den dummy-leverans som skapas.
