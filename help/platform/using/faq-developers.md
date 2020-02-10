---
title: Vanliga frågor
seo-title: Vanliga frågor
description: Vanliga frågor om Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# Utvecklare - frågor och svar {#dev-faq}

Adobe Campaign är en öppen lösning som är redo för anpassning och utveckling av avancerade applikationer.

## Vad är Campaign-datamodellen? {#what-is-the-campaign-data-model}

Adobe Campaign-databasens konceptuella datamodell består av en uppsättning inbyggda tabeller och deras interaktion. Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign, som kallas schema. Mer information om Adobe Campaign-scheman [finns i det här avsnittet](../../configuration/using/about-schema-edition.md).

[Klicka här om du vill veta mer om Campaign-datamodellen](https://helpx.adobe.com/campaign/kb/acc-datamodel.html).

Bästa tillvägagångssätt beskrivs [i den här artikeln](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).

## Hur arbetar man med Campaign-scheman? {#how-to-work-with-campaign-schemas-}

I Adobe Campaign används datamappningar för att:

* Definiera hur dataobjekt i programmet kopplas till underliggande databastabeller.
* Definiera länkar mellan olika dataobjekt i Campaign-programmet.
* Definiera och beskriv de enskilda fälten som ingår i varje objekt.

Läs mer om hur [tabeller och scheman kommer igång](../../configuration/using/about-schema-edition.md) för att förstå hur du arbetar med dataschema, utökar och anpassar Campaign efter dina behov.

## Hur använder man en anpassad mottagartabell? {#how-to-use-a-custom-recipient-table-}

Du kan skapa och implementera en mottagartabell som inte är standard i Campaign för att skicka meddelanden.

[Klicka här för mer information](../../configuration/using/about-custom-recipient-table.md)

## Vilka är de bästa sätten att definiera frågor i Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

Adobe Campaign-frågeredigeraren är ett kraftfullt verktyg för att utforska data och bygga segment.

Adobe Campaign-frågeverktyget finns på flera nivåer i programmet: för att skapa en målpopulation, segmentkunder, extrahera och filtrera spårningsloggar, byggfilter osv.

Du kan fråga Campaign-databasen med den generiska frågeredigeraren. **Den öppnas via** Verktyg > Allmän frågeredigerare... -menyn. Du kan extrahera information som lagras i en databas och ordna, gruppera, sortera osv. Användaren kan till exempel återställa mottagare som klickat mer än n gånger på länken i ett nyhetsbrev under en viss period. Med det här verktyget kan du samla in, sortera och visa resultat utifrån dina behov. Det här verktyget kombinerar alla Adobe Campaign-frågemöjligheter. Du kan till exempel skapa och spara begränsningsfilter. Det innebär att ett användarfilter som har skapats i den allmänna frågeredigeraren kan användas i rutan Fråga i ett målarbetsflöde, osv.

Frågor skapas med hjälp av fält i den valda tabellen eller med hjälp av en formel. De viktigaste principerna för att skapa en fråga i Campaign-databasen beskrivs [på den här sidan](../../platform/using/about-queries-in-campaign.md).

[Klicka här](../../workflow/using/query.md) om du vill identifiera redigeraren för Campaign-frågan.

## Hur importerar jag ett datapaket? {#how-can-i-import-a-data-package-}

Med Adobe Campaign kan ni exportera eller importera plattformskonfigurationen och data via ett paketsystem. Med datapaket kan enheter i Adobe Campaign-databasen visas med filer i XML-format. Varje entitet i ett paket representeras med alla dess data.

Principen med datapaket är att exportera en datakonfiguration och integrera den i ett annat Adobe Campaign-system.

[Klicka här](../../platform/using/working-with-data-packages.md) för att lära dig hur du arbetar med datapaket för att importera och exportera Campaign-konfigurationer.

## Var hittar jag listan över API:er för Campaign Classic? {#where-can-i-find-the-list-of-campaign-classic-apis}

Alla Campaign-API:er, inklusive deras fullständiga beskrivning, finns i den här [dedikerade dokumentationen](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).
