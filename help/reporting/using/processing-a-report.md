---
title: Bearbeta en rapport
seo-title: Bearbeta en rapport
description: Bearbeta en rapport
seo-description: null
page-status-flag: never-activated
uuid: af8f1101-135f-49ce-bada-bd19fe32053b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 667746cb-b553-4a71-8523-6b2695047ab6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62b2f1f6cfcaadd10880d428b8b94d73d2addcdb

---


# Använda en analysrapport{#processing-a-report}

## Spara en analysrapport {#saving-an-analysis-report}

Om du har rätt behörighet kan du spara en analysrapport som har skapats från en mall eller exportera den i Excel-, PDF- eller OpenOffice-format.

Spara rapporten genom att klicka **[!UICONTROL Save]** och ge rapporten en etikett.

Välj **[!UICONTROL Also save data]** om du vill skapa en historik för rapporten och se rapportens värden när du sparar den. Mer information finns i Rapporter om [arkiveringsanalys](#archiving-analysis-reports).

Med det här **[!UICONTROL Share this report]** alternativet kan andra operatorer få åtkomst till rapporten.

![](assets/s_ncs_user_report_wizard_010.png)

När den har sparats kan den här rapporten återanvändas för att generera andra analysrapporter:

![](assets/s_ncs_user_report_wizard_08a.png)

Om du vill göra ändringar i den här rapporten redigerar du noden i Adobe Campaign-trädet (eller den första mappen av typen Rapporter som operatorn har redigeringsbehörighet för). **[!UICONTROL Administration > Configuration > Adobe Campaign tree reports]** Mer information finns i [Konfigurera layouten för en beskrivande analysrapport](#configuring-the-layout-of-a-descriptive-analysis-report).

## Ytterligare inställningar för analysrapport {#analysis-report-additional-settings}

När en beskrivande analysrapport har sparats kan du redigera dess egenskaper och få tillgång till ytterligare alternativ.

![](assets/s_ncs_user_report_wizard_08b.png)

Dessa alternativ är desamma som standardrapporter och beskrivs på [den här sidan](../../reporting/using/properties-of-the-report.md).

## Konfigurera layouten för en beskrivande analysrapport {#configuring-the-layout-of-a-descriptive-analysis-report}

Du kan anpassa visningen och layouten av data i diagram och tabeller i den beskrivande analysen. Alla alternativ nås via Adobe Campaign-trädet på fliken **[!UICONTROL Edit]** för respektive rapport.

### Visningsläge för analysrapport {#analysis-report-display-mode}

När du skapar en rapport med hjälp av **[!UICONTROL qualitative distribution]** mallen väljs tabell- och diagramvisningslägena som standard. Om du bara vill ha ett visningsläge avmarkerar du lämplig ruta. Det innebär att bara fliken för det markerade visningsläget är tillgänglig.

![](assets/s_ncs_advuser_report_display_01.png)

Om du vill ändra schemat för rapporten klickar du på **[!UICONTROL Select the link]** och väljer en annan tabell i databasen.

![](assets/s_ncs_advuser_report_display_02.png)

### Visningsinställningar för analysrapport {#analysis-report-display-settings}

Du kan dölja eller visa statistik och delsummor samt välja statistikens orientering.

![](assets/s_ncs_advuser_report_display_05.png)

När du skapar statistik kan du anpassa deras etikett.

![](assets/s_ncs_advuser_report_display_06.png)

Deras namn visas i rapporten.

![](assets/s_ncs_advuser_report_display_07.png)

Om du avmarkerar alternativet för etikett och delsummor visas de inte i rapporten. Namnet visas i ett verktygstips när du håller muspekaren över en cell i tabellen.

![](assets/s_ncs_advuser_report_display_08.png)

Som standard visas statistiken online. Om du vill ändra orienteringen väljer du lämpligt alternativ i listrutan.

![](assets/s_ncs_advuser_report_wizard_035a.png)

I följande exempel visas statistiken i kolumner.

![](assets/s_ncs_advuser_report_wizard_035.png)

### Datalayout för analysrapport {#analysis-report-data-layout}

Du kan anpassa datalayouten direkt i de beskrivande analystabellerna. Det gör du genom att högerklicka på variabeln som du vill arbeta med. Välj tillgängliga alternativ i listrutan:

* **[!UICONTROL Pivot]** om du vill ändra variabelns axel.
* **[!UICONTROL Up]** / **[!UICONTROL Down]** för att växla variablerna på rader.
* **[!UICONTROL Move to the right]** / **[!UICONTROL Move to the left]** för att växla variablerna i kolumner.
* **[!UICONTROL Turn]** för att invertera variabelaxlarna.
* **[!UICONTROL Sort from A to Z]** om du vill sortera variabelvärdena från låg till hög.
* **[!UICONTROL Sort from Z to A]** för att sortera variabelvärdena high till low.

   ![](assets/s_ncs_advuser_report_wizard_016.png)

Uppdatera vyn om du vill återgå till den ursprungliga visningen.

### Alternativ för analysrapportdiagram {#analysis-report-chart-options}

Det går att anpassa visningen av data i diagrammet. Det gör du genom att klicka på den **[!UICONTROL Variables...]** länk som är tillgänglig under urvalssteget för diagramtyp.

![](assets/s_ncs_advuser_report_wizard_3c.png)

Följande alternativ är tillgängliga:

* I fönstrets övre del kan du ändra diagrammets visningsområde.
* Etiketter visas som standard i diagrammet. Du kan dölja dem genom att avmarkera **[!UICONTROL Show values]** alternativet.
* Med det här **[!UICONTROL Accumulate values]** alternativet kan du lägga till värden från en serie till en annan.
* Du kan välja om du vill visa diagramförklaringen eller inte: om du vill dölja den avmarkerar du lämpligt alternativ. Som standard visas teckenförklaringen utanför diagrammet i det övre högra hörnet.

   Förklaringen kan också visas ovanpå diagrammet för att spara på visningsutrymmet. Välj alternativet **[!UICONTROL Include in the chart]**

   Välj lodrät och vågrät justering i **[!UICONTROL Caption position]** listrutan.

   ![](assets/s_ncs_advuser_report_wizard_3d.png)

## Exportera en analysrapport {#exporting-an-analysis-report}

Om du vill exportera data från en analysrapport klickar du på listrutan och väljer önskat utdataformat.

![](assets/s_ncs_user_report_wizard_09.png)

Mer information finns på [den här sidan](../../reporting/using/actions-on-reports.md).

## Återanvända befintliga rapporter och analyser {#re-using-existing-reports-and-analyses}

Du kan skapa beskrivande analysrapporter om data med hjälp av befintliga rapporter som redan lagrats i Adobe Campaign. Det här läget är möjligt när analyser har sparats eller när rapporter har skapats och konfigurerats för att nås via den beskrivande analysguiden.

Information om hur du sparar beskrivande analyser finns i [Spara en analysrapport](#saving-an-analysis-report).

Om du vill skapa beskrivande analysrapporter måste den beskrivande analysguiden köras via en arbetsflödesövergång eller via **[!UICONTROL Tools > Descriptive analysis]** menyn.

1. Markera **[!UICONTROL Existing analyses and reports]** och klicka **[!UICONTROL Next]**.
1. På så sätt kan du komma åt listan med tillgängliga rapporter. Välj den rapport som du vill generera.

   ![](assets/s_ncs_user_report_wizard_01.png)

## Arkiveringsanalysrapporter {#archiving-analysis-reports}

När du skapar en beskrivande analys baserad på en befintlig analys kan du skapa arkiv för att lagra data och jämföra rapportresultat.

Så här skapar du en historik:

1. Öppna en befintlig analys eller skapa en ny beskrivande analysguide.
1. Klicka på knappen för att skapa en historik i verktygsfältet på rapportvisningssidan och bekräfta sedan enligt nedan:

   ![](assets/reporting_descriptive_historize_icon.png)

1. Använd arkivåtkomstknappen för att visa tidigare analyser.

   ![](assets/reporting_descriptive_historize_access.png)

