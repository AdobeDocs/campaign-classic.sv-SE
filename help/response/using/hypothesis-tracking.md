---
product: campaign
title: Spåra hypotes
description: Lär dig spåra hypoteser i svarshanteraren för kampanjer
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 878ba2b532d5cb59af77b6450b12ae5d2ff149b2
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Spårning av hypoteser{#hypothesis-tracking}

![](../../assets/common.svg)

Resultatet av hypotesberäkningarna finns på olika nivåer i Adobe Campaign: Indikatorer som beräknas utifrån hypoteser och målpopulationens reaktioner är synliga via den faktiska hypotesen, liksom i hypotesrapporter som är tillgängliga via kampanjer och leveranser.

## Hyposterresultat {#hypothesis-results}

### Indikatorer {#indicators}

När hypotesen har beräknats uppdateras flera mätningsindikatorer automatiskt. Dessa finns i **[!UICONTROL General]** hypotesens.

![](assets/response_hypothesis_delivery_example_010.png)

Dessa indikatorer är följande:

* **Antal respondentkontakter**: Antal kontaktade personer som matchar hypotesen.
* **Kontaktad svarsfrekvens**: antal kontaktpersoner/totalt antal kontaktade personer under leveransen.
* **Antal kontakter i kontrollgruppen för svarande**: antalet kontrollgrupper som matchar hypotesen.
* **Kontrollgruppens svarsfrekvens**: antal respondentkontrollgrupper/totalt antal leveranskontrollgrupper.
* **Antal reaktioner**: antal poster i tabellen som innehåller förhållandet mellan individer, hypotesen och transaktionstabellen.

Klicka på knappen **[!UICONTROL Display the list]** länk:

![](assets/response_hypothesis_indicators_002.png)

Indikatorerna ger följande information:

* **Den totala intäkten hos den kontaktade befolkningen**: Totalt antal kontaktade personer.
* **Kontrollgruppens totala inkomster**: totalbelopp över antalet kontrollgrupper.
* **Genomsnittlig intäkt per kontakt**: totalt antal/kontaktade.
* **Genomsnittlig intäkt för kontrollgruppen**: totala belopp/kontrollgrupp.
* **Total marginal per kontakt**: total marginal över kontaktad.
* **Total marginal för kontrollgruppen**: total marginal över kontrollgruppen.
* **Genomsnittlig marginal per kontakt**: total marginal/kontaktad.
* **Genomsnittlig marginal för kontrollgrupper**: totala marginaler/kontrollgrupp.
* **Ytterligare intäkter**: (Genomsnittlig intäkt för kontaktad - Genomsnittlig intäkt för kontrollgruppen)&#42;Antal kontaktade
* **Ytterligare marginal**: (Genomsnittlig kontaktmarginal - genomsnittlig kontrollgruppsmarginal) / antal kontaktade
* **Genomsnittlig kostnad per kontakt**: beräknad leveranskostnad/antal kontakter.
* **avkastning**: beräknad kostnad för leveransen/total marginal per kontakt
* **Effektiv avkastning**: beräknad leveranskostnad/tilläggsmarginal.
* **Signifikans**: innehåller värdena 0 till 3 beroende på kampanjens betydelse.

### Reaktioner {#reactions}

Du kan visa mottagarnas reaktioner på hypoteserna via **[!UICONTROL Reactions]** -fliken.

1. När hypotesberäkningen är klar går du till **[!UICONTROL Campaign management > Measurement hypotheses]** noden i Adobe Campaign-trädet.
1. Välj önskad hypotes och klicka på **[!UICONTROL Reactions]** för att visa en lista över mottagare som kan köpa något efter marknadsföringskampanjen.

   ![](assets/response_hypothesis_reactions_001.png)

## Rapporter {#reports}

The **[!UICONTROL Hypothesis report]** gör att du kan se resultatet av de hypoteser som utförts på kampanjer och leveranser. Denna rapport innehåller de indikatorer som beräknats av hypotesen (för mer information, se [Indikatorer](#indicators)).

* **På kampanjnivå**: klicka på **[!UICONTROL Reports]** länk till den relevanta kampanjen och välj **[!UICONTROL Hypothesis report]**. Den här rapporten innehåller en lista över kampanjleveranser och de hypoteser som beräknas för varje leverans.

   ![](assets/response_hypothesis_campaign_report_001.png)

* **På leveransnivå**: för att få tillgång till rapporten, öppna den aktuella leveransen, klicka på **[!UICONTROL Reports]** i **[!UICONTROL Summary]** och väljer **[!UICONTROL Hypothesis report]**. Om flera hypoteser har beräknats för samma leverans innehåller rapporten alla hypoteser.

   ![](assets/response_hypothesis_delivery_report_001.png)
