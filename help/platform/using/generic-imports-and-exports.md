---
title: Allmän import och export
seo-title: Allmän import och export
description: Allmän import och export
seo-description: null
page-status-flag: never-activated
uuid: e98753bb-1f14-4ec7-aa3b-d5e4f1ebaef7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: a21576c7-e94c-4fe1-9e31-d89116e427f6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Allmän import och export{#generic-imports-and-exports}

Adobe Campaign erbjuder en modul för dataexport som gör det enkelt att extrahera en lista över kunder eller potentiella kunder (till exempel efter en målinriktningsåtgärd) som sedan blir en del av målpopulationen.

Adobe Campaign erbjuder också en importmodul som gör att du kan förse databasen med data från externa filer.

>[!NOTE]
>
>Export och import konfigureras i dedikerade mallar som körs via arbetsflöden via **[!UICONTROL Import]** och **[!UICONTROL Export]** aktiviteter. De kan upprepas automatiskt enligt ett schema, t.ex. för att automatisera datautbyte mellan olika informationssystem. Om det behövs kan du skapa en tillfällig import eller export via noden **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** i Adobe Campaign-trädet.

Du kan:

* Skapa en import- eller exportmall och konfigurera den (se nedan).
* Skapa en import eller export: hänvisar till [Exportera data](../../platform/using/exporting-data.md) eller [Importera data](../../platform/using/importing-data.md).
* Starta importen eller exporten och övervaka dess körning. se [Körningsspårning](#execution-tracking).

>[!CAUTION]
>
>Dataimport i Campaign bör ske via arbetsflöden för att säkra konsekvensen och förbättra effektiviteten. Mer information finns i avsnitten [Importera data](../../workflow/using/importing-data.md), [Importera bästa praxis](../../workflow/using/importing-data.md#best-practices-when-importing-data) och Exempel [på](../../workflow/using/importing-data.md#setting-up-a-recurring-import) importmallar.

## Skapa en jobbmall {#creating-a-job-template}

Import- och exportmallar lagras i katalogen **[!UICONTROL Resources > Templates > Job templates]** i Adobe Campaign-trädet.

![](assets/s_ncs_user_export_wizard_template.png)

Som standard finns det tre importmallar och en exportmall i den här katalogen. De får inte ändras. Du kan duplicera dem för att skapa egna mallar eller skapa en ny mall via menyn **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** .

![](assets/s_ncs_user_export_wizard_template_create.png)

Hur du skapar en processmall beskrivs i [Exportguiden](../../platform/using/exporting-data.md#export-wizard) och [importguiden](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>Den inbyggda mallen **[!UICONTROL Import blacklist]** är redan konfigurerad för att importera en lista med utskrivna e-postadresser.
> 
>Med mallarna **[!UICONTROL New text import]** och **[!UICONTROL New text export]** kan du konfigurera en import- eller exportfunktion från grunden.

## Skapa en ny import/export {#creating-a-new-import-export}

När mallen har konfigurerats kan import- och exportåtgärder startas i flera sammanhang i Adobe Campaign.

Alla dessa öppnar [import](../../platform/using/importing-data.md) - eller [exportguiden](../../platform/using/exporting-data.md#export-wizard) .

* Klicka på **[!UICONTROL Profiles and targets]** länken i delen **[!UICONTROL Jobs]** av arbetsytan i Adobe Campaign: detta tar dig till listan över befintliga importer och exporter.

   Klicka på **[!UICONTROL Create]** knappen och välj den typ av jobb som du vill utföra.

   ![](assets/s_ncs_user_import_from_home.png)

* Du kan även starta import och export från avsnittet Övervakning på arbetsytan: två dedikerade länkar gör att du kan starta importen eller exporten direkt.

   ![](assets/s_ncs_user_import_from_production.png)

* Import och export kan också startas från Adobe Campaign Explorer.

   Om du vill exportera/importera data klickar du på **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** noden, sedan på **[!UICONTROL New]** ikonen och väljer **[!UICONTROL Export]** eller **[!UICONTROL Import]**. Då öppnas rätt guide.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## Körningsspårning {#execution-tracking}

Du kan visa spårningen av körningen i den övre delen av redigeraren. Du kan stänga exportguiden och visa körningen av jobbet via listan över import-/exportjobb.

![](assets/s_ncs_user_export_list_and_details.png)

* På fliken **[!UICONTROL Log]** kan du titta i loggmeddelanden som rör körning.
* Fliken innehåller de avvisade posterna **[!UICONTROL Rejects]** . Se [Beteende i händelse av ett fel](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>Status för import-/exportjobb anges i [jobbstatus](../../platform/using/importing-data.md#job-statuses).

