---
title: Definiera ett villkorligt innehåll
seo-title: Definiera ett villkorligt innehåll
description: Definiera ett villkorligt innehåll
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Definiera ett villkorligt innehåll{#defining-a-conditional-content}

Du kan begränsa visningen av specifika rapportobjekt eller sidor.

Om du vill göra vissa objekt villkorliga anpassar du deras synlighetsinställningar. Mer information finns i [Villkorsobjektsvisning](#conditioning-item-display).

Om du vill göra visningen av en eller flera sidor villkorlig använder du en **[!UICONTROL Test]** typaktivitet. Mer information finns i [Villkorlig sidvisning](#conditioning-page-display).

## Visning av villkorsobjekt {#conditioning-item-display}

För att göra visningen av en del av en rapport villkorlig måste du definiera dess synlighetsvillkor: Om de inte uppfylls visas inte objekten.

Visningsvillkoren kan vara beroende av operatörens status, av vilka objekt som har markerats eller angetts på rapportsidan.

Exempel på villkorlig visning av objekt på en sida finns i [det här avsnittet](../../web/using/form-rendering.md#defining-fields-conditional-display).

I följande exempel beror visningsvillkoret på språket:

![](assets/reporting_display_condition.png)

## Villkorsstyrd sidvisning {#conditioning-page-display}

I ett rapportdiagram kan du med hjälp av den här aktiviteten ändra sidordningen beroende på ett eller flera villkor. **[!UICONTROL Test]**

Denna verksamhet bygger på följande verksamhetsprincip:

1. Placera en bild **[!UICONTROL Test]** i ett diagram och redigera den.
1. Klicka på **[!UICONTROL Add]** knappen för att skapa olika möjliga fall.

   ![](assets/reporting_test_sample.png)

   För varje fall läggs en utdataövergång till i **[!UICONTROL Test]** aktiviteten.

   ![](assets/reporting_test_transitions.png)

1. Markera alternativet **[!UICONTROL Enable default transition]** för att lägga till en övergång om något av de konfigurerade villkoren inte uppfylls.

   Mer information finns i [det här avsnittet](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

En **[!UICONTROL Test]** aktivitet kan placeras i början av diagrammet för att villkora visningen beroende på kontext- eller operatorprofilen till exempel.
