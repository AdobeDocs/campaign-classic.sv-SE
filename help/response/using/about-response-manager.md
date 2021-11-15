---
product: campaign
title: Om responshanteraren
description: Om responshanteraren
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 5%

---

# Kom igång med Campaign Response Manager{#about-response-manager}

![](../../assets/v7-only.svg)

Adobe Campaign erbjuder ett tillägg för Response Management som gör att ni kan mäta framgången och lönsamheten för marknadsföringskampanjer eller erbjuda erbjudanden över olika kommunikationskanaler: e-post, mobil, direktreklam osv.

## Hypotes {#hypothesis-concept}

Hypoeser kan konfigureras under en viss period från kontaktdatumet för att minska beteendet hos de som anges efter att ha fått en leverans. Hypoteserna baseras på en **transaktion**-tabell som sparar inköp och information om dessa inköp.

Hypoesen är tidsbegränsad och kan tillämpas på en kontrollgrupp som ska jämföras med målpopulationen. Hypoesresultat tillhandahålls av **indikatorer** som uppdateras automatiskt när beräkningen är klar. Den avkastning som är kopplad till hypoteserna kommer att beaktas i kampanjrapporterna.

Med **rapporterna** från Response Manager kan du också sammanfatta informationen som är kopplad till omsättningsökning, marginalberäkning samt avkastningen på leveransen eller erbjudandet.

Tack vare inköpsdetaljraderna kan du dessutom ange att dina hypoteser bara ska fokuseras på en viss produkt.

Efter en leverans som befordrar en artikel vill vi till exempel utvärdera de intäkter som genereras. Vi tillämpar hypotesen att alla mottagare som har köpt minst en artikel under månaden efter utlösandet av leveransen har reagerat på den här åtgärden. Svarshanteringen avgör, utifrån denna hypotes, vilka inköpsanbudsrader som ska tilldelas den. På grundval av detta blir det sedan möjligt att fastställa de resulterande intäkterna som summan av dessa rader.

>[!CAUTION]
>
>Svarshanteraren är ett **[!UICONTROL Campaign]**-alternativ. Kontrollera licensavtalet.

Du kan också beräkna alla reaktioner för hela hushållet med mottagaren som tog emot leveransen eller erbjudandet.

Varje hypotes är kopplad till en enda transaktionstabell. En leverans eller ett erbjudande kan vara kopplat till flera hypoteser.

## Implementeringssteg {#method}

Innan du börjar använda Svarshanteraren ska du läsa [Konfiguration](configuration.md) och utföra de nödvändiga konfigurationerna.

För att kunna inleda en hypotes om en leverans eller ett erbjudande måste ni definiera sammanhanget i en mall som ska användas för varje hypotes som ni skapar.

Använd följande process för att definiera och skapa mäthypoteser:

1. Definiera en hypotesmodell. [Läs mer](hypothesis-templates.md#creating-a-hypothesis-model)
1. Skapa en eller flera hypoteser för en befintlig leverans. [Läs mer](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   eller

   Skapa en eller flera hypoteser om erbjudanden. [Läs mer](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Kontrollera hypotesresultaten. [Läs mer](hypothesis-tracking.md)
1. Återlansera hypoteser om det behövs. [Läs mer](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)