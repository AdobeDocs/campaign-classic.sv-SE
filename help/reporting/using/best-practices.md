---
title: Bästa tillvägagångssätt för rapportering
seo-title: Bästa tillvägagångssätt för rapportering
description: Bästa tillvägagångssätt för rapportering
seo-description: null
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# Bästa tillvägagångssätt för rapportering{#best-practices-reporting}

## Analysera behov{#analyzing-needs}

Användningen av ett rapporteringsverktyg beror på mängden data som ska ändras, dess komplexitet och på vilken typ av rapportering som ska skapas.

Om du vill optimera framtagningen, användningen och varaktigheten av en rapport måste du ta en närmare titt på de behov du vill uppfylla. Den första analysen gör att du kan identifiera vilken typ av rapport som ska skapas och vilket som är det bästa. Så här skapar du rapporten:

1. Identifiera behovet

   Det första steget är att tydligt identifiera behovet av vad du vill visa i rapporten och vad målet är (övervakning, analys, dataexport osv.).

   Adobe Campaign har ett stort antal rapporttjänster. Det är viktigt att analysera behovet av att identifiera den lämpligaste funktionen.

   Du kan till exempel:

   * Utforska data i databasen och definiera mått (via [detta avsnitt](../../reporting/using/about-cubes.md)),
   * Lägg till indikatorer i en befintlig rapport (se [detta avsnitt](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Visa data i databasen (via [detta avsnitt](../../reporting/using/about-descriptive-analysis.md)),
   * Skapa en ny leveransrapport (se [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md)),
   * Exportera data från Adobe Campaign-databasen (via ett arbetsflöde, se [det här avsnittet](../../workflow/using/about-workflows.md)),
   * Skapa en pivottabell (se [det här avsnittet](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)),
   * Utforska aggregerade data (via [detta avsnitt](../../reporting/using/about-cubes.md)),
   * Använd en guide för att analysera data (via [det här avsnittet](../../reporting/using/about-descriptive-analysis.md)),
   * Analysera stora datavolymer (se [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md)) osv.

1. Identifiera målpopulationen

   Sedan måste ni ta reda på vem den rapport ni vill skapa är avsedd för, veta vilken typ av publik som kommer att se den och rapportvisningsläget (i en webbläsare, i Adobe Campaign, för ett visst objekt, för hela plattformen osv.).

   Du kan också skapa rapporter för:

   * Alla Adobe Campaign-operatörer,
   * Operatörer som endast har rätt att få tillgång till en marknadsföringskampanj,
   * En enda operatör för tillfälligt bruk.
   * Alla operatorer för webbåtkomst osv.
   Dessa överväganden måste också beakta de problem som är kopplade till åtkomsträttigheter och säkerhet.

1. Definiera innehållet

   Sedan måste du ta reda på vilken typ av data du vill visa: leveransindikatorer, rapporter om databasprofiler osv.

   Ni måste också känna till vilken typ av data det är (enkel, som ett resultat av en beräkning, signifikant osv.), dess plats (i Adobe Campaign, i ett tredjepartssystem), dess uppdateringsfrekvens för att definiera beräkningsfrekvensen (varje dag, varje vecka, direkt) samt dess volym.

   De problem som är kopplade till datavolymer och uppdateringar måste undersökas noggrant för att undvika problem med rapportvisningen, särskilt i fråga om tid. Därför rekommenderar vi att man skapar aggregat för att förberäkna vissa data utanför rapporten. Tabeller som innehåller spårnings- och leveransloggar kan innehålla miljontals poster: Detta innebär att data måste aggregeras via ett arbetsflöde för att användas i en rapport.

## Optimera rapportskapande{#optimizing-report-creation}

### Datavolym {#data-volume}

För att optimala prestanda ska kunna garanteras får mängden manipulerade data inte vara för stor.

Namn:

* Beräkningstiden för en rapport får inte överstiga 5 minuter.

   På samma sätt måste beräkningsmetoderna ändras under designfasen, med en liten datavolym, om rapportberäkningen överstiger 60 sekunder.

* När marknadsföringsanalys används får de manipulerade data inte överstiga 10 miljoner rader.

Vi rekommenderar också att man beräknar aggregat på natten och använder dessa aggregerade data direkt i rapporterna. Dessa aggregat måste skapas via dedikerade datahanteringsarbetsflöden (SQL-frågor).

Du kan också beräkna rapporter under natten och automatiskt skapa en historik som kan visas när som helst utan att överbelasta databasen.

### Frågor {#queries}

Vi rekommenderar att du använder SQL-frågor när det är möjligt och undviker JavaScript-efterbearbetning. Om det behövs kan du använda en skriptaktivitet i ett arbetsflöde och ta bort de data som används för beräkningen. Du kan också använda arkiverade data för att snabba upp bearbetningstiden.

I det här fallet bör följande syntax användas:

```
if(string(ctx@_historyId)!==""))
```

Frågor som gör att du kan samla in de data som visas i rapporterna får inte vara för komplexa, särskilt om de tillämpas på alla data i databasen. Om du vill förbättra prestandan kan det vara praktiskt att filtrera data innan du kör följande frågor: Detta innebär att beräkningen endast gäller en del av uppgifterna.

### Prestanda {#performances}

Med rekommendationerna ovan kan du optimera rapportberäkningen.

Adobe Campaign rekommenderar dessutom följande förbättringar:

* Studera datamodellen: indexerade fält måste huvudsakligen användas för att förbättra beräkningsformler.

   Om du snabbt vill hitta ett indexerat fält ska du titta på namnet på kolumnen i Adobe Campaign-gränssnittet: sorteringspilen stryks under med rött om fältet är indexerat.

* Kontrollera att rapporten är giltig i längden: datavolymen kan öka betydligt med tiden.

   På samma sätt kan mängden data som manipuleras under testfaserna skilja sig från den faktiska datavolymen i produktionen. Därför är testfaserna viktiga.

   Slutligen måste förseningar i samband med datarensning vara kända och vid behov anpassas för att underlätta datahanteringen.

### Exportera rapporter {#exporting-reports}

Rekommendationer som är specifika för export av rapporter beskrivs i [detta avsnitt](../../reporting/using/actions-on-reports.md#exporting-a-report).
