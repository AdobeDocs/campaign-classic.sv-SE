---
product: campaign
title: Använd guiden för beskrivande analys
description: Använd guiden för beskrivande analys
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Reporting, Monitoring
exl-id: 848d67c7-d1dc-4eba-bcb8-672e76d8ce87
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 1%

---

# Använd guiden för beskrivande analys{#using-the-descriptive-analysis-wizard}



Använd den dedikerade guiden för att skapa en beskrivande analysrapport. Konfigurationen beror på vilka data som ska analyseras och på önskad återgivning.

## Analysera data i databasen {#analyzing-data-in-the-database}

Den beskrivande analysguiden kan startas via **[!UICONTROL Tools > Descriptive analysis]** meny: i det här fallet gäller analysen mottagare som standard (**nms:mottagare**). Det gäller alla data i Adobe Campaign-databasen.

![](assets/reporting_descriptive_wz_launch.png)

Analysera en annan tabell än standardmottagarna en (**nms:mottagare**) klickar du på **[!UICONTROL Advanced settings...]** i det sista steget i guiden och markera tabellen som matchar dina inställningar, i det här fallet **cus:individuell**:

![](assets/reporting_descriptive_other_schema.png)

Om du vill producera statistik för en del av data kan du definiera ett filter: om du vill göra det klickar du på **[!UICONTROL Advanced settings...]** länka och definiera det filter som ska användas, enligt nedan:

![](assets/reporting_descriptive_wz_filter.png)

Analysen gäller endast mottagare som är 16 år eller äldre och som bor i London.

## Analysera en uppsättning data {#analyzing-a-set-of-data}

Du kan använda den beskrivande analysguiden i ett annat sammanhang: en lista, en arbetsflödesövergång, en eller flera leveranser, ett urval av mottagare osv.

Det är tillgängligt via flera noder i Adobe Campaign-trädet som pekar på mottagartabellen.

Öppna den beskrivande analysguiden genom att markera objekt och högerklicka. Endast markerade data kommer att analyseras.

![](assets/reporting_descriptive_from_recipients.png)

