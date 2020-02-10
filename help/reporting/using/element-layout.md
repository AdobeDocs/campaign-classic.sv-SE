---
title: Elementlayout
seo-title: Elementlayout
description: Elementlayout
seo-description: null
page-status-flag: never-activated
uuid: 60dc80d9-f81b-48ce-9341-f975daaf5ebc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 8fdda764-3e42-4972-a9c9-63567588931e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Elementlayout{#element-layout}

Förutom de olika diagram som beskrivs här: [Diagramtyper och varianter](../../reporting/using/creating-a-chart.md#chart-types-and-variants)kan du anpassa visningen och lägga till element på rapportsidorna.

Du kan använda behållare: Med dessa kan du länka flera element på en sida och konfigurera deras layout i kolumner och/eller celler. Hur du använder dem beskrivs i [detta avsnitt](../../web/using/defining-web-forms-layout.md#creating-containers).

Du kan konfigurera rapportlayouten i roten av trädet och överlagra den för varje behållare. Sidorna sorteras i kolumner. Behållare sorteras också i kolumner. Endast statiska och grafiska objekt sorteras i celler.

## Definiera alternativ för varje sida {#defining-the-options-for-each-page}

Du kan använda alternativen på varje sida i rapporten.

På fliken **[!UICONTROL General]** kan du ändra sidans titel, samt konfigurera förklaringspositioner och bläddra mellan rapportsidorna.

![](assets/s_ncs_advuser_report_wizard_022.png)

I **[!UICONTROL Title]** fältet kan du anpassa etiketten i rubriken på rapportsidan. Fönstrets namn kan konfigureras via rapportens **[!UICONTROL Properties]** fönster. Mer information finns i [Lägga till ett sidhuvud och en sidfot](#adding-a-header-and-a-footer).

Med alternativen kan du **[!UICONTROL Display settings]** välja kontrollbildtextens position på en rapportsida och definiera antalet kolumner på sidan. Mer information om sidlayout finns i avsnittet **Objektlayout** i [det här avsnittet](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Välj de olika alternativen i **[!UICONTROL Browse]** avsnittet för att godkänna bläddring från en rapportsida till en annan. Om alternativet **[!UICONTROL Disable next page]** eller **[!UICONTROL Disable previous page]** alternativet är markerat försvinner **[!UICONTROL Next]** - och **[!UICONTROL Previous]** -knapparna från rapportsidan.

## Lägga till ett sidhuvud och en sidfot {#adding-a-header-and-a-footer}

I fönstret för rapportegenskaper kan du även definiera layoutelement, till exempel: fönstrets titel, HTML-innehållet för sidhuvuden och sidfötter.

Du öppnar egenskapsfönstret genom att klicka på **[!UICONTROL Properties]** knappen i rapporten.

![](assets/reporting_properties.png)

På fliken **[!UICONTROL Page]** kan du anpassa visningen.

![](assets/s_ncs_advuser_report_properties_04.png)

Innehållet som är konfigurerat på den här fliken visas på alla rapportsidor.

På **[!UICONTROL Texts]** underfliken kan du definiera variabelt innehåll: det kommer att beaktas under översättningscykeln om rapporten är avsedd att användas på flera språk.

Detta gör att du kan skapa en lista med textfragment och länka dem till identifierare:

![](assets/s_ncs_advuser_report_properties_04a.png)

Infoga sedan dessa identifierare i HTML-innehållet i rapporten:

![](assets/s_ncs_advuser_report_properties_04b.png)

De ersätts automatiskt med rätt innehåll när rapporten visas.

Precis som för HTML-texter kan du med det här operativsystemet centralisera texterna som används i rapporten och hantera översättningen av dem. Texten som skapas på den här fliken samlas automatiskt in av det integrerade översättningsverktyget Adobe Campaign.
