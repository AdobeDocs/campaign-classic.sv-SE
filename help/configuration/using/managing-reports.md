---
title: Hantera rapporter
seo-title: Hantera rapporter
description: Hantera rapporter
seo-description: null
page-status-flag: never-activated
uuid: 3b8e6f11-4cbd-450e-871b-50fd0ead96db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 21777423-0c8a-4bb1-b210-972f660648bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Hantera rapporter{#managing-reports}

Rapporter som baseras på ett schema som är specifikt för Adobe Campaign-standardmottagarna (nm:mottagare eller schemalänkad) måste utvecklas på nytt för att data från den anpassade tabellen och dess tabeller ska kunna länkas via målmappningen (se avsnittet [Målmappning](../../configuration/using/target-mapping.md) ).

Se [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md)för att skapa nya rapporter.

I vissa fall måste du också skapa nya kuber som är specifika för dessa tabeller. Kuber beskrivs närmare i [det här avsnittet](../../reporting/using/about-cubes.md).

Följande rapporter berörs:

* **[!UICONTROL Recent proposition tracking]** (recentPropositions): förslagsspårning i realtid.
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent): öppnas enligt användarprogram.
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities): analys av delningsaktiviteter, öppningar och prenumerationer per tidsperiod.
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback): spårningsindikatorer för leverans i mobilapplikationer.
* **[!UICONTROL Offer analysis]** (offerAnalysis): analys av erbjudanden per datum och kanal.
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution): reaktivitetsgrad för de senaste leveranserna.
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution): Uppdelning av aktiva prenumerationer per mobilapplikation.

