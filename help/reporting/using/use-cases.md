---
product: campaign
title: Användningsexempel för analysrapportering
description: Användningsexempel för analysrapportering
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Reporting, Monitoring
exl-id: e326e32e-7bb0-46ff-9ba5-94ccd1169af2
source-git-commit: 5e062f9dbdf6c148e442ac10dbb12cf72ba0179b
workflow-type: tm+mt
source-wordcount: '1331'
ht-degree: 0%

---

# Användningsexempel för analysrapportering {#use-cases}

## Analysera en population {#analyzing-a-population}

I följande exempel kan du utforska populationen som har en uppsättning nyhetsbrev som mål med hjälp av den beskrivande analysassistenten.

Implementeringsstegen beskrivs nedan, medan en uttömmande lista över alternativ och beskrivningar finns i de andra avsnitten i detta kapitel.

### Identifiera populationen som ska analyseras {#identifying-the-population-to-analyze}

I det här exemplet vill vi utforska målpopulationen för leveranser som ingår i mappen **Newsletters** .

Om du vill göra det väljer du de aktuella leveranserna, högerklickar och väljer **[!UICONTROL Action > Explore the target...]**.

![](assets/reporting_quick_start_1.png)

### Välja en analystyp {#selecting-a-type-of-analysis}

I det första steget i assistenten kan du välja den beskrivande analysmall som ska användas. Som standard har Adobe Campaign två mallar: **[!UICONTROL Qualitative distribution]** och **[!UICONTROL Quantitative distribution]**. Mer information finns i avsnittet [Konfigurera den kvalitativa distributionsmallen](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-qualitative-distribution-template). De olika återgivningarna visas i avsnittet [Om beskrivande analys](../../reporting/using/about-descriptive-analysis.md).

I det här exemplet väljer du mallen **[!UICONTROL Qualitative distribution]** och väljer en visning med ett diagram och en tabell (matris). Ge rapporten ett namn (&quot;Beskrivning analys&quot;) och klicka på **[!UICONTROL Next]**.

![](assets/reporting_descriptive_quickstart_step_1.png)

### Välja vilka variabler som ska visas {#selecting-the-variables-to-display}

I nästa steg kan du markera de data som ska visas i tabellen.

Klicka på länken **[!UICONTROL Add...]** för att markera variabeln som innehåller de data som ska visas. Här vill vi visa städerna för våra mottagare på en rad:

![](assets/reporting_descriptive_quickstart_step_2.png)

Kolumnerna visar antalet inköp per företag. I det här exemplet aggregeras belopp i fältet **Webbköp**.

Här vill vi definiera resultatbindning för att förtydliga hur de visas. Om du vill göra det väljer du bindningsalternativet **[!UICONTROL Manual]** och anger beräkningsklasserna för segmenten som ska visas:

![](assets/reporting_descriptive_quickstart_step_2a.png)

Klicka sedan på **[!UICONTROL Ok]** för att godkänna konfigurationen.

När linjerna och kolumnerna har definierats kan du ändra, flytta eller ta bort dem med verktygsfältet.

![](assets/reporting_descriptive_quickstart_step_2b.png)

### Definiera visningsformatet {#defining-the-display-format}

I nästa steg i assistenten kan du välja vilken typ av diagram du vill generera.

I det här fallet väljer du histogrammet.

![](assets/reporting_descriptive_quickstart_step_3.png)

