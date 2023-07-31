---
product: campaign
title: Om inledande konfiguration
description: Om inledande konfiguration
feature: Installation, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 12%

---

# Viktiga steg för att konfigurera och distribuera instansen{#about-initial-configuration}



När Adobe Campaign-installationen är klar måste du konfigurera den så att den fungerar effektivt med dina begränsningar och din tekniska arkitektur. Stegen för att konfigurera en Adobe Campaign-instans beskrivs i det här kapitlet i följande sekvens:

1. Skapa instansen och den relaterade anslutningen, se [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).
1. Skapa och konfigurera databasen, se [Skapa och konfigurera databasen](../../installation/using/creating-and-configuring-the-database.md).
1. Konfigurera Adobe Campaign-servern, se [Kampanjserverkonfiguration](../../installation/using/configuring-campaign-server.md).
1. Distribuera instansen, se [Distribuera en instans](../../installation/using/deploying-an-instance.md).

När du konfigurerar instansen måste du aktivera processer (webb, mta, wfserver, osv.) som ska startas på servern och konfigureras moduler för att skicka e-post, för spårning osv. För varje instans aktiveras Adobe Campaign-processer på servern. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#enabling-processes).

Ytterligare konfigurationer kan krävas för varje instans (beroende på vilka moduler som används, arkitekturen och dina behov) för att optimera Adobe Campaign-driften.
