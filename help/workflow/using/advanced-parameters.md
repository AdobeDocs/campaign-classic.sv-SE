---
title: Avancerade parametrar
seo-title: Avancerade parametrar
description: Avancerade parametrar
seo-description: null
page-status-flag: never-activated
uuid: 9453d291-921b-4a03-80d1-2c8295f9a986
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f66f1ff5-3601-4eb8-b05d-6f99164890ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Avancerade parametrar{#advanced-parameters}

Egenskapsskärmen för en aktivitet har en **[!UICONTROL Advanced]** flik där du kan definiera ett beteende i händelse av fel, körningsperioden för aktiviteten; och gör att du kan ange ett initieringsskript. Det finns två versioner av den här fliken:

* en förenklad version (till exempel för **[!UICONTROL Start]** och **[!UICONTROL End]** aktiviteter)

   ![](assets/wf-advanced-basic.png)

* en mer detaljerad version (till exempel för **[!UICONTROL Query]** aktiviteten)

   ![](assets/wf-advanced-full.png)

Fälten som ska anges på **[!UICONTROL Advanced]** fliken beskrivs i följande avsnitt.

## Namn {#name}

Det här fältet innehåller aktivitetens interna namn.

## Bild {#image}

I det här fältet kan du ändra bilden som är länkad till en aktivitet. Mer information finns i: Hantera [aktivitetsbilder](../../workflow/using/managing-activity-images.md).

## Körning {#execution}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten aktiveras. Det finns tre möjliga alternativ:

De här alternativen är vanligtvis markerade i kundvagnen genom att högerklicka på aktiviteten.

* **[!UICONTROL Normal]**: aktiviteten utförs som vanligt.
* **[!UICONTROL Do not activate]**: den här aktiviteten och alla följande uppgifter (i samma gren) körs inte.
* **[!UICONTROL Activate but do not execute]**: den här aktiviteten och alla följande uppgifter (i samma gren) stoppas automatiskt. Detta kan vara användbart om du vill vara där när aktiviteten startas. Om du vill utföra åtgärden manuellt högerklickar du på aktiviteten och väljer **[!UICONTROL Normal execution]**.

## Tillhörighet {#affinity}

I det här fältet kan du framtvinga körning av en aktivitet på en viss dator. Mer information finns i: Hantera [benägenhet](../../workflow/using/managing-propensity.md).

## Max. körningsperiod {#max--execution-period}

I det här fältet kan du ange en varning för när aktiviteten tar för lång tid. Det påverkar inte arbetsflödets funktion. Om uppgiften inte är slutförd innan den är **[!UICONTROL Max. execution period]** klar visas en varning för det här arbetsflödet på **[!UICONTROL Instance monitoring]** sidan. Den här sidan öppnas via fliken **[!UICONTROL Monitoring]** på startsidan.

## Beteende {#behavior}

I det här fältet kan du definiera det beteende som ska användas för asynkrona uppgifter. Det finns två möjliga alternativ:

* **[!UICONTROL Several tasks authorized]**: flera åtgärder kan utföras samtidigt, även om den första inte är klar.
* **[!UICONTROL The current task has priority]**: pågående uppgifter får prioritet. Så länge en uppgift pågår kommer ingen annan åtgärd att utföras.

## Tidszon {#time-zone}

I det här fältet kan du välja aktivitetens tidszon. Mer information: Hantera [tidszoner](../../workflow/using/managing-time-zones.md).

## Vid fel {#in-case-of-errors}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten innehåller fel. Det finns två möjliga alternativ:

* **[!UICONTROL Stop the process]**: arbetsflödet stoppas automatiskt. Dess status ändras till **[!UICONTROL Failed]**. Starta om arbetsflödet när problemet är löst.
* **[!UICONTROL Ignore]**: den här aktiviteten och alla följande åtgärder (i samma gren) körs inte. Detta kan vara användbart för återkommande uppgifter. Om grenen har en schemaläggare placerad uppströms startar den som vanligt på nästa körningsdatum.

## Initieringsskript {#initialization-script}

I det här fältet kan du initiera variabler eller ändra aktivitetsegenskaper. Mer information finns i: [JavaScript-skript och -mallar](../../workflow/using/javascript-scripts-and-templates.md).

## Kommentar {#comment}

Fältet är ett **[!UICONTROL Comment]** kostnadsfritt fält där du kan lägga till en beskrivning.
