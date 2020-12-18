---
solution: Campaign Classic
product: campaign
title: Leveranskörning
description: Leveranskörning
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 8%

---


# Leveranskörning{#delivery-execution}

>[!NOTE]
>
>MTA prioriterar bearbetning av transaktionsmeddelanden framför annan leverans.

I exekveringsinstansen skickas leveransen när anrikningsfasen är slutförd och en leveransmall har länkats till händelsen. Alla leveranser grupperas i mappen **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Som standard sorteras de i undermappar efter leveransmånad.

Den här sorteringen kan ändras i meddelandemallens egenskaper enligt nedan.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Om du har uppgraderat till Enhanced MTA kan alla transaktionsmeddelanden även skickas med Adobe Campaign Enhanced MTA för förbättrad leverans, genomströmning och studshantering. Alla konsekvenser är desamma som för vanliga marknadsföringsmeddelanden och de beskrivs i dokumentet [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/se/campaign/kb/acc-campaign-enhanced-mta.html).