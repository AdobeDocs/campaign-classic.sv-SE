---
product: campaign
title: Konfigurera exportjobb
description: Lär dig hur du konfigurerar och kör exportjobb i Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 1%

---

# Konfigurera exportjobb {#executing-export-jobs}

![](../../assets/common.svg)

Med exportjobben kan du komma åt och extrahera data från databasen: kontakter, kunder, listor, segment osv.

Det kan till exempel vara användbart att använda kampanjspårningsdata (historik för spårning osv.) i ett kalkylblad. Utdata kan vara i formaten txt, CSV, TAB eller XML.

Med exportguiden kan du konfigurera och exportera, definiera alternativ och starta körningen. Det är en serie skärmar vars innehåll beror på typen av export (enkel eller flera) och operatörens rättigheter.

Exportguiden visas när ett nytt exportjobb har skapats (se [Skapa import- och exportjobb](../../platform/using/creating-import-export-jobs.md).

## Steg 1 - Välj exportmall {#step-1---choosing-the-export-template}

När du startar exportguiden måste du först välja en mall. Om du till exempel vill konfigurera exporten av mottagare som nyligen har registrerat sig följer du stegen nedan:

1. Välj **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** mapp.
1. Klicka **Nytt** och sedan klicka **Exportera** för att skapa exportmallen.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Klicka på pilen till höger om **[!UICONTROL Export template]** fält för att välja mallen eller klicka på **[!UICONTROL Select link]** för att bläddra i trädet.

   Den inbyggda mallen är **[!UICONTROL New text export]**. Den här mallen får inte ändras, men du kan duplicera den för att konfigurera en ny mall. Som standard sparas exportmallar i **[!UICONTROL Resources > Templates > Job templates]** nod.

1. Ange ett exportnamn i dialogrutan **[!UICONTROL Label]** fält. Du kan lägga till en beskrivning.
1. Välj exporttyp. Det finns två möjliga typer av export: **[!UICONTROL Simple export]** för att exportera endast en fil, och **[!UICONTROL Multiple export]** om du vill exportera flera filer i en enda körning, från en eller flera typer av källdokument.

## Steg 2 - Typ av fil som ska exporteras {#step-2---type-of-file-to-export}

Välj den typ av dokument som ska exporteras, dvs. schemat för de data som ska exporteras.

Som standard när exporten startas från **[!UICONTROL Jobs]** nod som data kommer från mottagartabellen. När exporten startas från en lista med data (från **[!UICONTROL right click > Export]** -menyn) fylls tabellen som data hör till automatiskt i **[!UICONTROL Document type]** fält.

![](assets/s_ncs_user_export_wizard02.png)

* Som standard är **[!UICONTROL Download the file generated on the server after the export]** är markerat. I **[!UICONTROL Local file]** fält, fyll i namn och sökväg för filen som ska skapas eller bläddra på den lokala hårddisken genom att klicka på mappen till höger om fältet. Du kan avmarkera det här alternativet om du vill ange åtkomstsökväg och namn för serverutdatafilen.

   >[!NOTE]
   >
   >Automatiska import- och exportjobb utförs alltid på servern.
   >
   >Om du bara vill exportera vissa data klickar du på **[!UICONTROL Advanced parameters]** och ange antalet rader som ska exporteras i lämpligt fält.

* Du kan skapa en differentiell export om du bara vill exportera poster som har ändrats sedan den senaste körningen. Om du vill göra det klickar du på **[!UICONTROL Advanced parameters]** klicka på **[!UICONTROL Differential export]** tabbtangenten och sedan **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   Du måste ange datumet för den senaste ändringen. Den kan hämtas från ett fält eller beräknas.

## Steg 3 - Definiera utdataformatet {#step-3---defining-the-output-format}

Välj ett utdataformat för exportfilen. Följande format kan användas: text, text med fasta kolumner, CSV och XML.

![](assets/s_ncs_user_export_wizard03.png)

* För **[!UICONTROL Text]** markerar du avgränsarna (tabbar, kommatecken, semikolon eller egna) och strängarna (enkla eller dubbla citattecken eller inga).
* För **[!UICONTROL text]** och **[!UICONTROL CSV]** kan du välja alternativet **[!UICONTROL Use first lines as column titles]**.
* Ange datumformat och talformat. Om du vill göra det klickar du på **[!UICONTROL Edit]** för fältet i fråga och använd redigeraren.
* För fält som innehåller uppräknade värden kan du välja **[!UICONTROL Export labels instead of internal values of enumerations]**. Titeln kan till exempel sparas i formuläret **1=Mr.**, **2=Fröken**, **3=Mrs.**. Om det här alternativet är markerat **Mr.**, **Fröken** och **Fru** exporteras.

## Steg 4 - Val av data {#step-4---data-selection}

Markera de fält som ska exporteras. Så här gör du:

1. Dubbelklicka på önskade fält i dialogrutan **[!UICONTROL Available fields]** för att lägga till dem i **[!UICONTROL Output columns]** -avsnitt.
1. Använd pilarna till höger om listan för att definiera fältordningen i utdatafilen.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Klicka på **[!UICONTROL Add]** för att anropa funktioner. Mer information finns i [Lista över funktioner](../../platform/using/defining-filter-conditions.md#list-of-functions).

## Steg 5 - Sortera kolumner {#step-5---sorting-columns}

Välj sorteringsordning för kolumnerna.

![](assets/s_ncs_user_export_wizard05.png)

## Steg 6 - Filtervillkor {#step-6---filter-conditions-}

Du kan lägga till filtervillkor för att undvika att exportera alla data. Konfigurationen för den här filtreringen är densamma som målinriktningen för mottagare i leveransguiden. Se [den här sidan](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

## Steg 7 - Dataformatering {#step-7---data-formatting}

Du kan ändra ordningen och etiketten på fälten för utdatafilen och använda omformningar på källdata.

* Om du vill ändra ordningen på de kolumner som ska exporteras markerar du den aktuella kolumnen och använder de blå pilarna till höger om tabellen.
* Om du vill ändra etiketten för ett fält klickar du i cellen i **[!UICONTROL Label]** kolumn som matchar fältet som ska ändras och ange den nya etiketten. Tryck på Enter på tangentbordet för att bekräfta.
* Om du vill tillämpa en skiftlägesomformning på innehållet i ett fält väljer du det i dialogrutan **[!UICONTROL Transformation]** kolumn. Du kan välja:

   * Växla till gemener
   * Växla till versaler
   * Första bokstaven i versaler

   ![](assets/s_ncs_user_export_wizard06.png)

* Klicka **[!UICONTROL Add a calculated field]** om du vill skapa ett nytt beräknat fält (t.ex. en kolumn som innehåller efternamn + förnamn). Mer information finns i [Beräknade fält](../../platform/using/executing-import-jobs.md#calculated-fields).

Om du exporterar en samling element (t.ex. mottagarnas prenumerationer, de listor som de hör till osv.) måste du ange antalet element i samlingen som du vill exportera.

![](assets/s_ncs_user_export_wizard06_c.png)

## Steg 8 - Förhandsgranska data {#step-8---data-preview}

Klicka **[!UICONTROL Start the preview of the data]** för en förhandsgranskning av exportresultatet. Som standard visas de första 200 raderna. Om du vill ändra det här värdet klickar du på pilarna till höger om **[!UICONTROL Lines to display]** fält.

![](assets/s_ncs_user_export_wizard07.png)

Klicka på flikarna längst ned i guiden för att växla från förhandsgranskningen av resultat i kolumner till resultaten i XML-format. Du kan även visa de genererade SQL-frågorna.

## Steg 9 - Starta exporten {#step-9---launching-the-export}

Klicka **[!UICONTROL Start]** för att starta dataexport.

![](assets/s_ncs_user_export_wizard08.png)

Du kan sedan övervaka importjobbets körning (se [Övervaka körning av jobb](../../platform/using/monitoring-jobs-execution.md).
