---
product: campaign
title: Simuleringsomfång
description: Simuleringsomfång
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---

# Simuleringsomfång{#simulation-scope}

![](../../assets/v7-only.svg)

## Definition av omfattningen {#definition-of-the-scope}

Öppna **[!UICONTROL Scope]** för att välja inställningar.

Följande punkter är obligatoriska:

* Miljö eller erbjudandekategori.
* Erbjud utrymme.
* Kontaktdatum. Erbjudanden som inte är berättigade på kontaktdatumet beaktas inte.
* Målgrupp.

   Om du inte konfigurerar ett filter på målet kommer hela mottagartabellen att beaktas.

* Antal förslag som ska simuleras per mål.

   Mottagaren får så många förslag. Om du till exempel anger 5 får varje mottagare maximalt 5 erbjudandeförslag.

   ![](assets/offer_simulation_009.png)

Om du vill förfina de erbjudanden som ska beaktas vid simuleringen kan du lägga till ett eller flera teman (som anges i förväg i kategorierna).

Du kan också välja att utföra simuleringen för alla erbjudanden eller endast de som finns online. Vissa filter gör att du kan ändra markeringen om du vill.

>[!NOTE]
>
>Du måste ange ett kontaktdatum. Detta gör att interaktionsmotorn kan sortera erbjudandena i den valda miljön eller kategorin. Om inget datum är konfigurerat genereras ett fel vid simuleringen.

## Lägga till rapporteringsaxlar {#adding-reporting-axes}

Du kan förbättra simuleringsanalysen genom att lägga till rapportaxlar på målet eller själva erbjudandena via **[!UICONTROL Calculations]** -fliken.

Om du vill göra det klickar du på **[!UICONTROL Add]** och välj rätt fält. Axlar används för att beräkna simuleringen och visas i analysrapporten. Mer information finns i [Simuleringsspårning](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
