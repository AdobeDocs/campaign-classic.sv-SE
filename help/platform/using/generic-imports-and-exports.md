---
solution: Campaign Classic
product: campaign
title: Allmän import och export
description: Allmän import och export
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---


# Allmän import och export{#generic-imports-and-exports}

Adobe Campaign erbjuder en modul för dataexport som gör det enkelt att extrahera en lista över kunder eller potentiella kunder (till exempel efter en målinriktningsåtgärd) som sedan blir en del av målpopulationen.

I Adobe Campaign finns också en importmodul som gör att du kan förse databasen med data från externa filer.

>[!NOTE]
>
>Export och import konfigureras i dedikerade mallar som körs via arbetsflöden via aktiviteterna **[!UICONTROL Import]** och **[!UICONTROL Export]**. De kan upprepas automatiskt enligt ett schema, t.ex. för att automatisera datautbyte mellan olika informationssystem. Om det behövs kan du skapa en tillfällig import eller export via noden **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** i Adobe Campaign-trädet.

Du kan:

* Skapa en import- eller exportmall och konfigurera den (se nedan).
* Skapa en import eller export: hänvisar till [Exportera data](../../platform/using/exporting-data.md) eller [Importera data](../../platform/using/importing-data.md).
* Starta importen eller exporten och övervaka dess körning. se [Körningsspårning](#execution-tracking).

>[!CAUTION]
>
>Dataimport i Campaign bör ske via arbetsflöden för att säkra konsekvensen och förbättra effektiviteten. Mer information finns i avsnitten [Importera data](../../workflow/using/importing-data.md), [Importera metodtips](../../workflow/using/importing-data.md#best-practices-when-importing-data) och [Exempel på importmall](../../workflow/using/importing-data.md#setting-up-a-recurring-import).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

## Skapar en jobbmall {#creating-a-job-template}

Import- och exportmallar lagras i katalogen **[!UICONTROL Resources > Templates > Job templates]** i Adobe Campaign-trädet.

Som standard finns det tre importmallar och en exportmall i den här katalogen. De får inte ändras. Du kan duplicera dem för att skapa egna mallar eller skapa en ny mall via menyn **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

![](assets/s_ncs_user_export_wizard_template_create.png)

Hur du skapar en processmall beskrivs i [Exportguiden](../../platform/using/exporting-data.md#export-wizard) och [Importguiden](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>Den inbyggda mallen **[!UICONTROL Import denylist]** har redan konfigurerats för att importera en lista med e-postadresser som har lagts till i blockeringslista.
> 
>Med hjälp av mallarna **[!UICONTROL New text import]** och **[!UICONTROL New text export]** kan du konfigurera en import- eller exportfunktion från början.

## Skapa en ny import/export {#creating-a-new-import-export}

När mallen har konfigurerats kan import- och exportåtgärder startas i flera sammanhang i Adobe Campaign.

Alla dessa öppnar guiden [import](../../platform/using/importing-data.md) eller [export](../../platform/using/exporting-data.md#export-wizard).

* Klicka på länken **[!UICONTROL Jobs]** i **[!UICONTROL Profiles and targets]**-avsnittet på Adobe Campaign-arbetsytan: detta tar dig till listan över befintliga importer och exporter.

   Klicka på knappen **[!UICONTROL Create]** och välj den typ av jobb som du vill utföra.

   ![](assets/s_ncs_user_import_from_home.png)

* Du kan även starta import och export från avsnittet Övervakning på arbetsytan: två dedikerade länkar gör att du kan starta importen eller exporten direkt.

   ![](assets/s_ncs_user_import_from_production.png)

* Import och export kan också startas från Adobe Campaign Explorer.

   Om du vill exportera/importera data klickar du på noden **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**, sedan på ikonen **[!UICONTROL New]** och väljer **[!UICONTROL Export]** eller **[!UICONTROL Import]**. Då öppnas rätt guide.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## Körningsspårning {#execution-tracking}

Du kan visa spårningen av körningen i den övre delen av redigeraren. Du kan stänga exportguiden och visa körningen av jobbet via listan över import-/exportjobb.

![](assets/s_ncs_user_export_list_and_details.png)

* På fliken **[!UICONTROL Log]** kan du titta i loggmeddelanden om körning.
* Fliken **[!UICONTROL Rejects]** innehåller de avvisade posterna. Se [Beteende i händelse av ett fel](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>Status för import/export av jobb anges i [Jobbstatus](../../platform/using/importing-data.md#job-statuses).

