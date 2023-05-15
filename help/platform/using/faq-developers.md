---
product: campaign
title: Vanliga frågor och svar för utvecklare
description: Vanliga frågor och svar för utvecklare
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 97%

---

# Vanliga frågor och svar för utvecklare {#dev-faq}



Adobe Campaign är en öppen lösning som är redo för personalisering och avancerad utveckling av applikationer.

## Vad är datamodellen i Campaign? {#what-is-the-campaign-data-model}

Den konceptuella datamodellen av databasen i Adobe Campaign består av en uppsättning inbyggda tabeller och deras interaktion. Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den följer en grammatik som är specifik för Adobe Campaign och som kallas för ett schema. Se [det här avsnittet](../../configuration/using/about-schema-edition.md) för mer information om scheman i Adobe Campaign.

[Klicka här för att läsa mer om datamodellen i Campaign](https://helpx.adobe.com/se/campaign/kb/acc-datamodel.html).

Bästa praxis beskrivs [i den här artikeln](../../configuration/using/data-model-best-practices.md).

## Hur arbetar man med scheman i Campaign? {#how-to-work-with-campaign-schemas-}

I Adobe Campaign används datascheman för att:

* Definiera hur dataobjekt i programmet länkas till underliggande databastabeller.
* Definiera länkar mellan olika dataobjekt i programmet Campaign.
* Definiera och beskriva de enskilda fälten som ingår i varje objekt.

Läs mer i [Komma igång med tabeller och scheman](../../configuration/using/about-schema-edition.md) för att förstå hur du arbetar med datascheman samt utökar och anpassar Campaign efter dina behov.

## Hur använder man en anpassad mottagartabell? {#how-to-use-a-custom-recipient-table-}

Du kan skapa och implementera en icke-inbyggd mottagartabell i Campaign för att skicka meddelanden.

[Klicka här för att läsa mer](../../configuration/using/about-custom-recipient-table.md)

## Vad är bästa praxis för att definiera frågor i Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

Frågeredigeraren i Adobe Campaign är ett kraftfullt verktyg som låter dig utforska data och bygga segment.

Du kan hitta frågeverktyget i Adobe Campaign på flera nivåer i programmet. Du kan skapa en målgrupp, segmentera kunder, extrahera och filtrera spårningsloggar och bygga filter osv.

Du kan fråga databasen i Campaign med den generiska frågeredigeraren. Den öppnas via menyn **Verktyg > Allmän frågeredigerare ...**. Den låter dig extrahera information som finns lagrad i en databas och ordna, gruppera och sortera osv. Användaren kan till exempel hämta mottagare som har klickat mer än &quot;n&quot; gånger på länken i ett nyhetsbrev under en viss period. Det här verktyget låter dig samla in, sortera och visa resultat utifrån dina behov. Det här verktyget kombinerar alla frågemöjligheter i Adobe Campaign. Du kan till exempel skapa och spara begränsningsfilter. Det innebär att ett användarfilter som har skapats i den allmänna frågeredigeraren kan användas i frågeformuläret i ett arbetsflöde för målgrupper osv.

Frågor skapas med hjälp av fält i den valda tabellen eller med hjälp av en formel. De viktigaste principerna för att skapa en fråga med databasen i Campaign beskrivs [på den här sidan](../../platform/using/about-queries-in-campaign.md).

[Klicka här](../../workflow/using/query.md) för att lära dig om frågeredigeraren i Campaign.

## Hur importerar jag ett datapaket? {#how-can-i-import-a-data-package-}

Med Adobe Campaign kan du exportera eller importera plattformskonfigurationen och data via ett paketsystem. Med datapaket kan enheter i databasen i Adobe Campaign visas via filer i XML-format. Varje entitet i ett paket representeras med alla dess data.

Principen med datapaket är att exportera en datakonfiguration och integrera den i ett annat system i Adobe Campaign.

[Klicka här](../../platform/using/working-with-data-packages.md) för att lära dig hur du arbetar med datapaket för att importera och exportera konfigurationer i Campaign.

## Var hittar jag listan över API:er i Campaign Classic? {#where-can-i-find-the-list-of-campaign-classic-apis}

Alla API:er i Campaign inklusive deras fullständiga beskrivning finns i den här [dedikerade dokumentationen](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv).