Möjliga konfigurationer av de olika bilderna finns i avsnittet [Alternativ för analysrapportdiagram](../../reporting/using/processing-a-report.md#analysis-report-chart-options).

### Konfigurera statistiken som ska beräknas {#configuring-the-statistic-to-calculate}

Ange sedan de beräkningar som ska tillämpas på de insamlade uppgifterna. Som standard utför den beskrivande analysassistenten ett enkelt antal värden.

I det här fönstret kan du definiera en lista med statistik som ska beräknas.

![](assets/reporting_descriptive_quickstart_step_4.png)

Om du vill skapa en ny statistik klickar du på knappen **[!UICONTROL Add]**. Mer information finns i [Statistikberäkning](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation).

### Visa och använda rapporten {#viewing-and-using-the-report}

I det sista steget i assistenten visas tabellen och diagrammet.

Du kan lagra, exportera och skriva ut data med verktygsfältet ovanför tabellen. Mer information finns i [Bearbeta en rapport](../../reporting/using/processing-a-report.md).

![](assets/reporting_descriptive_quickstart_step_5.png)

## Kvalitativ dataanalys {#qualitative-data-analysis}

### Exempel på en diagramvisning {#example-of-a-chart-display}

**Mål**: Generera en analysrapport om platsen för potentiella kunder eller kunder.

1. Öppna den beskrivande analysassistenten och välj bara **[!UICONTROL Chart]**.

   ![](assets/s_ncs_user_report_wizard_05a.png)

   Klicka på **[!UICONTROL Next]** för att godkänna det här steget.

1. Välj sedan alternativet **[!UICONTROL 2 variables]** och ange att **[!UICONTROL First variable (abscissa)]** ska referera till mottagarstatus (prospects/customers) och att den andra variabeln ska referera till landet.
1. Välj **[!UICONTROL Cylinders]** som typ.

   ![](assets/s_ncs_user_report_wizard_05.png)

1. Klicka på **[!UICONTROL Next]** och lämna standardvärdet **[!UICONTROL Simple count]**.
1. Klicka på **[!UICONTROL Next]** för att visa rapporten.

   ![](assets/s_ncs_user_report_wizard_04.png)

   Håll muspekaren över en bar för att se det exakta antalet kunder eller potentiella kunder för det här landet.

1. Aktivera eller inaktivera visning av ett av länderna baserat på teckenförklaringen.

   ![](assets/s_ncs_user_report_wizard_06png.png)

### Exempel på en tabellvisning {#example-of-a-table-display}

**Mål**: analysera företagets e-postdomäner.

1. Öppna den beskrivande analysassistenten och välj endast visningsläget **[!UICONTROL Array]**.

   ![](assets/s_ncs_user_report_wizard_03a.png)

   Klicka på knappen **[!UICONTROL Next]** för att godkänna det här steget.

1. Markera variabeln **[!UICONTROL Company]** som en kolumn och variabeln **[!UICONTROL Email domain]** som en rad.
1. Behåll alternativet **[!UICONTROL By rows]** för statistikorientering: Den statistiska beräkningen visas till höger om variabeln **[!UICONTROL Email domain]**.

   ![](assets/s_ncs_user_report_wizard_03b.png)

   Klicka på **[!UICONTROL Next]** för att godkänna det här steget.

1. Ange sedan den statistik som ska beräknas: behåll standardantalet och skapa en ny statistik. Det gör du genom att klicka på **[!UICONTROL Add]** och välja **[!UICONTROL Total percentage distribution]** som operator.

   ![](assets/s_ncs_user_report_wizard_03.png)

1. Ange en etikett för statistiken så att det inte blir ett tomt fält när rapporten visas.

   ![](assets/s_ncs_user_report_wizard_014.png)

1. Klicka på **[!UICONTROL Next]** för att visa rapporten.

   ![](assets/s_ncs_user_report_wizard_06.png)

1. När analysrapporten har skapats kan du anpassa visningen efter dina behov utan att ändra konfigurationen. Du kan till exempel växla mellan axlarna: högerklicka på domännamnen och välj **[!UICONTROL Turn]** på snabbmenyn.

   ![](assets/s_ncs_user_report_wizard_07.png)

   Tabellen visar informationen enligt följande:

   ![](assets/s_ncs_user_report_wizard_07a.png)

## Kvantitativ dataanalys {#quantitative-data-analysis}

**Mål**: För att generera en kvantitativ analysrapport för mottagarnas ålder

1. Öppna den beskrivande analysassistenten och välj **[!UICONTROL Quantitative distribution]** i listrutan.

   ![](assets/s_ncs_user_report_wizard_011a.png)

   Klicka på knappen **[!UICONTROL Next]** för att godkänna det här steget.

1. Markera variabeln **[!UICONTROL Age]** och ange dess etikett. Ange om det är ett heltal eller inte och klicka sedan på **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_report_wizard_011.png)

1. Ta bort statistiken för **[!UICONTROL Deciles]**, **[!UICONTROL Distribution]** och **[!UICONTROL Sum]**: de behövs inte här.

   ![](assets/s_ncs_user_report_wizard_012.png)

1. Klicka på **[!UICONTROL Next]** för att visa rapporten.

   ![](assets/s_ncs_user_report_wizard_013.png)

## Analysera ett övergångsmål i ett arbetsflöde {#analyzing-a-transition-target-in-a-workflow}

**Mål**: för att generera rapporter om populationen i ett målarbetsflöde

1. Öppna önskat målarbetsflöde.
1. Högerklicka på en övergång som pekar på mottagartabellen.
1. Välj **[!UICONTROL Analyze target]** i listrutan för att öppna det beskrivande analysfönstret.

   ![](assets/s_ncs_user_report_wizard_from_transision.png)

