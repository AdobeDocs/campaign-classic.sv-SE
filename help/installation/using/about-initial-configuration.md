---
solution: Campaign Classic
product: campaign
title: Om inledande konfiguration
description: Om inledande konfiguration
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 5%

---


# Om inledande konfiguration{#about-initial-configuration}

När Adobe Campaign-installationen är klar måste du konfigurera den så att den fungerar effektivt med dina begränsningar och din tekniska arkitektur. Stegen för att konfigurera en Adobe Campaign-instans beskrivs i det här kapitlet i följande sekvens:

1. Skapa instansen och den relaterade anslutningen, se [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).
1. Information om hur du skapar och konfigurerar databasen finns i [Skapa och konfigurera databasen](../../installation/using/creating-and-configuring-the-database.md).
1. Konfigurera Adobe Campaign-servern, se [Kampanjserverkonfiguration](../../installation/using/campaign-server-configuration.md).
1. Distribuera instansen i [Distribuera en instans](../../installation/using/deploying-an-instance.md).

När du konfigurerar instansen måste du aktivera processer (webb, mta, wfserver, osv.) som ska startas på servern och konfigureras moduler för att skicka e-post, för spårning osv. För varje instans aktiveras Adobe Campaign-processer på servern. Mer information finns i [Aktivera processer](../../installation/using/campaign-server-configuration.md#enabling-processes).

Ytterligare konfigurationer kan krävas för varje instans (beroende på vilka moduler som används, arkitekturen och dina behov) för att optimera Adobe Campaign-driften.
