---
product: campaign
title: Om inledande konfiguration
description: Om inledande konfiguration
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 8%

---

# Viktiga steg för att konfigurera och distribuera instansen{#about-initial-configuration}

![](../../assets/v7-only.svg)

När Adobe Campaign-installationen är klar måste du konfigurera den så att den fungerar effektivt med dina begränsningar och din tekniska arkitektur. Stegen för att konfigurera en Adobe Campaign-instans beskrivs i det här kapitlet i följande sekvens:

1. Skapa instansen och den relaterade anslutningen, se [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).
1. Skapa och konfigurera databasen, se [Skapa och konfigurera databasen](../../installation/using/creating-and-configuring-the-database.md).
1. Konfigurera Adobe Campaign-servern, se [Kampanjserverkonfiguration](../../installation/using/configuring-campaign-server.md).
1. Distribuera instansen, se [Distribuera en instans](../../installation/using/deploying-an-instance.md).

När du konfigurerar instansen måste du aktivera processer (webb, mta, wfserver, osv.) som ska startas på servern och konfigureras moduler för att skicka e-post, för spårning osv. För varje instans aktiveras Adobe Campaign-processer på servern. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#enabling-processes).

Ytterligare konfigurationer kan krävas för varje instans (beroende på vilka moduler som används, arkitekturen och dina behov) för att optimera Adobe Campaign-driften.
