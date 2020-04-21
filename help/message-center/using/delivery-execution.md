---
title: Leveranskörning
seo-title: Leveranskörning
description: Leveranskörning
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 631e29bd6e59b8ae46084dee3a1d470916a2032b

---


# Leveranskörning{#delivery-execution}

>[!NOTE]
>
>MTA prioriterar bearbetning av transaktionsmeddelanden framför annan leverans.

I exekveringsinstansen skickas leveransen när anrikningsfasen är slutförd och en leveransmall har länkats till händelsen. Alla leveranser grupperas i **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** mappen.

![](assets/messagecenter_deliveries_execinstances_001.png)

Som standard sorteras de i undermappar efter leveransmånad.

Den här sorteringen kan ändras i meddelandemallens egenskaper enligt nedan.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Om du har uppgraderat till Förbättrat MTA för hostinginstallationer eller hybridinstallationer kan alla transaktionsmeddelanden också skickas med Förbättrat MTA i Adobe Campaign för förbättrad leverans, genomströmning och studshantering. Alla effekter är desamma som för vanliga marknadsföringsmeddelanden och de beskrivs i dokumentet Förbättrat MTA [för](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) Adobe Campaign.