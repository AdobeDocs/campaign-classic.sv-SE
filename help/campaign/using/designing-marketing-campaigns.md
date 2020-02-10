---
title: Utforma marknadsföringskampanjer
seo-title: Utforma marknadsföringskampanjer
description: Utforma marknadsföringskampanjer
seo-description: null
page-status-flag: never-activated
uuid: e0fd5df6-7516-4ca6-bbdf-243a264d0283
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
discoiquuid: a9eb6627-2e51-42d0-9b29-5b798bdf5b33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Utforma marknadsföringskampanjer{#designing-marketing-campaigns}

Med Adobe Campaign kan ni definiera, optimera, genomföra och analysera kommunikation och marknadsföringskampanjer. Adobe Campaign fungerar som en enhetlig order- och exekveringscentral för marknadsföringsstrategier. Mer information finns i [Få tillgång till kampanjer](../../campaign/using/accessing-campaigns.md) och [Konfigurera marknadsföringskampanjer](../../campaign/using/setting-up-marketing-campaigns.md).

Med modulen **Marketing Resource Management (MRM)** kan ni dessutom styra marknadsföringsåtgärder i ett samverkansbaserat läge genom att tillhandahålla fullständig hantering och realtidsspårning av de uppgifter, budgetar och marknadsföringsresurser som ingår. Med Marketing Resource Management kan ni optimera och reglera hanteringen av interna och externa processer, resurser och marknadsföringskampanjer samt relationer till tredje part (byråer, skrivare osv.). Mer information finns i [det här avsnittet](../../campaign/using/about-marketing-resource-management.md).

>[!NOTE]
>
>Mer information om huvudfunktionerna i Adobe Campaign finns i avsnittet [Komma igång](../../platform/using/about-adobe-campaign-classic.md) .\
>Funktioner för målgruppsanpassning, meddelandepersonalisering och meddelandeleverans i olika kanaler beskrivs i [det här avsnittet](../../delivery/using/communication-channels.md).

## Kärnkoncept {#core-concepts}

Följande koncept måste vara kända i samband med Campaign:

* **Campaign**

   En kampanj centraliserar alla element som hör till en marknadsföringskampanj: leveranser, regler för målinriktning, kostnader, exportfiler, relaterade dokument osv. Varje kampanj är kopplad till ett program.

   Mer information finns i [Lägga till en kampanj](../../campaign/using/setting-up-marketing-campaigns.md#adding-a-campaign).

* **Program**

   Med ett program kan du definiera marknadsföringsåtgärder för en kalenderperiod: lansering, kanvantning, lojalitet osv. Varje program innehåller kampanjer som är länkade till en kalender, som ger en övergripande bild.

* **Plan**

   Marknadsföringsplanen kan innehålla flera program. Den är kopplad till en kalenderperiod, har en tilldelad budget och kan även kopplas ihop med dokument och mål.

   Mer information finns i [Kampanjkalendern](../../campaign/using/accessing-marketing-campaigns.md#campaign-calendar).

* **Arbetsflöde**

   Ett kampanjarbetsflöde innehåller samma aktiviteter som för alla arbetsflöden, men är specifikt för kampanjen. Det gör att du kan skapa och konfigurera leveranser för alla tillgängliga kanaler.

   Mer information finns i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

* **Mål**

   I kampanjen, programmet eller planen kan ni ange en lista med mål. Dessa är kvantifierade värden som ska uppnås. I slutet av kampanjen, programmet eller planen kan ni med MRM-modulen jämföra målen och resultaten i dedikerade rapporter.

* **Leveransöversikt**

   En leveransdisposition är en strukturerad beskrivning av en leverans. Varje leverans kan referera till en leveransdisposition som t.ex. innehåller relaterade erbjudanden, dokument som ska bifogas eller en länk till butiker. Det går att referera till ett erbjudande i leveransen enligt den valda leveransdispositionen.

   Mer information finns i [Associera och strukturera resurser via en leveransöversikt](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).
