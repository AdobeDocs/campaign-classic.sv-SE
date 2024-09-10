---
product: campaign
title: Bästa praxis för rapportering
description: Bästa praxis för kampanjrapportering
feature: Reporting, Monitoring
badge: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 1%

---

# Rapportera bästa praxis{#best-practices-reporting}



## Analysera era behov{#analyzing-needs}

Användningen av ett rapporteringsverktyg beror på mängden data som ska ändras, dess komplexitet och på vilken typ av rapportering som ska skapas.

Om du vill optimera framtagningen, användningen och varaktigheten av en rapport måste du ta en närmare titt på de behov du vill uppfylla. Den första analysen gör att du kan identifiera vilken typ av rapport som ska skapas och vilket som är det bästa. Så här skapar du rapporten:

1. Identifiera behovet

   Det första steget är att tydligt identifiera behovet: vad du vill visa i din rapport och vad målet är (övervakning, analys, dataexport osv.).

   Adobe Campaign har ett stort antal rapporttjänster. Det är viktigt att analysera behovet av att identifiera den lämpligaste funktionen.

   Du kan till exempel:

   * Utforska data i databasen och definiera mått. Läs mer [i det här avsnittet](../../reporting/using/ac-cubes.md)
   * Lägg till indikatorer i en befintlig rapport. Läs mer [i det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md)
   * Visa data i databasen. Läs mer [i det här avsnittet](../../reporting/using/about-descriptive-analysis.md)
   * Skapa en ny leveransrapport. Läs mer [i det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Exportera data från Adobe Campaign-databasen (via ett arbetsflöde, se [det här avsnittet](../../workflow/using/about-workflows.md))
   * Skapa en pivottabell. Läs mer [i det här avsnittet](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * Utforska aggregerade data. Läs mer [i det här avsnittet](../../reporting/using/ac-cubes.md)
   * Använd en assistent för att analysera data. Läs mer [i det här avsnittet](../../reporting/using/about-descriptive-analysis.md)
   * Analysera stora datavolymer. Läs mer [i det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md)

1. Identifiera målpopulationen

   Sedan måste du ta reda på vem rapporten du vill skapa ska ha som mål, veta vilken typ av publik som ska visa den och rapportens visningsläge (i en webbläsare, i Adobe Campaign, för ett visst objekt, för hela plattformen osv.).

   Du kan också skapa rapporter för:

   * Alla Adobe Campaign-operatorer
   * Operatörer som endast har rätt att få tillgång till en marknadsföringskampanj,
   * En enda operatör för tillfälligt bruk.
   * Alla operatorer för webbåtkomst osv.

   Dessa överväganden måste också beakta de problem som är kopplade till åtkomsträttigheter och säkerhet.

1. Definiera innehållet

   Sedan måste ni ta reda på vilken typ av data ni vill visa: leveransindikatorer, rapporter om databasprofiler, osv.

   Du måste också känna till vilken typ av data det är (enkel, som ett resultat av en beräkning, signifikant osv.), dess plats (i Adobe Campaign, i ett tredjepartssystem), dess uppdateringsfrekvens för att definiera beräkningsfrekvensen (varje dag, varje vecka, varje gång) samt dess volym.

   De problem som är kopplade till datavolymer och uppdateringar måste undersökas noggrant för att undvika problem med rapportvisningen, särskilt i fråga om tid. Därför rekommenderar vi att man skapar aggregat för att förberäkna vissa data utanför rapporten. Tabeller som innehåller spårnings- och leveransloggar kan innehålla miljontals poster: det innebär att data måste samlas in via ett arbetsflöde för att användas i en rapport.

## Optimera rapportdesign{#optimizing-report-creation}

### Datavolym {#data-volume}

För att optimala prestanda ska kunna garanteras får mängden manipulerade data inte vara för stor.

Namn:

* Beräkningstiden för en rapport får inte överstiga 5 minuter.

  På samma sätt måste beräkningsmetoderna ändras under designfasen, med en liten datavolym, om rapportberäkningen överstiger 60 sekunder.

* Rapporteringsdata får inte överstiga 10 miljoner rader när modulen Marketing Analytics används.

Vi rekommenderar också att man beräknar aggregat på natten och använder dessa aggregerade data direkt i rapporterna. Dessa aggregat måste skapas via dedikerade datahanteringsarbetsflöden (SQL-frågor).

Du kan också beräkna rapporter under natten och automatiskt skapa en historik som kan visas när som helst utan att överbelasta databasen.

### Frågor {#queries}

Vi rekommenderar att du använder SQL-frågor när det är möjligt och undviker efterbearbetning av JavaScript. Om det behövs kan du använda en skriptaktivitet i ett arbetsflöde och ta bort de data som används för beräkningen. Du kan också använda arkiverade data för att snabba upp bearbetningstiden.

I det här fallet bör följande syntax användas:

```
if(string(ctx@_historyId)!==""))
```

Frågor som gör att du kan samla in de data som visas i rapporterna får inte vara för komplexa, särskilt om de tillämpas på alla data i databasen. För att förbättra prestandan kan det vara användbart att filtrera data innan du kör dessa frågor: detta innebär att beräkningen endast gäller en del av data.

### Prestanda {#performances}

Med rekommendationerna ovan kan du optimera rapportberäkningen.

Dessutom rekommenderar Adobe Campaign följande förbättringar:

* Arbeta med datamodellen: indexerade fält måste huvudsakligen användas för att förbättra beräkningsformler.

  Om du snabbt vill hitta ett indexerat fält ska du titta på namnet på kolumnen i Adobe Campaign-gränssnittet: sorteringspilen är röd om fältet är indexerat.

  Mer information om index finns i [det här avsnittet](../../configuration/using/data-model-best-practices.md#indexes).

* Se till att rapporten är skalbar: datavolymen kan öka avsevärt över tiden.

  På samma sätt kan mängden data som manipuleras under testfaserna skilja sig från den faktiska datavolymen i produktionen. Därför är testfaserna viktiga.

  Slutligen måste förseningar i samband med datarensning vara kända och vid behov anpassas för att underlätta datahanteringen.

  Mer information om rensning och datalagring finns i [det här avsnittet](../../configuration/using/data-model-best-practices.md#data-retention).

### Exportera rapporter {#exporting-reports}

Recommendations som är specifikt för att exportera rapporter beskrivs i [det här avsnittet](../../reporting/using/actions-on-reports.md#exporting-a-report).
