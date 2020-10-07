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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 5%

---


# Hantera rapporter{#managing-reports}

Rapporter baserade på ett schema som är specifikt för Adobe Campaign standardmottagare (nm:mottagare eller schemalänkad) måste utvecklas på nytt för att data från den anpassade tabellen och dess tabeller ska kunna länkas via målmappningen (se avsnittet [Målmappning](../../configuration/using/target-mapping.md) ).

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

