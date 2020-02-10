---
title: Samla in alla besök
seo-title: Samla in alla besök
description: Samla in alla besök
seo-description: null
page-status-flag: never-activated
uuid: c2869b3d-33bb-4a22-a8e6-ac037f0665d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 7f841368-3867-4d6e-9720-c038d9bea0ce
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Samla in alla besök{#collecting-all-visits}

Med hjälp av webbspårningsmodulen i Adobe Campaign kan du samla in besök på vissa sidor av webbplatsen som en mottagare utför i samband med webbplatsspårning efter ett klick i ett meddelande.

Du kan dock konfigurera plattformen så att den samlar in alla besök på sidor med en webbspårningstagg från en användare som är känd för plattformen.

En användare som är känd för plattformen är en mottagare som redan har fått målet av en leverans och som har klickat i ett mottaget meddelande minst en gång. En permanent cookie används för att identifiera den här mottagaren.

>[!CAUTION]
>
>Adobe Campaign-plattformen är inte avsedd att användas som ett verktyg för webbplatsspårning, förutom när man besöker webbplatsen efter ett klick i ett meddelande. När det här alternativet är aktiverat kan det leda till mycket hög användning av resurser på de datorer som är värdar för dina servrar (omdirigering, program och databas). Vi rekommenderar att du ser till att maskinvaruarkitekturen kan hantera den här inläsningen och undviker att placera webbspårningstaggar på de mest besökta sidorna, till exempel hemsidan.

## Serverkonfiguration {#server-configuration}

Servrarna konfigureras genom att överlagra vissa element i **filen serverConf.xml** . Dessa filer sparas i underkatalogen **conf** i installationskatalogen för Adobe Campaign.

### Omdirigeringsserver {#redirection-server}

För omdirigeringsservern anger du attributet **trackWebVisitors** för **omdirigeringselementet** till **true**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## Konfigurera en standardmatchningskampanj {#configuring-a-default-matching-campaign}

Om du vill visa spårningsinformation via klientkonsolen måste du:

* Skapa en **overksam leverans** (leveransmappningen måste vara identisk med mappningen av målschemat),
* Ange det **interna namnet** för leveransen i alternativet **NmsTracking_WebTrackingDelivery** .

All information om webbplatsspårning som inte kommer direkt efter ett klick i ett e-postmeddelande kan visas i den provleverans som skapas.
