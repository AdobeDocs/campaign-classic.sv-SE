---
solution: Campaign Classic
product: campaign
title: Leveranskörning
description: Leveranskörning
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 1788346f7dfe2c18c490363c90358fcb737f1646
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 4%

---


# Leveranskörning{#delivery-execution}

## Transaktionsmeddelande som skickar {#transactional-message-send}

I exekveringsinstansen skickas leveransen när anrikningsfasen är slutförd och en leveransmall har länkats till händelsen.

>[!NOTE]
>
>MTA prioriterar bearbetning av transaktionsmeddelanden framför annan leverans.

Alla leveranser grupperas i mappen **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**.

![](assets/messagecenter_deliveries_execinstances_001.png)

Som standard sorteras de i undermappar efter leveransmånad. Den här sorteringen kan ändras i meddelandemallens egenskaper enligt nedan.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Om du har uppgraderat till Enhanced MTA kan alla transaktionsmeddelanden även skickas med Adobe Campaign Enhanced MTA för förbättrad leverans, genomströmning och studshantering. Alla konsekvenser är desamma som för vanliga marknadsföringsmeddelanden och de beskrivs i dokumentet [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/se/campaign/kb/acc-campaign-enhanced-mta.html).

## Övervakning av transaktionsmeddelande {#transactional-message-monitoring}

Kontrollera leveransloggarna om du vill övervaka dina transaktionsmeddelanden. Åtkomst till leveransloggarna presenteras i [det här avsnittet](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

Transaktionsleveranser som skickas från körningsinstansen synkroniseras tillbaka till kontrollinstansen via ett tekniskt arbetsflöde (**[!UICONTROL Message Center execution instance]**) som körs varje timme.

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