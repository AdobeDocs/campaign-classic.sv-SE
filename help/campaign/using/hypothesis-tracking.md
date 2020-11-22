---
solution: Campaign Classic
product: campaign
title: Spåra hypoteser
description: Spåra hypoteser
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 1%

---


# Spåra hypoteser{#hypothesis-tracking}

Resultatet av hypotesberäkningarna finns på olika nivåer i Adobe Campaign: Indikatorer som beräknas utifrån hypoteser och målpopulationens reaktioner är synliga via den faktiska hypotesen, liksom i hypotesrapporter som är tillgängliga via kampanjer och leveranser.

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