* För en uppsättning **mottagare**, välj de mottagare som ska analyseras, högerklicka och välj **[!UICONTROL Actions > Explore...]**, som visas ovan. Om ett filter används i listan med mottagare analyseras bara dess innehåll.

  Om du vill markera alla mottagare i mappen eller det aktuella filtret använder du kortkommandot CTRL+A. Detta innebär att även mottagare som inte visas markeras.

  Ett exempel på en beskrivande analys av mottagare finns i: [Kvalitativ dataanalys](../../reporting/using/use-cases.md#qualitative-data-analysis).

* När det gäller **arbetsflöde** placerar du markören på en övergång som pekar mot mottagartabellen, högerklickar och väljer **[!UICONTROL Analyze target]**. Mer information om detta finns i exemplet i [Analysera ett övergångsmål i ett arbetsflöde](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow).
* För **listor** markerar du en eller flera listor och använder samma process som för mottagarna.
* När det gäller **leverans**, välj de leveranser vars mål du vill analysera, högerklicka och välj **[!UICONTROL Actions > Explore the target]**, enligt nedan:

  ![](assets/reporting_descriptive_from_deliveries.png)

  Här finns exempel på beskrivande analyser av leveranser: [Analysera en population](../../reporting/using/use-cases.md#analyzing-a-population) och här: [Analysera loggar för mottagarspårning](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs).

## Konfigurera den kvalitativa distributionsmallen {#configuring-the-qualitative-distribution-template}

The **[!UICONTROL Qualitative distribution]** kan du skapa statistik för alla typer av data (t.ex. företagsnamn, e-postdomän).

Konfigurationsalternativ som är tillgängliga för en rapport som skapats via **[!UICONTROL Qualitative distribution]** -mallar finns i [Visa data i tabellen](#displaying-data-in-the-table). Ett fullständigt exempel finns i [Analysera en population](../../reporting/using/use-cases.md#analyzing-a-population).

När du använder den beskrivande analysguiden för att analysera dina data, beror de tillgängliga alternativen på de valda inställningarna. Dessa beskrivs nedan.

### Databindning {#data-binning}

När du väljer vilka variabler som ska visas kan du definiera databindning, d.v.s. konfigurera grupperingskriterier för de markerade data.

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>När fältet som berörs av beräkningen beräknas med hjälp av ett aggregat, kontrollera **[!UICONTROL The data is already aggregated]** för att förbättra prestandan.

Alternativen varierar beroende på fältets innehåll:

* **[!UICONTROL None]** : Med det här alternativet kan du visa alla värden som är tillgängliga för variabeln, utan bindning.

  >[!CAUTION]
  >
  >Det här alternativet bör användas med försiktighet: det kan ha stor inverkan på rapporten och på datorns prestanda.

* **[!UICONTROL Auto]** : det här alternativet gör att du kan visa de n som visas oftast. De beräknas automatiskt och var och en representerar en procentandel av variablerna jämfört med antalet behållare. För numeriska värden genererar Adobe Campaign automatiskt n klasser att sortera data i.
* **[!UICONTROL Manual]** : det här alternativet fungerar som **[!UICONTROL Auto]** förutom att du kan ange dessa värden manuellt. Klicka på **[!UICONTROL Add]** till höger om värdetabellen.

  Värdena kan initieras automatiskt av Adobe Campaign före personalisering: om du vill göra det anger du antalet behållare som du vill generera och klickar på **[!UICONTROL Initialize with]** länk, enligt nedan:

  ![](assets/reporting_descriptive_initialize.png)

  Anpassa sedan innehållet efter dina behov:

  ![](assets/reporting_descriptive_initialize_perso.png)

  Beroende på den önskade precisionsnivån kan fält som innehåller datum grupperas efter tid, dag, månad, år osv.

  ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** : gör att du kan skapa grupper med värden när det gäller numeriska värden. Med en modulo med värdet 10 kan du till exempel skapa ett intervall med värden som ändras tio gånger tio.

  ![](assets/reporting_descriptive_initialize_modulo.png)

  I det här exemplet kan du visa uppdelningen av mottagare per åldersgrupp.

  ![](assets/reporting_descriptive_initialize_modulo_result.png)

### Visa data i tabellen {#displaying-data-in-the-table}

Använd verktygsfältet för att anpassa visningen av variabler i tabellen: ta bort en kolumn, visa data i rader i stället för kolumner, flytta en kolumn till vänster eller höger, visa eller ändra värdeberäkning.

![](assets/s_ncs_user_report_wizard_toolbar.png)

I fönstrets övre del kan du välja visningsinställningar.

Du kan visa eller dölja namnet på statistiken och delsummorna och välja statistikens orientering. Mer information finns i [Visningsinställningar för analysrapport](../../reporting/using/processing-a-report.md#analysis-report-display-settings).

### Visa data i diagrammet {#displaying-data-in-the-chart}

I det första steget i guiden för beskrivande analys kan du välja att endast visa data i diagramformuläret, utan någon tabell. I det här fallet måste variabelval göras när bilden konfigureras. Du måste först välja antalet variabler som ska visas och välja fälten från den relevanta databasen.

![](assets/s_ncs_user_report_wizard_023.png)

Välj sedan önskad diagramtyp.

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>Du kan visa variablerna i ett diagram och i en tabell samtidigt. Om du vill göra det anger du variablerna i **[!UICONTROL Table configuration]** -fönstret. Klicka **[!UICONTROL Next]** och välj diagramtyp i diagramkonfigurationsfönstret. Om deldimensioner definieras i tabellen visas de inte i diagrammet.

Klicka på **[!UICONTROL Variants]** om du vill ändra diagramegenskaperna.

![](assets/reporting_descriptive_graphe_options.png)

Vilka alternativ som visas beror på vilken typ av diagram som är vald. För mer information om detta hittar du i [det här avsnittet](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

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

* **[!UICONTROL Calculated field]** för att skapa en anpassad operator (endast tillgänglig för tabeller). The **[!UICONTROL User function]** kan du ange den beräkning som ska användas för data.

  Exempel: Beräkna det genomsnittliga inköpsbeloppet per kund baserat på land och ursprung

  ![](assets/report_compute_data_sample1.png)

  Om du vill visa ovanstående information i en tabell måste du skapa ett beräkningsfält för lagring av det genomsnittliga inköpsbeloppet per kund.

  Så här gör du:

   1. Beräkna inköpssumman.

      ![](assets/report_compute_data_sample2.png)

   1. Den här statistiken visas inte i tabellen. Du måste avmarkera **[!UICONTROL Display in the table]** alternativ för **[!UICONTROL Advanced]** -fliken.

      ![](assets/report_compute_data_sample3.png)

   1. Skapa ett nytt **[!UICONTROL Calculated field]** typstatistik och ange följande formel i **[!UICONTROL User function]** fält: **@purchase/@count**.

      ![](assets/report_compute_data_sample4.png)

### Visa rapporten {#displaying-the-report}

I det sista steget i guiden kan du visa rapporten, dvs. tabellen eller diagrammet som de har konfigurerats.

När rapporten innehåller en tabell färgas resultatcellen för beräkning. Ju högre resultat, desto intensivare färg.

![](assets/report_compute_data_sample1.png)

Det går att ändra resultatlayouten. Om du vill göra det högerklickar du på variabeln och väljer indata på snabbmenyn.

![](assets/s_ncs_user_report_wizard_029.png)

När rapporten innehåller ett diagram kan du filtrera den visade informationen med etiketterna i förklaringen: klicka på en etikett för att aktivera/inaktivera visning i diagrammet.

![](assets/report_display_data_in_graph.png)

## Konfigurera den kvantitativa distributionsmallen {#configuring-the-quantitative-distribution-template}

Om du vill generera en beskrivande analys själv väljer du **Ny beskrivande analys från en mall** om det inte är inställt som standard.

The **[!UICONTROL Quantitative distribution]** mall som gör att du kan generera statistik om data som kan mätas eller räknas (t.ex. fakturabelopp, mottagarnas ålder).

Konfigurationsläget för en analysrapport som skapats via **[!UICONTROL Quantitative distribution]** mall anges i ett implementeringsexempel [Kvantitativ dataanalys](../../reporting/using/use-cases.md#quantitative-data-analysis).

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

  The **[!UICONTROL Detail...]** kan du redigera en statistik och vid behov anpassa beräkningen eller visningen av den:

  ![](assets/s_ncs_user_report_wizard_030.png)

  I det sista steget i guiden visas den kvantitativa analysrapporten.

  ![](assets/reporting_descriptive_view_report.png)

  Om du vill göra ändringar i rapporten ska du läsa [Bearbeta en rapport](../../reporting/using/processing-a-report.md).
