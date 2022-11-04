---
product: campaign
title: Hantera rapporter
description: Hantera rapporter
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# Hantera rapporter{#managing-reports}

![](../../assets/common.svg)

Rapporter baserade på ett schema som är specifikt för Adobe Campaign standardmottagare (nm:mottagare eller schemalänkad) måste utvecklas på nytt för att data från den anpassade tabellen och dess tabeller ska kunna länkas via målmappningen (se [Målmappning](../../configuration/using/target-mapping.md) ).

För att skapa nya rapporter, se [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md).

I vissa fall måste du också skapa nya kuber som är specifika för dessa tabeller. Kuber beskrivs i [det här avsnittet](../../reporting/using/ac-cubes.md).

Följande rapporter berörs:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): förslagsspårning i realtid.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): öppnas enligt användarprogram.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analys av delningsaktiviteter, öppningar och prenumerationer per tidsperiod.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): spårningsindikatorer för leverans i mobilapplikationer.
* **[!UICONTROL Offer analysis]** (offerAnalysis): analys av erbjudanden per datum och kanal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): reaktivitetsgrad för de senaste leveranserna.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): Uppdelning av aktiva prenumerationer per mobilapplikation.
