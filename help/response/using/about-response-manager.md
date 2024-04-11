---
product: campaign
title: Om svarshanteraren
description: Om svarshanteraren
feature: Campaigns
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 4%

---

# Kom igång med Campaign Response Manager{#about-response-manager}



Adobe Campaign erbjuder ett tillägg för Response Management som gör att ni kan mäta framgången och lönsamheten för marknadsföringskampanjer eller erbjuda erbjudanden över kommunikationskanaler: e-post, mobil, direktreklam osv.

## Hypotes {#hypothesis-concept}

Hypoeser kan konfigureras under en viss period från kontaktdatumet för att minska beteendet hos de som anges efter att ha fått en leverans. Dessa hypoteser bygger på en **transaktion** register som sparar inköp och information om dessa inköp.

Hypoesen är tidsbegränsad och kan tillämpas på en kontrollgrupp som ska jämföras med målpopulationen. Sammanfattande resultat från **indikatorer** som uppdateras automatiskt när beräkningen är klar. Den avkastning som är kopplad till hypoteserna kommer att beaktas i kampanjrapporterna.

Dessutom finns **rapporter** som ingår i Response Manager gör det möjligt att sammanfatta informationen som är kopplad till omsättningsökning, marginalberäkning samt avkastningen på leveransen eller erbjudandet.

Tack vare inköpsdetaljraderna kan du dessutom ange att dina hypoteser bara ska fokuseras på en viss produkt.

Efter en leverans som befordrar en artikel vill vi till exempel utvärdera de intäkter som genereras. Vi tillämpar hypotesen att alla mottagare som har köpt minst en artikel under månaden efter utlösandet av leveransen har reagerat på den här åtgärden. Svarshanteringen avgör, utifrån denna hypotes, vilka inköpsanbudsrader som ska tilldelas den. På grundval av detta blir det sedan möjligt att fastställa de resulterande intäkterna som summan av dessa rader.

>[!CAUTION]
>
>Svarshanteraren är en **[!UICONTROL Campaign]** alternativ. Kontrollera licensavtalet.

Du kan också beräkna alla reaktioner för hela hushållet med mottagaren som tog emot leveransen eller erbjudandet.

Varje hypotes är kopplad till en enda transaktionstabell. En leverans eller ett erbjudande kan vara kopplat till flera hypoteser.

## Implementeringssteg {#method}

Innan du börjar använda svarshanteraren bör du läsa [Konfiguration](configuration.md) och utföra de konfigurationer som krävs.

För att kunna inleda en hypotes om en leverans eller ett erbjudande måste ni definiera sammanhanget i en mall som ska användas för varje hypotes som ni skapar.

Använd följande process för att definiera och skapa mäthypoteser:

1. Definiera en hypotesmodell. [Läs mer](hypothesis-templates.md#creating-a-hypothesis-model)
1. Skapa en eller flera hypoteser för en befintlig leverans. [Läs mer](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   eller

   Skapa en eller flera hypoteser om erbjudanden. [Läs mer](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Kontrollera hypotesresultaten. [Läs mer](hypothesis-tracking.md)
1. Återlansera hypoteser om det behövs. [Läs mer](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
