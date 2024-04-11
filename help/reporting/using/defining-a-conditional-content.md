---
product: campaign
title: Definiera ett villkorligt innehåll
description: Definiera ett villkorligt innehåll
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Reporting, Monitoring
exl-id: efee50f7-d917-4c71-add2-116c4b8f7013
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 7%

---

# Definiera ett villkorligt innehåll{#defining-a-conditional-content}



Du kan begränsa visningen av specifika rapportobjekt eller sidor.

Om du vill göra vissa objekt villkorliga anpassar du deras synlighetsinställningar. Mer information finns i [Visning av villkorsobjekt](#conditioning-item-display).

Om du vill göra visningen av en eller flera sidor villkorlig använder du **[!UICONTROL Test]** typaktivitet. Mer information finns i [Visning av villkorssida](#conditioning-page-display).

## Visning av villkorsobjekt {#conditioning-item-display}

Om du vill att visningen av en del av en rapport ska vara villkorlig måste du definiera dess synlighetsvillkor: om de inte uppfylls visas inte objekten.

Visningsvillkoren kan vara beroende av operatörens status, av vilka objekt som har markerats eller angetts på rapportsidan.

Exempel på villkorlig visning av objekt på en sida finns i [det här avsnittet](../../web/using/form-rendering.md#defining-fields-conditional-display).

I följande exempel beror visningsvillkoret på språket:

![](assets/reporting_display_condition.png)

## Visning av villkorssida {#conditioning-page-display}

I rapportens diagram **[!UICONTROL Test]** kan du ändra sidsekvensen beroende på ett eller flera villkor.

Denna verksamhet bygger på följande verksamhetsprincip:

1. Placera en **[!UICONTROL Test]** i ett diagram och redigera.
1. Klicka på **[!UICONTROL Add]** för att skapa olika möjliga fall.

   ![](assets/reporting_test_sample.png)

   För varje fall läggs en utdataövergång till i **[!UICONTROL Test]** aktivitet.

   ![](assets/reporting_test_transitions.png)

1. Välj **[!UICONTROL Enable default transition]** om du vill lägga till en övergång, om ett av de konfigurerade villkoren inte uppfylls.

   Mer information om detta finns i [det här avsnittet](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

A **[!UICONTROL Test]** kan du placera aktiviteten i början av diagrammet för att ange att visningen ska vara beroende av kontext- eller operatorprofil, till exempel.
