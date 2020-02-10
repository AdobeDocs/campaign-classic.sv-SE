---
title: Använda guiden för beskrivande analys
seo-title: Använda guiden för beskrivande analys
description: Använda guiden för beskrivande analys
seo-description: null
page-status-flag: never-activated
uuid: 30554909-4b91-46ff-bd8d-fa57ab6304f9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 18ba04d9-7bab-4eea-8dbb-6c2c138c5293
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Använda guiden för beskrivande analys{#using-the-descriptive-analysis-wizard}

Använd den dedikerade guiden för att skapa en beskrivande analysrapport. Konfigurationen beror på vilka data som ska analyseras och på önskad återgivning.

## Analyserar data i databasen {#analyzing-data-in-the-database}

Den beskrivande analysguiden kan startas via **[!UICONTROL Tools > Descriptive analysis]** menyn: I det här fallet gäller analysen mottagare som standard (**nms:receive**). Det gäller alla data i Adobe Campaign-databasen.

![](assets/reporting_descriptive_wz_launch.png)

Om du vill analysera en annan tabell än standardmottagarna en (**nms:receiver**) klickar du på **[!UICONTROL Advanced settings...]** länken i det sista steget i guiden och väljer den tabell som matchar dina inställningar, i det här fallet **cus:individual**:

![](assets/reporting_descriptive_other_schema.png)

Om du vill producera statistik för en del av data kan du definiera ett filter: Om du vill göra det klickar du på **[!UICONTROL Advanced settings...]** länken och definierar filtret som ska användas enligt nedan:

![](assets/reporting_descriptive_wz_filter.png)

Analysen gäller endast mottagare som är 16 år eller äldre och som bor i London.

## Analysera en datauppsättning {#analyzing-a-set-of-data}

Du kan använda den beskrivande analysguiden i ett annat sammanhang: en lista, en arbetsflödesövergång, en eller flera leveranser, ett urval av mottagare osv.

Det är tillgängligt via flera noder i Adobe Campaign-trädet som pekar på mottagartabellen.

Öppna den beskrivande analysguiden genom att markera objekt och högerklicka. Endast markerade data analyseras.

![](assets/reporting_descriptive_from_recipients.png)

* För en uppsättning **mottagare** väljer du vilka mottagare som ska analyseras, högerklickar och väljer **[!UICONTROL Actions > Explore...]** enligt ovan. Om ett filter används i listan med mottagare analyseras bara dess innehåll.

   Om du vill markera alla mottagare i mappen eller det aktuella filtret använder du kortkommandot CTRL+A. Detta innebär att även mottagare som inte visas markeras.

   Ett exempel på en beskrivande analys av mottagare finns i: Kvalitativ [dataanalys](../../reporting/using/use-cases.md#qualitative-data-analysis).

* Placera markören på en övergång som pekar mot mottagartabellen i ett **arbetsflöde**, högerklicka och välj **[!UICONTROL Analyze target]**. Mer information finns i exemplet när du [analyserar ett övergångsmål i ett arbetsflöde](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* För **listor** väljer du en eller flera listor och använder samma process som för mottagare.
* I samband med en **leverans** väljer du de leveranser vars mål du vill analysera, högerklickar och väljer **[!UICONTROL Actions > Explore the target]** enligt nedan:

   ![](assets/reporting_descriptive_from_deliveries.png)

   Här finns exempel på beskrivande analyser av leveranser: [Analysera en population](../../reporting/using/use-cases.md#analyzing-a-population) och här: Analyserar loggar för [mottagarspårning](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs).

## Konfigurera den kvalitativa distributionsmallen {#configuring-the-qualitative-distribution-template}

Med **[!UICONTROL Qualitative distribution]** mallen kan du skapa statistik för alla typer av data (t.ex. företagsnamn, e-postdomän).

Konfigurationsalternativen som är tillgängliga för en rapport som skapas via **[!UICONTROL Qualitative distribution]** mallen beskrivs i [Visa data i tabellen](#displaying-data-in-the-table). Ett fullständigt exempel finns i [Analysera en population](../../reporting/using/use-cases.md#analyzing-a-population).

När du använder den beskrivande analysguiden för att analysera dina data, beror de tillgängliga alternativen på de valda inställningarna. Dessa beskrivs nedan.

### Databindning {#data-binning}

När du väljer vilka variabler som ska visas kan du definiera databindning, d.v.s. konfigurera grupperingskriterier för de markerade data.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>När det fält som berörs av beräkningen beräknas med hjälp av ett aggregat, bör du kontrollera **[!UICONTROL The data is already aggregated]** att resultatet blir bättre.

Alternativen varierar beroende på fältets innehåll:

* **[!UICONTROL None]** : Med det här alternativet kan du visa alla värden som är tillgängliga för variabeln, utan bindning.

   >[!CAUTION]
   >
   >Detta alternativ bör användas med försiktighet: det kan ha stor inverkan på rapporten och på datorns prestanda.

* **[!UICONTROL Auto]** : Med det här alternativet kan du visa de n som visas oftast. De beräknas automatiskt och var och en representerar en procentandel av variablerna jämfört med antalet behållare. För numeriska värden genererar Adobe Campaign automatiskt n klasser att sortera data i.
* **[!UICONTROL Manual]** : det här alternativet fungerar som **[!UICONTROL Auto]** alternativ, förutom att du kan ange dessa värden manuellt. Det gör du genom att klicka på **[!UICONTROL Add]** knappen till höger om värdetabellen.

   Värdena kan initieras automatiskt av Adobe Campaign före personalisering: Om du vill göra det anger du antalet behållare som du vill generera och klickar på **[!UICONTROL Initialize with]** länken enligt nedan:

   ![](assets/reporting_descriptive_initialize.png)

   Anpassa sedan innehållet efter dina behov:

   ![](assets/reporting_descriptive_initialize_perso.png)

   Beroende på den önskade precisionsnivån kan fält som innehåller datum grupperas efter tid, dag, månad, år osv.

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** : I kan du skapa grupper med värden när det gäller numeriska värden. Med en modulo med värdet 10 kan du till exempel skapa ett värdeintervall som ändras tio gånger tio.

   ![](assets/reporting_descriptive_initialize_modulo.png)

   I det här exemplet kan du visa uppdelningen av mottagare per åldersgrupp.

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Visa data i tabellen {#displaying-data-in-the-table}

Använd verktygsfältet för att anpassa visningen av variabler i tabellen: ta bort en kolumn, visa data på rader i stället för i kolumner, flytta en kolumn till vänster eller höger, visa eller ändra värdeberäkning.

![](assets/s_ncs_user_report_wizard_toolbar.png)

I fönstrets övre del kan du välja visningsinställningar.

Du kan visa eller dölja namnet på statistiken och delsummorna och välja statistikens orientering. Mer information finns i Visningsinställningar för [analysrapporter](../../reporting/using/processing-a-report.md#analysis-report-display-settings).

### Visa data i diagrammet {#displaying-data-in-the-chart}

I det första steget i guiden för beskrivande analys kan du välja att endast visa data i diagramformuläret, utan någon tabell. I det här fallet måste variabelval göras när bilden konfigureras. Du måste först välja antalet variabler som ska visas och välja fälten från den relevanta databasen.

![](assets/s_ncs_user_report_wizard_023.png)

Välj sedan önskad diagramtyp.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>Du kan visa variablerna i ett diagram och i en tabell samtidigt. Det gör du genom att ange variablerna i **[!UICONTROL Table configuration]** fönstret. Klicka **[!UICONTROL Next]** och välj diagramtyp i diagramkonfigurationsfönstret. Om deldimensioner definieras i tabellen visas de inte i diagrammet.

Klicka på **[!UICONTROL Variants]** länken om du vill ändra diagramegenskaperna.

![](assets/reporting_descriptive_graphe_options.png)

Vilka alternativ som visas beror på vilken typ av diagram som är vald. Mer information finns på [den här sidan](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### Statistikberäkning {#statistics-calculation}

Med guiden för beskrivande analys kan du beräkna flera typer av statistik för data. Som standard konfigureras bara ett enkelt antal.

Klicka **[!UICONTROL Add]** för att skapa en ny statistik.

![](assets/reporting_descriptive_create_stat.png)

Följande åtgärder är möjliga:

* **[!UICONTROL Count]** att räkna alla värden som inte är null i det fält som ska aggregeras, inklusive dubblettvärden (i det aggregerade fältet),
* **[!UICONTROL Average]** för att beräkna medelvärdet av värdena i ett numeriskt fält,
* **[!UICONTROL Minimum]** beräkna det minsta värdet i ett numeriskt fält,
* **[!UICONTROL Maximum]** för att beräkna det maximala värdet för ett numeriskt fält,
* **[!UICONTROL Sum]** beräkna summan av värdena i ett numeriskt fält,
* **[!UICONTROL Standard deviation]** för att beräkna hur de returnerade värdena fördelas runt genomsnittet,
* **[!UICONTROL Row percentage distribution]** för att beräkna förhållandet mellan värdet i en kolumn och värdet i en rad (endast tillgängligt för tabeller),
* **[!UICONTROL Column percentage distribution]** för att beräkna förhållandet mellan värdet i en rad och värdet i en kolumn (endast tillgängligt för tabeller),
* **[!UICONTROL Total percentage distribution]** beräkna fördelningen av de mottagare som berörs av värdena,

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** för att skapa en anpassad operator (endast tillgänglig för tabeller). I **[!UICONTROL User function]** fältet kan du ange den beräkning som ska användas för data.

   Exempel: Beräkna det genomsnittliga inköpsbeloppet per kund baserat på land och ursprung

   ![](assets/report_compute_data_sample1.png)

   Om du vill visa ovanstående information i en tabell måste du skapa ett beräkningsfält för lagring av det genomsnittliga inköpsbeloppet per kund.

   Så här gör du:

   1. Beräkna inköpssumman.

      ![](assets/report_compute_data_sample2.png)

   1. Den här statistiken visas inte i tabellen. Du måste avmarkera **[!UICONTROL Display in the table]** alternativet på **[!UICONTROL Advanced]** fliken.

      ![](assets/report_compute_data_sample3.png)

   1. Skapa en ny **[!UICONTROL Calculated field]** typstatistik och ange följande formel i **[!UICONTROL User function]** fältet: **@purchase/@count**.

      ![](assets/report_compute_data_sample4.png)

### Visa rapporten {#displaying-the-report}

I det sista steget i guiden kan du visa rapporten, dvs. tabellen eller diagrammet som de har konfigurerats.

När rapporten innehåller en tabell färgas resultatcellen för beräkning. Ju högre resultat, desto intensivare färg.

![](assets/report_compute_data_sample1.png)

Det går att ändra resultatlayouten. Om du vill göra det högerklickar du på variabeln och väljer indata på snabbmenyn.

![](assets/s_ncs_user_report_wizard_029.png)

När rapporten innehåller ett diagram kan du filtrera den visade informationen med etiketterna för teckenförklaringen: klicka på en etikett för att aktivera/inaktivera visning i diagrammet.

![](assets/report_display_data_in_graph.png)

## Konfigurera den kvantitativa distributionsmallen {#configuring-the-quantitative-distribution-template}

Om du vill generera en beskrivande analys själv väljer du alternativet **Ny beskrivande analys i en mall** om det inte är inställt som standard.

Den **[!UICONTROL Quantitative distribution]** mall som gör att du kan generera statistik om data som kan mätas eller räknas (t.ex. fakturabelopp, mottagarnas ålder).

Konfigurationsläget för en analysrapport som skapas via **[!UICONTROL Quantitative distribution]** mallen beskrivs i ett implementeringsexempel [Kvantitativ dataanalys](../../reporting/using/use-cases.md#quantitative-data-analysis).

De alternativ som är tillgängliga när du skapar en kvantitativ rapport med hjälp av den beskrivande analysguiden beskrivs nedan.

Börja med att markera variabeln som beräkningarna gäller:

![](assets/s_ncs_user_report_wizard_017.png)

Som standard erbjuder Adobe Campaign en serie statistik som ska beräknas för de valda uppgifterna. Du kan ändra den här listan, lägga till eller ta bort statistik beroende på dina behov.

Följande åtgärder är möjliga:

* **[!UICONTROL Count]** att räkna alla värden som inte är null i det fält som ska aggregeras, inklusive dubblettvärden (i det aggregerade fältet),
* **[!UICONTROL Average]** för att beräkna medelvärdet av värdena i ett numeriskt fält,
* **[!UICONTROL Minimum]** beräkna det minsta värdet i ett numeriskt fält,
* **[!UICONTROL Maximum]** för att beräkna det maximala värdet för ett numeriskt fält.
* **[!UICONTROL Sum]** beräkna summan av värdena i ett numeriskt fält,
* **[!UICONTROL Standard deviation]** för att beräkna hur de returnerade värdena fördelas runt genomsnittet.
* **[!UICONTROL Number of missing values]** för att beräkna antalet numeriska fält utan definierade värden.
* **[!UICONTROL Decile distribution]** för att distribuera de returnerade värdena så att var och en representerar 1/10 av värdena i ett numeriskt fält.
* **[!UICONTROL Custom distribution]** för att distribuera de returnerade värdena baserat på användardefinierade tröskelvärden.

   Med **[!UICONTROL Detail...]** knappen kan du redigera en statistik och vid behov anpassa beräkningen eller visningen av den:

   ![](assets/s_ncs_user_report_wizard_030.png)

   I det sista steget i guiden visas den kvantitativa analysrapporten.

   ![](assets/reporting_descriptive_view_report.png)

   Information om hur du ändrar rapporten finns i [Bearbeta en rapport](../../reporting/using/processing-a-report.md).

