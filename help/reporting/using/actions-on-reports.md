---
product: campaign
title: Åtgärder på rapporter
description: Åtgärder på rapporter
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# Åtgärder på rapporter{#actions-on-reports}

När du visar en rapport kan du utföra ett visst antal åtgärder med verktygsfältet. Dessa beskrivs nedan.

![](assets/s_ncs_advuser_report_wizard_2.png)

Med verktygsfältet kan du till exempel exportera, skriva ut, arkivera eller visa rapporten i en webbläsare.

![](assets/s_ncs_advuser_report_wizard_04.png)

## Exportera en rapport {#exporting-a-report}

Välj det format som du vill exportera rapporten till i listrutan. (.xls, .pdf eller .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

När en rapport innehåller flera sidor måste du upprepa åtgärden för varje sida.

Du kan konfigurera din rapport så att den exporteras i PDF-, Excel- eller OpenOffice-format. Öppna Adobe Campaign Utforskaren och välj den aktuella rapporten.

Exportalternativen nås via **[!UICONTROL Page]**-aktiviteterna i rapporten på fliken **[!UICONTROL Advanced]**.

Ändra inställningarna för **[!UICONTROL Paper]** och **[!UICONTROL Margins]** så att de passar dina behov. Du kan även tillåta export av en sida endast i PDF-format. Det gör du genom att avmarkera alternativet **[!UICONTROL Activate OpenOffice/Microsoft Excel export]**.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Exporterar till Microsoft Excel {#exporting-into-microsoft-excel}

För **[!UICONTROL List with group]**-typrapporter som ska exporteras till Excel gäller följande rekommendationer och begränsningar:

* Rapporterna får inte innehålla tomma rader.

   ![](assets/export_limitations_remove_empty_line.png)

* Förklaringen till listan måste vara dold.

   ![](assets/export_limitations_hide_label.png)

* Rapporterna behöver inte använda formatering som definierats på cellnivå. Du bör använda **[!UICONTROL Form rendering]** för att definiera formatet för cellerna i tabellen. Du kan komma åt **[!UICONTROL Form rendering]** via **[!UICONTROL Administration > Configuration > Form rendering]**.
* Vi rekommenderar inte att du infogar HTML-innehåll.
* Om en rapport innehåller flera tabeller, diagram osv. textelement exporteras de ena under de andra.
* Du kan tvinga radmatningstecknen i celler: den här konfigurationen sparas i Excel. Mer information finns i [Definiera cellformat](../../reporting/using/creating-a-table.md#defining-cell-format).

### Skjut upp exporten {#postpone-the-export}

Du kan skjuta upp exporten av en rapport, t.ex. för att vänta på asynkrona anrop. Om du vill göra det anger du följande parameter i initieringsskriptet på sidan:

```
document.nl_waitBeforeRender = true;
```

Om du vill aktivera exporten och börja konvertera till en PDF-fil använder du funktionen **document.nl_renderToPdf()** utan någon parameter.

### Minnesallokering {#memory-allocation}

När du exporterar vissa stora rapporter kan minnesallokeringsfel uppstå.

I vissa instanser är standardvärdet **maxMB** (**SKMS** för värdinstanser) för JavaScript som anges i konfigurationsfilen **serverConf.xml** inställt på 64 MB. Om du råkar ut för otillräckligt minne när du exporterar en rapport kan det rekommenderas att du ökar den här siffran till 512 MB:

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

Om du vill tillämpa ändringar som gjorts i konfigurationen måste **nlserver**-tjänsten startas om.

Mer information om filen **serverConf.xml** finns i [det här avsnittet](../../production/using/configuration-principle.md).

Mer information om **nlserver**-tjänsten finns i [det här avsnittet](../../production/using/administration.md).

## Skriva ut en rapport {#printing-a-report}

Du kan skriva ut rapporten: Om du vill göra det klickar du på skrivarikonen: Då öppnas dialogrutan.

Du får ett bättre resultat om du redigerar utskriftsalternativen i Internet Explorer och väljer **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## Skapar rapportarkiv {#creating-report-archives}

Genom att arkivera en rapport kan du skapa en vy av rapporten under olika perioder, t.ex. för att visa statistik för en viss tidsperiod.

Om du vill skapa ett arkiv öppnar du den aktuella rapporten och klickar på lämplig ikon.

![](assets/s_ncs_advuser_report_wizard_07.png)

Om du vill visa eller dölja befintliga arkiv klickar du på ikonen Visa/dölj.

![](assets/s_ncs_advuser_report_history_06.png)

Arkivdatumen visas under ikonen för att visa/dölja. Klicka på arkivet för att visa det.

![](assets/s_ncs_advuser_report_history_04.png)

Det går att ta bort ett rapportarkiv. Det gör du genom att gå till noden Adobe Campaign där dina rapporter lagras. Klicka på fliken **[!UICONTROL Archives]**, markera den du vill ta bort och klicka på **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
