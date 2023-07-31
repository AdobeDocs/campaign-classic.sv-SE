---
product: campaign
title: Leveranskörning
description: Läs mer om exekvering och övervakning av transaktionsmeddelanden
feature: Transactional Messaging, Message Center, Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 930c6395-0c00-40ee-a925-3e0cae67c55f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 6%

---

# Leveranskörning {#delivery-execution}



## Transaktionsmeddelande skickas {#transactional-message-send}

I exekveringsinstansen skickas leveransen när anrikningsfasen är slutförd och en leveransmall har länkats till händelsen.

>[!NOTE]
>
>MTA prioriterar bearbetning av transaktionsmeddelanden framför annan leverans.

Alla leveranser grupperas i **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** mapp.

![](assets/messagecenter_deliveries_execinstances_001.png)

Som standard sorteras de i undermappar efter leveransmånad. Den här sorteringen kan ändras i meddelandemallens egenskaper enligt nedan.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](../../delivery/using/sending-with-enhanced-mta.md), kan alla transaktionsmeddelanden också skickas med Adobe Campaign Enhanced MTA för förbättrad leveransbarhet, genomströmning och studshantering. Alla effekter är desamma som för vanliga marknadsföringsmeddelanden.        

## Övervakning av transaktionsmeddelanden {#transactional-message-monitoring}

Om du vill övervaka dina transaktionsmeddelanden ska du kontrollera [leveransloggar](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

Transaktionsleveranser som skickas från körningsinstansen synkroniseras tillbaka till kontrollinstansen via ett tekniskt arbetsflöde (**[!UICONTROL Message Center execution instance]**) som går varje timme.

>[!NOTE]
>
>Leveranserna varje vecka samlar ihop händelserna baserat på den senaste händelseuppdateringen, och inte på datumet då händelsen skapades. När du extraherar leveransloggar för transaktionsmeddelanden från kontrollinstansen kan det leverans-ID som är kopplat till varje leveranslogg-ID därför ändras över tiden när loggen uppdateras (till exempel när en inkommande avhoppning tas emot för händelsen).

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->

Information om hur du övervakar aktiviteten och körningen av körningsinstansen finns i [Rapporter om transaktionsmeddelanden](../../message-center/using/about-transactional-messaging-reports.md).
