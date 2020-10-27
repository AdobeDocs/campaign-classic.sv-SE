---
title: Tekniska arbetsflöden
seo-title: Tekniska arbetsflöden
description: Tekniska arbetsflöden
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
translation-type: tm+mt
source-git-commit: f7527a2d9b76e34fbaa2c9471c44a7a1e7e074d7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 11%

---


# Tekniska arbetsflöden{#technical-workflows}

Du måste se till att de tekniska arbetsflödena för kontrollinstansen och de olika körningsinstanserna verkligen har skapats och startats innan du distribuerar några transaktionsmeddelandemallar.

De olika tekniska arbetsflödena för transaktionsmeddelanden (Message Center) är uppdelade mellan kontrollinstansen och körningsinstansen/instanserna.

## Styra instansarbetsflöden {#control-instance-workflows}

Oavsett om du har en eller flera instanser registrerade för körning i kontrollinstansen måste du skapa ett arkiveringsarbetsflöde för varje **[!UICONTROL Message Center execution instance]** externt konto. Klicka på **[!UICONTROL Create the archiving workflow]** knappen för att skapa och starta arbetsflödet.

![](assets/messagecenter_archiving_002.png)

Du kommer sedan åt dessa arbetsflöden via mappen **Administration > Produktion > Meddelandecenter** . Arkiveringsarbetsflödena startas automatiskt när de har skapats.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## Arbetsflöden för körningsinstanser {#execution-instance-workflows}

På körningsinstansen/instanserna kan du komma åt de tekniska arbetsflödena för transaktionsmeddelanden via mappen **Administration > Produktion > Meddelandecenter** . Du behöver bara starta dem. Arbetsflödena i listan är:

* **[!UICONTROL Processing batch events]** (internt namn: **[!UICONTROL batchEventsProcessing]** ): Med det här arbetsflödet kan du dela upp grupphändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Processing real time events]** (internt namn: **[!UICONTROL rtEventsProcessing]** ): Med det här arbetsflödet kan du bryta ned realtidshändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Update event status]** (internt namn: **[!UICONTROL updateEventStatus]** ): det här arbetsflödet gör att du kan tilldela en status till händelsen.

   Följande händelselägen är tillgängliga:

   * **[!UICONTROL Pending]** : händelsen finns i kön. Ingen meddelandemall har ännu tilldelats den.
   * **[!UICONTROL Pending delivery]** : Om händelsen finns i kön har en meddelandemall tilldelats den och bearbetas av leveransen.
   * **[!UICONTROL Sent]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.
   * **[!UICONTROL Ignored by the delivery]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen ignorerats.
   * **[!UICONTROL Delivery failed]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen misslyckats.
   * **[!UICONTROL Event not taken into account]** : händelsen kunde inte länkas till en meddelandemall. Händelsen kommer inte att bearbetas.

