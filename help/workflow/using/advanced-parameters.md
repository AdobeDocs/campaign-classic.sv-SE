---
solution: Campaign Classic
product: campaign
title: Avancerade parametrar
description: Avancerade parametrar
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# Avancerade parametrar{#advanced-parameters}

Egenskapsskärmen för en aktivitet har en **[!UICONTROL Advanced]**-flik som gör att du kan definiera ett beteende i händelse av fel, körningsperioden för aktiviteten; och gör att du kan ange ett initieringsskript. Det finns två versioner av den här fliken:

* en förenklad version (för till exempel **[!UICONTROL Start]** och **[!UICONTROL End]**-aktiviteter)

   ![](assets/wf-advanced-basic.png)

* en mer detaljerad version (för aktiviteten **[!UICONTROL Query]**, till exempel)

   ![](assets/wf-advanced-full.png)

Fälten som ska anges på fliken **[!UICONTROL Advanced]** beskrivs i följande avsnitt.

## Namn {#name}

Det här fältet innehåller aktivitetens interna namn.

## Bild {#image}

I det här fältet kan du ändra bilden som är länkad till en aktivitet. Mer information finns i: [Hantera aktivitetsbilder](../../workflow/using/managing-activity-images.md).

## Körning {#execution}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten aktiveras. Det finns tre möjliga alternativ:

De här alternativen är vanligtvis markerade i kundvagnen genom att högerklicka på aktiviteten.

* **[!UICONTROL Normal]**: aktiviteten utförs som vanligt.
* **[!UICONTROL Do not activate]**: den här aktiviteten och alla följande uppgifter (i samma gren) körs inte.
* **[!UICONTROL Activate but do not execute]**: den här aktiviteten och alla följande uppgifter (i samma gren) stoppas automatiskt. Detta kan vara användbart om du vill vara där när aktiviteten startas. Om du vill utföra åtgärden manuellt högerklickar du på aktiviteten och väljer **[!UICONTROL Normal execution]**.

## Tillhörighet {#affinity}

Du kan välja att framtvinga körningen av ett arbetsflöde eller en arbetsflödesaktivitet på en viss dator. För att kunna göra detta måste du definiera en eller flera egenskaper på arbetsflödesnivå eller för den aktuella aktiviteten.

Arbetsflödeskonfigurationen för hög tillgänglighet beskrivs i det här [avsnittet](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).


## Max. körningsperiod {#max--execution-period}

I det här fältet kan du ange en varning för när aktiviteten tar för lång tid. Det påverkar inte arbetsflödets funktion. Om aktiviteten inte är klar när **[!UICONTROL Max. execution period]** är slut visas en varning för det här arbetsflödet på **[!UICONTROL Instance monitoring]**-sidan. Den här sidan nås via fliken **[!UICONTROL Monitoring]** på startsidan.

## Beteende {#behavior}

I det här fältet kan du definiera det beteende som ska användas för asynkrona uppgifter. Det finns två möjliga alternativ:

* **[!UICONTROL Several tasks authorized]**: flera åtgärder kan utföras samtidigt, även om den första inte är klar.
* **[!UICONTROL The current task has priority]**: pågående uppgifter får prioritet. Så länge en uppgift pågår kommer ingen annan åtgärd att utföras.

## Tidszon {#time-zone}

I det här fältet kan du välja aktivitetens tidszon. Mer information: [Hantera tidszoner](../../workflow/using/managing-time-zones.md).

## Vid fel {#in-case-of-errors}

I det här fältet kan du definiera vilken åtgärd som ska utföras när aktiviteten innehåller fel. Det finns två möjliga alternativ:

* **[!UICONTROL Stop the process]**: arbetsflödet stoppas automatiskt. Dess status ändras till **[!UICONTROL Failed]**. Starta om arbetsflödet när problemet är löst.
* **[!UICONTROL Ignore]**: den här aktiviteten och alla följande åtgärder (i samma gren) körs inte. Detta kan vara användbart för återkommande uppgifter. Om grenen har en schemaläggare placerad uppströms startar den som vanligt på nästa körningsdatum.

## Initieringsskript {#initialization-script}

I det här fältet kan du initiera variabler eller ändra aktivitetsegenskaper. Mer information finns i: [JavaScript-skript och -mallar](../../workflow/using/javascript-scripts-and-templates.md).

## Kommentar {#comment}

Fältet **[!UICONTROL Comment]** är ett kostnadsfritt fält där du kan lägga till en beskrivning.
