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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tekniska arbetsflöden{#technical-workflows}

Du måste se till att de tekniska arbetsflödena för kontrollinstansen och de olika körningsinstanserna verkligen har skapats och startats innan du distribuerar några transaktionsmeddelandemallar.

De olika tekniska arbetsflödena för transaktionsmeddelanden (Message Center) är uppdelade mellan kontrollinstansen och körningsinstansen/instanserna.

## Styra instansarbetsflöden {#control-instance-workflows}

På kontrollinstansen måste du skapa ett arkiveringsarbetsflöde per körningsinstans. Du kommer sedan åt arkiveringsarbetsflödena via mappen **Administration > Produktion > Meddelandecenter** . Arkiveringsarbetsflödena startas automatiskt när de har skapats.

**Distribuerad arkitektur**

Om du har registrerat en eller flera körningsinstanser på kontrollinstansen måste du skapa ett arkiveringsarbetsflöde för varje **[!UICONTROL Message Center execution instance]** externt konto. Klicka på **[!UICONTROL Create the archiving workflow]** knappen för att skapa och starta arbetsflödet.

![](assets/messagecenter_archiving_002.png)

**Minimal arkitektur**

När kontroll- och körningsmodulerna har installerats på samma instans måste du skapa arkiveringsarbetsflödet med distributionsguiden. Klicka på **[!UICONTROL Create the archiving workflow]** knappen för att skapa och starta arbetsflödet.

![](assets/messagecenter_archiving_001.png)

## Arbetsflöden för körningsinstanser {#execution-instance-workflows}

På körningsinstansen/instanserna kan du komma åt de tekniska arbetsflödena för transaktionsmeddelanden via mappen **Administration > Produktion > Meddelandecenter** . Du behöver bara starta dem. Arbetsflödena i listan är:

* **[!UICONTROL Processing batch events]** (internt namn: **[!UICONTROL batchEventsProcessing]** ): Med det här arbetsflödet kan du dela upp grupphändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Processing real time events]** (internt namn: **[!UICONTROL rtEventsProcessing]** ): Med det här arbetsflödet kan du bryta ned realtidshändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Update event status]** (internt namn: **[!UICONTROL updateEventStatus]** ): det här arbetsflödet gör att du kan tilldela en status till händelsen.

   Följande händelselägen är tillgängliga:

   * **[!UICONTROL Pending]** : händelsen finns i kön. Ingen meddelandemall har tilldelats den ännu.
   * **[!UICONTROL Pending delivery]** : Om händelsen finns i kön har en meddelandemall tilldelats den och bearbetas av leveransen.
   * **[!UICONTROL Sent]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.
   * **[!UICONTROL Ignored by the delivery]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen ignorerades.
   * **[!UICONTROL Delivery failed]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen misslyckades.
   * **[!UICONTROL Event not taken into account]** : händelsen kunde inte länkas till en meddelandemall. Händelsen kommer inte att bearbetas.

