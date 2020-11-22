---
solution: Campaign Classic
product: campaign
title: Om att simulera erbjudanden
description: Om att simulera erbjudanden
audience: interaction
content-type: reference
topic-tags: simulating-offers
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 3%

---


# Om att simulera erbjudanden{#about-offers-simulation}

Med modulen **Simulering** kan du testa distributionen av erbjudanden som tillhör en kategori eller en miljö innan du skickar ditt förslag till mottagarna.

Simuleringen tar hänsyn till de kontexter och regler för behörighet som tidigare använts för erbjudanden (se [Översikt över](../../interaction/using/offer-catalog-overview.md)erbjudandekatalogen) samt deras presentationsregler (se [Hantera erbjudandepresentation](../../interaction/using/managing-offer-presentation.md)). Detta gör att ni kan testa och förfina olika versioner av ert erbjudande utan att faktiskt använda ett erbjudande eller över/under beställning av ett mål, eftersom simuleringen inte har någon effekt på de avsedda mottagarna.

Läs stegen nedan om du vill lära dig hur du simulerar ett erbjudande. You can also watch this [video](https://helpx.adobe.com/campaign/classic/how-to/simulate-offer-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/introduction/collection.ccx.js&amp;ref=helpx.adobe.com).

## Huvudsteg för att skapa en simulering {#main-steps-for-creating-a-simulation}

Så här kör du en simulering av dina erbjudanden:

1. Klicka på **[!UICONTROL Profiles and Targets]** länken i **[!UICONTROL Simulations]** universum och klicka sedan på **[!UICONTROL Create]** knappen.

   ![](assets/offer_simulation_001.png)

1. Spara och redigera den simulering du just har skapat.
1. Gå till **[!UICONTROL Edit]** fliken och ange körningsinställningar.

   For more on this, refer to [Execution settings](../../interaction/using/execution-settings.md).

   ![](assets/offer_simulation_003.png)

   >[!NOTE]
   >
   >Körningsinställningar är bara tillgängliga om du använder Interaktion med Campaign.

1. Ange simuleringsomfånget.

   Mer information finns i [Definition av omfånget](../../interaction/using/simulation-scope.md#definition-of-the-scope).

   ![](assets/offer_simulation_004.png)

1. Lägg till rapportaxlar för att förbättra **[!UICONTROL Offer distribution by rank]** rapporten (valfritt).

   Mer information finns i [Lägga till rapportaxlar](../../interaction/using/simulation-scope.md#adding-reporting-axes).

   ![](assets/offer_simulation_005.png)

1. Klicka **[!UICONTROL Save]** för att spela in simuleringsinställningarna.
1. Starta simuleringen via kontrollpanelen.

   ![](assets/offer_simulation_006.png)

1. Kontrollera simuleringsresultatet och visa analysrapporten.

   For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

   ![](assets/offer_simulation_007.png)
