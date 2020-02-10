---
title: Spårning av hyposer
seo-title: Spårning av hyposer
description: Spårning av hyposer
seo-description: null
page-status-flag: never-activated
uuid: cb949a9d-8bbe-446b-b5b4-22234a91a68b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 4452bfc6-9ac4-4d81-a63c-879a163c13ee
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Spårning av hyposer{#hypothesis-tracking}

Resultatet av hypotesberäkningar finns på olika nivåer i Adobe Campaign-plattformen: Indikatorer som beräknas utifrån hypoteser och målpopulationens reaktioner är synliga via den faktiska hypotesen, liksom i hypotesrapporter som är tillgängliga via kampanjer och leveranser.

## Hyposterresultat {#hypothesis-results}

### Indikatorer {#indicators}

När hypotesen har beräknats uppdateras flera mätningsindikatorer automatiskt. Dessa finns på **[!UICONTROL General]** fliken för hypotesen.

![](assets/response_hypothesis_delivery_example_010.png)

Dessa indikatorer är följande:

* **Antal respondentkontakter**: Antal kontaktade personer som matchar hypotesen.
* **Kontaktad svarsfrekvens**: antal kontaktpersoner/totalt antal kontaktade personer under leveransen.
* **Antal kontaktpersoner** i kontrollgruppen för svarande: antalet kontrollgrupper som matchar hypotesen.
* **Kontrollgruppens** svarsfrekvens: antal respondentkontrollgrupper/totalt antal leveranskontrollgrupper.
* **Antal reaktioner**: antal poster i tabellen som innehåller förhållandet mellan individer, hypotesen och transaktionstabellen.

Klicka på **[!UICONTROL Display the list]** länken om du vill se en fullständig lista över indikatorer:

![](assets/response_hypothesis_indicators_002.png)

Indikatorerna ger följande information:

* **De totala intäkterna från den kontaktade** befolkningen: Totalt antal kontaktade personer.
* **Total intäkt för kontrollgruppen**: totalbelopp över antalet kontrollgrupper.
* **Genomsnittlig intäkt per kontakt**: totalt antal/kontaktade.
* **Genomsnittlig intäkt för kontrollgruppen**: totala belopp/kontrollgrupp.
* **Total marginal per kontakt**: total marginal över kontaktad.
* **Total marginal för kontrollgruppen**: total marginal över kontrollgruppen.
* **Genomsnittlig marginal per kontakt**: total marginal/kontaktad.
* **Genomsnittlig marginal för kontrollgrupper**: totala marginaler/kontrollgrupp.
* **Ytterligare intäkter**: (Genomsnittlig intäkt för kontaktad kontrollgrupp - genomsnittlig intäkt för kontrollgruppen)*Antal kontaktade
* **Ytterligare marginal**: (Genomsnittlig kontaktmarginal - genomsnittlig kontrollgruppsmarginal) / antal kontaktade
* **Genomsnittskostnad per kontakt**: beräknad leveranskostnad/antal kontakter.
* **Avkastning**: beräknad kostnad för leveransen/total marginal per kontakt
* **Effektiv avkastning**: beräknad leveranskostnad/tilläggsmarginal.
* **Signifikans**: innehåller värdena 0 till 3 beroende på kampanjens betydelse.

### Reaktioner {#reactions}

Du kan visa mottagarnas reaktioner på hypoteserna via **[!UICONTROL Reactions]** fliken.

1. När beräkningen av hypotesen är klar går du till noden **[!UICONTROL Campaign management > Measurement hypotheses]** i Adobe Campaign-trädet.
1. Välj önskad hypotes och klicka på **[!UICONTROL Reactions]** fliken för att visa en lista över mottagare som kan köpa något efter marknadsföringskampanjen.

   ![](assets/response_hypothesis_reactions_001.png)

## Rapporter {#reports}

Här **[!UICONTROL Hypothesis report]** kan du se resultatet av de hypoteser som utförts på kampanjer och leveranser. Denna rapport innehåller de indikatorer som beräknats genom hypotesen (för mer information, se [Indikatorer](#indicators)).

* **På kampanjnivå**: klicka på **[!UICONTROL Reports]** länken för den relevanta kampanjen och välj **[!UICONTROL Hypothesis report]**. Den här rapporten innehåller en lista över kampanjleveranser och de hypoteser som beräknas för varje leverans.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **På leveransnivå**: för att öppna rapporten öppnar du den aktuella leveransen, klickar på **[!UICONTROL Reports]** på **[!UICONTROL Summary]** fliken och väljer **[!UICONTROL Hypothesis report]**. Om flera hypoteser har beräknats för samma leverans innehåller rapporten alla hypoteser.

   ![](assets/response_hypothesis_delivery_report_001.png)