1. Nu kan du antingen välja alternativet **[!UICONTROL Existing analyses and reports]** och använda rapporter som skapats tidigare (se [Återanvända befintliga rapporter och analyser](../../reporting/using/processing-a-report.md#re-using-existing-reports-and-analyses)) eller skapa en ny beskrivande analys. Låt alternativet **[!UICONTROL New descriptive analysis from a template]** vara markerat som standard.

   Resten av konfigurationen är densamma som för alla beskrivande analyser.

### Rekommendationer för målinriktad analys {#target-analyze-recommendations}

Analysen av en population i ett arbetsflöde kräver att populationen fortfarande finns i övergången. Om arbetsflödet startas kan resultatet som gäller populationen rensas från övergången. Om du vill göra en analys kan du antingen:

* Koppla loss övergången från målaktiviteten och starta arbetsflödet för att aktivera den. När övergången börjar blinka startar du assistenten på det vanliga sättet.

  ![](assets/s_ncs_user_report_wizard_018.png)

* Ändra arbetsflödets egenskaper genom att välja alternativet **[!UICONTROL Keep the result of interim populations between two executions]**. Detta gör att du kan starta en analys av den övergång du vill använda, även om arbetsflödet är färdigt.

  ![](assets/s_ncs_user_report_wizard_020.png)

  Om populationen rensades från övergången uppmanas du att välja det aktuella alternativet innan du startar den beskrivande analysassistenten.

  ![](assets/s_ncs_user_report_wizard_019.png)

>[!CAUTION]
>
>Alternativet **[!UICONTROL Keep the result of interim populations between two executions]** får bara användas i utvecklingsfaser, men aldrig för en miljö i produktion.\
>Interimspopulationerna rensas automatiskt när tidsgränsen för kvarhållande har uppnåtts. Den här tidsgränsen anges på fliken för arbetsflödesegenskaper **[!UICONTROL Execution]**.

## Analyserar loggar för mottagarspårning {#analyzing-recipient-tracking-logs}

Den beskrivande analysassistenten kan generera rapporter för andra arbetsregister. Det innebär att du kan analysera leveransloggar genom att skapa en dedikerad rapport.

I det här exemplet vill vi analysera reaktivitetsfrekvensen för nyhetsbrevets mottagare.

Gör så här:

1. Öppna den beskrivande analysassistenten via menyn **[!UICONTROL Tools > Descriptive analysis]** och ändra standardarbetstabellen. Välj **[!UICONTROL Recipient tracking log]** och lägg till ett filter för att exkludera korrektur och inkludera nyhetsbrev.

   ![](assets/reporting_descriptive_sample_tracking_1.png)

   Markera en tabellvisning och klicka på **[!UICONTROL Next]**.

1. I nästa fönster anger du att analysen avser leveranser.

   ![](assets/reporting_descriptive_sample_tracking_2.png)

   Här visas leveransetiketter i den första kolumnen.

1. Ta bort standardantalet och skapa tre statistiker för att konfigurera den statistik som ska visas i tabellen.

   Här visas för varje nyhetsbrev: antalet öppningar, antalet klick och reaktivitetsfrekvensen (i procent).

1. Lägg till en statistik för att räkna antalet klick: definiera det relevanta filtret på fliken **[!UICONTROL Filter]**.

   ![](assets/reporting_descriptive_sample_tracking_3.png)

1. Klicka sedan på fliken **[!UICONTROL General]** för att byta namn på statistiketiketten och aliaset:

   ![](assets/reporting_descriptive_sample_tracking_4.png)

1. Lägg till en andra statistik för att räkna antalet öppningar:

   ![](assets/reporting_descriptive_sample_tracking_5.png)

1. Klicka sedan på fliken **[!UICONTROL General]** för att byta namn på statistiketiketten och dess alias:

   ![](assets/reporting_descriptive_sample_tracking_6.png)

1. Lägg till den tredje statistiken och välj operatorn **[!UICONTROL Calculated field]** för att mäta reaktivitetsfrekvensen.

   ![](assets/reporting_descriptive_sample_tracking_7.png)

   Gå till fältet **[!UICONTROL User function]** och ange följande formel:

   ```
   @clic / @open * 100
   ```

   Anpassa statistiketiketten enligt nedan:

   ![](assets/reporting_descriptive_sample_tracking_8.png)

   Slutligen anger du om värdena ska visas i procent: om du vill göra det avmarkerar du alternativet **[!UICONTROL Default formatting]** på fliken **[!UICONTROL Advanced]** och väljer **[!UICONTROL Percentage]** utan decimaltecken.

   ![](assets/reporting_descriptive_sample_tracking_10.png)

1. Klicka på **[!UICONTROL Next]** för att visa rapporten.

   ![](assets/reporting_descriptive_sample_tracking_9.png)

## Analyserar exkluderingsloggar för leverans {#analyzing-delivery-exclusion-logs}

Om analysen gäller en leverans kan du analysera den uteslutna populationen. Om du vill göra det väljer du de leveranser som ska analyseras och högerklickar för att öppna menyn **[!UICONTROL Action > Explore exclusions]**.

![](assets/reporting_descriptive_exclusion_menu.png)

Detta tar dig till den beskrivande analysassistenten och analysen rör loggarna för uteslutning av mottagare.

Du kan till exempel visa domänerna för alla utelämnade adresser och sortera dem efter exkluderingsdatum.

![](assets/reporting_descriptive_exclusion_sample.png)

Detta skulle generera följande typ av rapport:

![](assets/reporting_descriptive_exclusion_result.png)
