---
title: Om rapportverktyg i Adobe Campaign
seo-title: Om rapportverktyg i Adobe Campaign
description: Om rapportverktyg i Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: a8122c9e-60ba-4ef7-bc63-05d6cf16fad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: c5dad561-0708-4b7a-84a0-eb00beff58c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1719d6ac9643f0b3e9339037cf4d0f209d16340e

---


# Kom igång med rapporter {#about-adobe-campaign-reporting-tools}

Förutom [inbyggda rapporter](../../reporting/using/about-campaign-built-in-reports.md)kan ni med Adobe Campaign generera rapporter i olika sammanhang och för att tillgodose olika behov. Principer för användning och implementeringslägen beskrivs i detta dokument.

Adobe Campaign är inget specialiserat rapporteringsverktyg: rapporter som skapats i Adobe Campaign gör det i huvudsak möjligt för er att visa aggregerade data. Adobe Campaign-rapporter, som är avsedda att analysera och representera data, är inte utformade för databasexport.

Om du vill exportera data från Adobe Campaign-databasen måste du skapa ett arbetsflöde och använda en dataexportaktivitet. Mer information finns i [det här avsnittet](../../workflow/using/about-action-activities.md).

Adobe Campaign innehåller flera rapporteringsverktyg:

1. **Inbyggda rapporter**: Adobe Campaign erbjuder en uppsättning rapporter om leveranser, kampanjer, plattformsaktiviteter, valfria funktioner osv. Rapporterna finns tillgängliga via de olika funktioner som de avser. De kan anpassas efter dina specifika behov.

   Mer information finns i [det här avsnittet](../../reporting/using/about-campaign-built-in-reports.md).

1. **Beskrivande dataanalys**: Adobe Campaign är ett visuellt verktyg för att producera statistik om data i databasen. Du kan skapa beskrivande analysrapporter med en dedikerad guide och anpassa innehållet och layouten efter behov.

   Mer information finns i [det här avsnittet](../../reporting/using/about-descriptive-analysis.md).

1. **Personaliserade rapporter**: Med Adobe Campaign kan ni skapa rapporter om data i databasen. När de har skapats görs de tillgängliga i rätt sammanhang.

   Beroende på hur komplexa frågorna, beräkningarna och volymerna är kan de data som analyseras i dessa rapporter samlas in via en fråga och sedan aggregeras i en lista (datahanteringsarbetsflöde) eller i en kub (med hjälp av Marketing Analytics). Den visas i form av en pivottabell eller en grupplista.

   Mer information finns i [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Analysrapporter**: Marknadsföringsanalys möjliggör intuitiv datautforskning.

   Mer information finns i [det här avsnittet](../../reporting/using/about-cubes.md).

>[!CAUTION]
>
>För enkel visning och hantering, samt effektiv export, får rapporter inte innehålla fler än 1 000 rader.