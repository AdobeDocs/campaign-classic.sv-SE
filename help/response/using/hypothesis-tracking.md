---
product: campaign
title: Spåra hypotes
description: Lär dig spåra hypoteser i svarshanteraren för kampanjer
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Spårning av hypoteser{#hypothesis-tracking}

![](../../assets/v7-only.svg)

Resultatet av hypotesberäkningarna finns på olika nivåer i Adobe Campaign: Indikatorer som beräknas utifrån hypoteser och målpopulationens reaktioner är synliga via den faktiska hypotesen, liksom i hypotesrapporter som är tillgängliga via kampanjer och leveranser.

## Hyposterresultat {#hypothesis-results}

### Indikatorer {#indicators}

När hypotesen har beräknats uppdateras flera mätningsindikatorer automatiskt. Dessa finns på fliken **[!UICONTROL General]** i hypotesen.

![](assets/response_hypothesis_delivery_example_010.png)

Dessa indikatorer är följande:

* **Antal respondentkontakter**: Antal kontaktade personer som matchar hypotesen.
* **Kontaktad svarsfrekvens**: antal kontaktpersoner/totalt antal kontaktade personer under leveransen.
* **Antal kontaktpersoner** i kontrollgruppen för svarande: antalet kontrollgrupper som matchar hypotesen.
* **Kontrollgruppens** svarsfrekvens: antal respondentkontrollgrupper/totalt antal leveranskontrollgrupper.
* **Antal reaktioner**: antal poster i tabellen som innehåller förhållandet mellan individer, hypotesen och transaktionstabellen.

Klicka på länken **[!UICONTROL Display the list]** om du vill se en fullständig lista över indikatorer:

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

Du kan visa mottagarnas reaktioner på hypoteserna via fliken **[!UICONTROL Reactions]**.

1. När hypotesberäkningen är klar går du till noden **[!UICONTROL Campaign management > Measurement hypotheses]** i Adobe Campaign-trädet.
1. Välj önskad hypotes och klicka på fliken **[!UICONTROL Reactions]** för att visa en lista över mottagare som kan köpa något efter marknadsföringskampanjen.

   ![](assets/response_hypothesis_reactions_001.png)

## Rapporter {#reports}

Med **[!UICONTROL Hypothesis report]** kan du visa resultatet av de hypoteser som utförts på kampanjer och leveranser. Denna rapport innehåller de indikatorer som beräknats av hypotesen (mer information finns i [Indikatorer](#indicators)).

* **På kampanjnivå**: klicka på  **[!UICONTROL Reports]** länken till den relevanta kampanjen och välj  **[!UICONTROL Hypothesis report]**. Den här rapporten innehåller en lista över kampanjleveranser och de hypoteser som beräknas för varje leverans.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **På leveransnivå**: för att öppna rapporten öppnar du den aktuella leveransen, klickar på  **[!UICONTROL Reports]** på  **[!UICONTROL Summary]** fliken och väljer  **[!UICONTROL Hypothesis report]**. Om flera hypoteser har beräknats för samma leverans innehåller rapporten alla hypoteser.

   ![](assets/response_hypothesis_delivery_report_001.png)
