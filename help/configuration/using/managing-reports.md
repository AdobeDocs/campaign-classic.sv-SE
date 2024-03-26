---
product: campaign
title: Hantera rapporter
description: Hantera rapporter
feature: Reporting, Configuration
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 4%

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
