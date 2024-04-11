---
product: campaign
title: Presentationsregler
description: Presentationsregler
feature: Interaction, Offers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# Presentationsregler{#presentation-rules}



## Skapa en presentationsregel {#creating-a-presentation-rule}

I vår databas finns flera reseerbjudanden för Europa, Afrika, USA och Kanada. Vi vill skicka erbjudanden för en resa till Kanada, men om mottagaren vägrar skicka den här typen av erbjudande vill vi inte skicka det till dem igen

Vi kommer att konfigurera vår regel så att resan till Kanada endast erbjuds en gång per mottagare och inte erbjuds igen om den avvisas.

1. Gå till Adobe Campaign **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** nod.
1. Skapa ett nytt **[!UICONTROL Offer presentation]** typregel.

   ![](assets/offer_typology_example_001.png)

1. Ändra vid behov etiketten och beskrivningen.

   ![](assets/offer_typology_example_002.png)

1. Välj **[!UICONTROL All channels]** om du vill utöka regeln till alla kanaler.

   ![](assets/offer_typology_example_003.png)

1. Klicka på **[!UICONTROL Edit expression]** länk och välj **[!UICONTROL Category]** som ett uttryck.

   ![](assets/offer_typology_example_004.png)

1. Välj den kategori som matchar ditt reseerbjudande för Kanada och klicka på **[!UICONTROL OK]** för att stänga frågefönstret.

   ![](assets/offer_typology_example_005.png)

1. I **[!UICONTROL Offer presentation]** väljer du samma dimensioner som de som har konfigurerats i miljön.

   ![](assets/offer_typology_example_006.png)

1. Ange den period under vilken regeln ska gälla.

   ![](assets/offer_typology_example_007.png)

1. Begränsa erbjudandet till ett så att mottagare som redan har avvisat en resa till Kanada inte får ett liknande erbjudande.

   ![](assets/offer_typology_example_008.png)

1. Välj **[!UICONTROL Offers for the same category]** filtrera för att exkludera alla erbjudanden från **Kanada** kategori.

   ![](assets/offer_typology_example_020.png)

1. Välj **[!UICONTROL Rejected propositions]** filtrera så att endast förslag som avvisats av mottagaren beaktas.

   ![](assets/offer_typology_example_021.png)

1. Välj de mottagare som regeln gäller för.

   I vårt exempel väljer vi **Täta resenärer** mottagare.

   ![](assets/offer_typology_example_009.png)

1. Referera regeln i en erbjudandetypologi.

   ![](assets/offer_typology_example_013.png)

1. Gå till erbjudandemiljön, (**Miljö - mottagare** i det här fallet) och hänvisa till den nya typologi som just skapats med listrutan i **[!UICONTROL Eligibility]** -fliken.

   ![](assets/offer_typology_example_014.png)

## Använda presentationsregeln {#applying-the-presentation-rule}

Här är ett programexempel på den typologiregel som skapades tidigare.

Vi vill skicka ett första erbjudande som tillhör kategorin Kanada. Om någon av mottagarna avvisar erbjudandet kommer det inte att erbjudas igen.

1. I **Täta resenärer** väljer du en av profilerna för att se vilka erbjudanden de är berättigade till: klicka på **[!UICONTROL Propositions]** -fliken och sedan **[!UICONTROL Preview]** -fliken.

   I vårt exempel **Tim Ramsey** är berättigade till ett erbjudande som ingår i **Amerika** kategori.

   ![](assets/offer_typology_example_015.png)

1. Börja med att skapa en e-postleverans som riktar sig till **Täta resenärer** mottagare med erbjudanden.
1. Välj parametrarna för anropet till erbjudandemotorn.

   I vårt exempel **Resor i Amerika** -kategorin väljs, som innehåller **Kanada** och **Amerikas förenta stater** underkategorier.

   ![](assets/offer_typology_example_016.png)

1. Lägg in erbjudandena i meddelandets brödtext och skicka leveransen. Mer information finns i [Om utgående kanaler](../../interaction/using/about-outbound-channels.md).

   Mottagaren har fått det erbjudande som de är berättigade till.

1. Mottagaren avvisade erbjudandet från Kanada, vilket visas i offerthistoriken.

   ![](assets/offer_typology_example_018.png)

1. Kontrollera de erbjudanden som de nu är berättigade till.

   Vi ser att inga erbjudanden för Kanada har valts ut.

   ![](assets/offer_typology_example_019.png)
