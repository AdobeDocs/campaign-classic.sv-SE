---
title: Om svarshanteraren
seo-title: Om svarshanteraren
description: Om svarshanteraren
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Om svarshanteraren{#about-response-manager}

## Mål {#objectives}

Adobe Campaign erbjuder en svarshanteringsapplikation (Response Manager) som gör det möjligt att mäta framgången och lönsamheten för marknadsföringskampanjer eller erbjuda förslag för alla kommunikationskanaler (e-post, mobil, telefon, direktreklam, fax, byrå, osv.).

## Hyposterkoncept {#hypothesis-concept}

Hypoeser kan konfigureras under en viss period från kontaktdatumet för att minska beteendet hos de som anges efter att ha fått en leverans. Hypoteserna baseras på ett **transaktionsregister** som sparar inköp och information om dessa inköp.

Hypoesen är tidsbegränsad och kan tillämpas på en kontrollgrupp som ska jämföras med målpopulationen. Hypoesresultat tillhandahålls av **indikatorer** som uppdateras automatiskt när beräkningen är klar. Den avkastning som är kopplad till hypoteserna kommer att beaktas i kampanjrapporterna.

Med **rapporterna** från Response Manager kan du också sammanfatta informationen som är kopplad till omsättningsökning, marginalberäkning samt avkastningen på leveransen eller erbjudandet.

Tack vare inköpsdetaljraderna kan du dessutom ange att dina hypoteser bara ska fokuseras på en viss produkt.

Efter en leverans som befordrar en artikel vill vi till exempel utvärdera de intäkter som genereras. Vi tillämpar hypotesen att alla mottagare som har köpt minst en artikel under månaden efter utlösandet av leveransen har reagerat på den här åtgärden. Svarshanteringen avgör, utifrån denna hypotes, vilka inköpsanbudsrader som ska tilldelas den. På grundval av detta blir det sedan möjligt att fastställa de resulterande intäkterna som summan av dessa rader.

>[!CAUTION]
>
>Svarshanteraren är ett **[!UICONTROL Campaign]** alternativ. Kontrollera licensavtalet.

Du kan också beräkna alla reaktioner för hela hushållet med mottagaren som tog emot leveransen eller erbjudandet.

Varje hypotes är kopplad till en enda transaktionstabell. En leverans eller ett erbjudande kan vara kopplat till flera hypoteser.

## Metod {#method}

Innan du börjar använda Response Manager ska du läsa [Konfiguration](../../campaign/using/configuration.md) och utföra de nödvändiga konfigurationerna.

För att kunna inleda en hypotes om en leverans eller ett erbjudande måste ni definiera sammanhanget i en mall som ska användas för varje hypotes som ni skapar.

Använd följande process för att definiera och skapa mäthypoteser:

1. Definiera en hypotesmodell. Se [Skapa en hypotesmodell](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Skapa en eller flera hypoteser för en befintlig leverans. Se [Referera till en hypotes i en kampanjleverans](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   eller

   Skapa en eller flera hypoteser om erbjudanden. Se [Skapa en hypotes om ett erbjudande](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Kontrollera hypotesresultaten. Se [Avstavningsspårning](../../campaign/using/hypothesis-tracking.md).
1. Återlansera hypoteser om det behövs. Se [Skapa en hypotes direkt vid leverans](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

