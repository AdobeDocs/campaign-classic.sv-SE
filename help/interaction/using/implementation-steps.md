---
product: campaign
title: Implementeringssteg
description: Implementeringssteg
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---

# Implementeringssteg{#implementation-steps}

## Konfigurerar interaktion {#configuring-interaction}

>[!NOTE]
>
>Följande steg bör utföras av en **Administrator**-profil och endast i designmiljöer.

1. Skapa användarprofiler. Mer information finns i [Operatorprofiler](../../interaction/using/operator-profiles.md).
1. Skapa en erbjudandemiljö genom att inrikta er på olika aspekter. Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Skapa typologiregler för varje miljö. Mer information finns i [Skapa och referera till en presentationsregel för erbjudande](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Skapa utrymme för varje miljö och konfigurera återgivningsfunktioner. Mer information finns i [Skapa erbjudandemellanslag](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Om utrymmet definieras av en enhetskanal i identifierat läge måste du ange de avancerade parametrarna för det här utrymmet.

1. Konfigurerar erbjudandemotorn för inkommande interaktioner för att presentera och uppdatera ett eller flera erbjudanden.

   De olika integreringslägena beskrivs i [Om inkommande kanaler](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >När ett utrymme skapas på den inkommande webbkanalen krävs även en konfiguration på den webbplats där erbjudandet ska visas.

## Hantera erbjudandekatalogen {#managing-the-offer-catalog-}

>[!NOTE]
>
>Följande steg bör utföras av en **Erbjudandehanterare**.

1. Skapa erbjudandekategorier i designmiljöer. Mer information finns i [Skapa erbjudandekategorier](../../interaction/using/creating-offer-categories.md).
1. Skapa erbjudanden i designmiljöer. Mer information finns i [Skapa ett erbjudande](../../interaction/using/creating-an-offer.md).
1. Godkänna och publicera erbjudanden på ett eller flera platser för att göra dem tillgängliga för leveranshanteraren. Mer information finns i [Godkänna och aktivera ett erbjudande](../../interaction/using/approving-and-activating-an-offer.md).

## Använda erbjudandekatalogen {#using-the-offer-catalog-}

>[!NOTE]
>
>Följande steg ska utföras av en **Delivery Manager**-profil. De kan bara redigera erbjudanden i live-miljöer.

1. Skapa en kampanj.
1. Referera till ett erbjudande i en kampanj eller en kampanjleverans. Mer information finns i [Om utgående kanaler](../../interaction/using/about-outbound-channels.md).
