---
product: campaign
title: Presentationsregler
description: Presentationsregler
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: f9dd9ad6-48da-4a80-9405-109a433a1ed5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---

# Presentationsregler{#presentation-rules}

![](../../assets/v7-only.svg)

## Skapa en presentationsregel {#creating-a-presentation-rule}

I vår databas finns flera reseerbjudanden för Europa, Afrika, USA och Kanada. Vi vill skicka erbjudanden för en resa till Kanada, men om mottagaren vägrar skicka den här typen av erbjudande vill vi inte skicka det till dem igen

Vi ska konfigurera vår regel så att resan till Kanada endast erbjuds en gång per mottagare och inte erbjuds igen om den avvisas.

1. Gå till noden **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** i Adobe Campaign-trädet.
1. Skapa en ny **[!UICONTROL Offer presentation]**-typregel.

   ![](assets/offer_typology_example_001.png)

1. Ändra vid behov etiketten och beskrivningen.

   ![](assets/offer_typology_example_002.png)

1. Välj alternativet **[!UICONTROL All channels]** om du vill utöka regeln till alla kanaler.

   ![](assets/offer_typology_example_003.png)

1. Klicka på länken **[!UICONTROL Edit expression]** och välj noden **[!UICONTROL Category]** som ett uttryck.

   ![](assets/offer_typology_example_004.png)

1. Välj den kategori som matchar ditt reseerbjudande för Kanada och klicka på **[!UICONTROL OK]** för att stänga frågefönstret.

   ![](assets/offer_typology_example_005.png)

1. På fliken **[!UICONTROL Offer presentation]** väljer du samma dimensioner som de som konfigurerats i miljön.

   ![](assets/offer_typology_example_006.png)

1. Ange den period under vilken regeln ska gälla.

   ![](assets/offer_typology_example_007.png)

1. Begränsa erbjudandet till ett så att mottagare som redan har avvisat en resa till Kanada inte får ett liknande erbjudande.

   ![](assets/offer_typology_example_008.png)

1. Välj filtret **[!UICONTROL Offers for the same category]** om du vill exkludera alla erbjudanden från kategorin **Kanada**.

   ![](assets/offer_typology_example_020.png)

1. Välj filtret **[!UICONTROL Rejected propositions]** om du bara vill ta med förslag som avvisats av mottagaren.

   ![](assets/offer_typology_example_021.png)

1. Välj de mottagare som den här regeln gäller för.

   I vårt exempel väljer vi **Vanliga resenärer** mottagare.

   ![](assets/offer_typology_example_009.png)

1. Referera regeln i en erbjudandetypologi.

   ![](assets/offer_typology_example_013.png)

1. Gå till erbjudandemiljön (**Miljö - mottagare** i det här fallet) och referera till den nya typologin som just skapats med listrutan på fliken **[!UICONTROL Eligibility]**.

   ![](assets/offer_typology_example_014.png)

## Använda presentationsregeln {#applying-the-presentation-rule}

Här är ett programexempel på den typologiregel som skapades tidigare.

Vi vill skicka ett första erbjudande som tillhör kategorin Kanada. Om någon av mottagarna avvisar erbjudandet kommer det inte att erbjudas igen.

1. I mappen **Vanliga resenärer** mottagare väljer du en av profilerna för att kontrollera de erbjudanden som de är berättigade till: klicka på fliken **[!UICONTROL Propositions]** och sedan på fliken **[!UICONTROL Preview]**.

   I vårt exempel är **Tim Ramsey** berättigad till ett erbjudande som ingår i kategorin **Amerika**.

   ![](assets/offer_typology_example_015.png)

1. Börja med att skapa en e-postleverans som riktar sig till dina **återkommande resenärer**-mottagare med erbjudanden.
1. Välj parametrarna för anropet till erbjudandemotorn.

   I vårt exempel väljs kategorin **Resa i Amerika**, som innehåller underkategorierna **Kanada** och **USA**.

   ![](assets/offer_typology_example_016.png)

1. Lägg in erbjudandena i meddelandetexten och skicka leveransen. Mer information finns i [Om utgående kanaler](../../interaction/using/about-outbound-channels.md).

   Mottagaren har fått det erbjudande som de är berättigade till.

1. Mottagaren avvisade erbjudandet från Kanada, vilket visas i offerthistoriken.

   ![](assets/offer_typology_example_018.png)

1. Kontrollera de erbjudanden som de nu är berättigade till.

   Vi ser att inga erbjudanden för Kanada har valts ut.

   ![](assets/offer_typology_example_019.png)

**Relaterat ämne**

* [Hantera erbjudanden och styr redundansen över alla kanaler](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Manageoffersandcontrolredundancyacrosschannels)
