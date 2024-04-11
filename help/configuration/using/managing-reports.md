---
product: campaign
title: Hantera rapporter
description: Hantera rapporter
feature: Reporting, Configuration
role: Data Engineer, Developer
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Hantera rapporter{#managing-reports}



Rapporter baserade på ett schema som är specifikt för Adobe Campaign standardmottagare (nm:mottagare eller schemalänkad) måste utvecklas på nytt för att data från den anpassade tabellen och dess tabeller ska kunna länkas via målmappningen (se [Målmappning](../../configuration/using/target-mapping.md) ).

Om du vill skapa nya rapporter ska du läsa [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md).

I vissa fall måste du också skapa nya kuber som är specifika för dessa tabeller. Kuber beskrivs i [det här avsnittet](../../reporting/using/ac-cubes.md).

Följande rapporter berörs:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): förslagsspårning i realtid.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): öppnas med uppdelning enligt användarprogramvara.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analys av delningsaktiviteter, öppningar och prenumerationer per tidsperiod.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): spårningsindikatorer för leverans i ett mobilprogram.
* **[!UICONTROL Offer analysis]** (offerAnalysis): erbjudandeanalys per datum och kanal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): reaktivitetsfrekvens för de senaste leveranserna.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): uppdelning av aktiva prenumerationer per mobilprogram.
