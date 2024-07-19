---
product: campaign
title: Elementlayout
description: Elementlayout
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Reporting, Monitoring
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Elementlayout{#element-layout}



Förutom de olika diagram som beskrivs [här](../../reporting/using/creating-a-chart.md#chart-types-and-variants) kan du anpassa visningen och lägga till element på rapportsidorna.

Du kan använda behållare: med dessa kan du länka flera element på en sida och konfigurera deras layout i kolumner och/eller celler. Hur du använder dem beskrivs i [det här avsnittet](../../web/using/defining-web-forms-layout.md#creating-containers).

Du kan konfigurera rapportlayouten i roten av trädet och överlagra den för varje behållare. Sidorna sorteras i kolumner. Behållare sorteras också i kolumner. Endast statiska och grafiska objekt sorteras i celler.

## Definiera alternativ för varje sida {#defining-the-options-for-each-page}

Du kan använda alternativen på varje sida i rapporten.

På fliken **[!UICONTROL General]** kan du ändra sidans titel, samt konfigurera förklaringspositioner och bläddra mellan rapportsidorna.

![](assets/s_ncs_advuser_report_wizard_022.png)

I fältet **[!UICONTROL Title]** kan du anpassa etiketten i rubriken på rapportsidan. Fönstrets titel kan konfigureras via rapportens **[!UICONTROL Properties]**-fönster. Mer information finns i [Lägga till ett sidhuvud och en sidfot](#adding-a-header-and-a-footer).

Med alternativen för **[!UICONTROL Display settings]** kan du välja placering av kontrollbildtexten på en rapportsida och definiera antalet kolumner på sidan. Mer information om sidlayout finns i avsnittet **Objektlayout** i [det här avsnittet](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

Välj de olika alternativen i avsnittet **[!UICONTROL Browse]** om du vill tillåta bläddring från en rapportsida till en annan. Om alternativet **[!UICONTROL Disable next page]** eller **[!UICONTROL Disable previous page]** väljs försvinner knapparna **[!UICONTROL Next]** och **[!UICONTROL Previous]** från rapportsidan.

## Lägga till ett sidhuvud och en sidfot {#adding-a-header-and-a-footer}

I fönstret för rapportegenskaper kan du också definiera layoutelement, t.ex. fönstrets titel och HTML i sidhuvuden och sidfötter.

Om du vill öppna egenskapsfönstret klickar du på knappen **[!UICONTROL Properties]** i rapporten.

![](assets/reporting_properties.png)

På fliken **[!UICONTROL Page]** kan du anpassa visningen.

![](assets/s_ncs_advuser_report_properties_04.png)

Innehållet som är konfigurerat på den här fliken visas på alla rapportsidor.

Med underfliken **[!UICONTROL Texts]** kan du definiera variabelt innehåll. Det kommer att tas med i översättningscykeln om rapporten är avsedd att användas på flera språk.

Detta gör att du kan skapa en lista med textfragment och länka dem till identifierare:

![](assets/s_ncs_advuser_report_properties_04a.png)

Infoga sedan dessa identifierare i HTML i rapportens innehåll:

![](assets/s_ncs_advuser_report_properties_04b.png)

De ersätts automatiskt med rätt innehåll när rapporten visas.

Precis som för HTML-texter kan du med det här operativsystemet centralisera texterna som används i rapporten och hantera översättningen av dem. Texten som skapas på den här fliken samlas automatiskt in med det inbyggda Adobe Campaign-översättningsverktyget.
