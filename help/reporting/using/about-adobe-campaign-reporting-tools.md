---
product: campaign
title: Om Adobe Campaign rapporteringsverktyg
description: Analysera framgångarna med dina kampanjer i inbyggda eller anpassade rapporter
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 14%

---

# Kom igång med rapporter {#about-adobe-campaign-reporting-tools}



Förutom [inbyggda rapporter](../../reporting/using/about-campaign-built-in-reports.md)Med Adobe Campaign kan du generera rapporter i olika sammanhang och för att uppfylla olika behov. Principer för användning och implementeringslägen beskrivs i detta dokument.

Adobe Campaign är inget specialiserat rapporteringsverktyg: rapporter som skapats i Adobe Campaign gör det i huvudsak möjligt att visa aggregerade data. Adobe Campaign-rapporter, som används för att analysera och representera data, är inte utformade för databasexport.

Om du vill exportera data från Adobe Campaign-databasen måste du skapa ett arbetsflöde och använda en dataexportaktivitet. Mer information om detta finns i [det här avsnittet](../../workflow/using/about-action-activities.md).

Adobe Campaign har flera rapportverktyg:

1. **Inbyggda rapporter**: Adobe Campaign erbjuder en uppsättning rapporter om leveranser, kampanjer, plattformsaktiviteter, valfria funktioner etc. Rapporterna finns tillgängliga via de olika funktioner som de avser. De kan anpassas efter dina specifika behov.

   Mer information om detta finns i [det här avsnittet](../../reporting/using/about-campaign-built-in-reports.md).

1. **Beskrivande dataanalys**: Adobe Campaign tillhandahåller ett visuellt verktyg för att producera statistik om data i databasen. Du kan skapa beskrivande analysrapporter med en dedikerad guide och anpassa innehållet och layouten efter behov.

   Mer information om detta finns i [det här avsnittet](../../reporting/using/about-descriptive-analysis.md).

1. **Personaliserade rapporter**: Med Adobe Campaign kan du skapa rapporter om data i databasen. När de har skapats görs de tillgängliga i rätt sammanhang.

   Beroende på hur komplexa frågorna, beräkningarna och volymerna är kan de data som analyseras i dessa rapporter samlas in via en fråga och sedan aggregeras i en lista (datahanteringsarbetsflöde) eller i en kub (med hjälp av Marketing Analytics). Den visas i form av en pivottabell eller en grupplista.

   Mer information om detta finns i [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md).

1. **Analysrapporter**: Marknadsföringsanalys möjliggör intuitiv datautforskning.

   Mer information om detta finns i [det här avsnittet](../../reporting/using/ac-cubes.md).

>[!CAUTION]
>
>För enkel visning och hantering, samt effektiv export, får rapporter inte innehålla fler än 1 000 rader.
