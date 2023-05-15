---
product: campaign
title: Erbjudanden på en utgående kanal
description: Erbjudanden på en utgående kanal
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 77fee343-09d1-4d60-be43-efe02953a70c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 3%

---

# Erbjudanden på en utgående kanal{#offers-on-an-outbound-channel}



## Leverans av e-posterbjudande {#email-offer-delivery}

I vår databas finns det en kategori reseerbjudanden till Afrika. Berättigandet, kontexterna och representationerna för varje erbjudande har konfigurerats. Nu vill vi skapa en kampanj som visar våra erbjudanden via e-post.

1. Skapa en marknadsföringskampanj och ett arbetsflöde för målinriktning.

   ![](assets/offer_delivery_example_001.png)

1. Redigera e-postleveransen och klicka på **[!UICONTROL Offers]** ikon.

   ![](assets/offer_delivery_example_002.png)

1. Välj det e-postutrymme för din erbjudandemiljö som matchar helgerna.

   ![](assets/offer_delivery_example_003.png)

1. Välj den kategori som innehåller reseerbjudandena för Afrika.

   ![](assets/offer_delivery_example_004.png)

1. Ställ in antalet erbjudanden i leveransen till två.

   ![](assets/offer_delivery_example_005.png)

1. Stäng fönstret för hantering av erbjudanden och skapa innehållet i leveransen.

   ![](assets/offer_delivery_example_006.png)

1. Använd menyerna för att infoga ett första erbjudande och välj återgivningsfunktionen HTML.

   ![](assets/offer_delivery_example_007.png)

1. Lägg in det andra erbjudandet.

   ![](assets/offer_delivery_example_008.png)

1. Klicka **[!UICONTROL Preview]** om du vill förhandsgranska dina erbjudanden i leveransen väljer du en mottagare som ska förhandsgranska erbjudandena allt eftersom de kommer att få dem.

   ![](assets/offer_delivery_example_009.png)

1. Spara leveransen och starta arbetsflödet för målinriktning.
1. Öppna leveransen och klicka på **[!UICONTROL Audit]** leveransflik: ser du att erbjudandemotorn har valt vilka erbjudanden som ska göras från de olika erbjudandena i katalogen.

   ![](assets/offer_delivery_example_010.png)

## Simulera erbjudanden {#perform-an-offer-simulation}

1. I **[!UICONTROL Profiles and Targets]** klickar du på **[!UICONTROL Simulations]** klicka på **[!UICONTROL Create]** -knappen.

   ![](assets/offer_simulation_001.png)

1. Välj en etikett och ange körningsinställningarna om det behövs.

   ![](assets/offer_simulation_example_002.png)

1. Spara simuleringen. Då öppnas den på en ny flik.

   ![](assets/offer_simulation_example_003.png)

1. Klicka på **[!UICONTROL Edit]** tabben **[!UICONTROL Scope]**.

   ![](assets/offer_simulation_example_004.png)

1. Välj den kategori som du vill simulera erbjudanden för.

   ![](assets/offer_simulation_example_005.png)

1. Välj det erbjudandeutrymme som ska användas för simuleringen.

   ![](assets/offer_simulation_example_006.png)

1. Ange giltighetsdatum. Du måste ange ett startdatum. Detta gör att erbjudandemotorfiltret kan erbjuda och välja vilka som är giltiga på ett visst datum.
1. Ange vid behov ett eller flera teman för att begränsa antalet erbjudanden till dem som innehåller nyckelordet i inställningarna.

   I vårt exempel **Resa** -kategorin innehåller två underkategorier med två separata teman. Vi vill simulera erbjudanden med **Kunder > 1 år** tema.

   ![](assets/offer_simulation_example_007.png)

1. Välj de mottagare som du vill ha som mål.

   ![](assets/offer_simulation_example_008.png)

1. Konfigurera antalet erbjudanden som ska skickas till varje mottagare.

   I vårt exempel kommer erbjudandemotorn att välja de tre erbjudandena med den högsta vikten för varje mottagare.

   ![](assets/offer_simulation_example_009.png)

1. Spara inställningarna och klicka sedan på **[!UICONTROL Start]** i **[!UICONTROL Dashboard]** för att köra simuleringen.

   ![](assets/offer_simulation_example_010.png)

1. När simuleringen är klar, se **[!UICONTROL Results]** för en detaljerad uppdelning av anbud per erbjudande.

   I vårt exempel har offertmotorn baserat uppdelningen av erbjudanden på tre anbud.

   ![](assets/offer_simulation_example_011.png)

1. Visa **[!UICONTROL Breakdown of offers by rank]** för att visa en lista över erbjudanden som valts ut av erbjudandemotorn.

   ![](assets/offer_simulation_example_012.png)

1. Om det behövs kan du ändra omfångsinställningarna och köra simuleringen igen genom att klicka på **[!UICONTROL Start simulation]**.

   ![](assets/offer_simulation_example_010.png)

1. Om du vill spara simuleringsdata använder du historik- eller exportfunktionerna som finns i rapporten.

   ![](assets/offer_simulation_example_013.png)
