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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 9%

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
>Om du har uppgraderat till Enhanced MTA kan alla transaktionsmeddelanden även skickas med Adobe Campaign Enhanced MTA för förbättrad leverans, genomströmning och studshantering. Alla effekter är desamma som för vanliga marknadsföringsmeddelanden och de beskrivs i [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/se/campaign/kb/acc-campaign-enhanced-mta.html) -dokument.