---
product: campaign
title: Datas livscykel
description: Läs mer om datalivscykler i arbetsflöden
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 366acc1e-d769-4053-9fa1-f47182627c07
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 4%

---

# Datas livscykel {#data-life-cycle}



## Arbetsregister {#work-table}

I arbetsflöden lagras data som transporteras från en aktivitet till en annan i en temporär arbetstabell.

Dessa data kan visas och analyseras genom att högerklicka på lämplig övergång.

![](assets/wf-right-click-analyze.png)

Välj den relevanta menyn för att göra detta:

* Visa målet

  Den här menyn visar tillgängliga data för målpopulationen samt arbetstabellens struktur (**[!UICONTROL Schema]**-fliken).

  ![](assets/wf-right-click-display.png)

  Mer information finns i [Arbetstabeller och arbetsflödesschema](monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Analysera målet

  På den här menyn kan du komma åt den beskrivande analysassistenten som gör att du kan ta fram statistik och rapporter om övergångsdata.

  Mer information om detta hittar du i det här [avsnittet](../../reporting/using/using-the-descriptive-analysis-wizard.md).

Måldata rensas när arbetsflödet körs. Endast den sista arbetstabellen är tillgänglig. Du kan konfigurera arbetsflödet så att alla arbetsregister förblir tillgängliga: markera alternativet **[!UICONTROL Keep the result of interim populations between two executions]** i arbetsflödesegenskaperna.

Vi rekommenderar dock att du undviker att aktivera det här alternativet om det finns stora mängder data.

![](assets/wf-purge-data-option.png)

## Måldata {#target-data}

De data som lagras i arbetsflödets arbetstabell är tillgängliga i personaliseringsfälten.

På så sätt kan du använda data som samlats in via en lista eller baserat på svar på en enkät i en leverans. Använd följande syntax:

```
%= targetData.FIELD %
```

Anpassningselement av typen **[!UICONTROL Target extension]** (targetData) är inte tillgängliga för arbetsflöden med målinriktning. Leveransmålet måste byggas in i arbetsflödet och anges i den inkommande övergången för leveransen.

Om du vill skapa leveranskorrektur måste korrekturmålet byggas baserat på läget **[!UICONTROL Address substitution]** så att personaliseringsdata kan anges. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

I följande exempel ska vi samla in en lista med information om kunderna som ska användas i ett personaliserat e-postmeddelande.

Använd följande steg:

1. Skapa ett arbetsflöde för att samla in information, stämma av den med data som redan finns i databasen och starta sedan en leverans.

   ![](assets/wf-targetdata-sample-1.png)

   I vårt exempel är filinnehållet följande:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Så här läser du in filen:

   ![](assets/wf-targetdata-sample-2.png)

1. Konfigurera typaktiviteten **[!UICONTROL Enrichment]** för att stämma av insamlade data med data som redan finns i Adobe Campaign-databasen.

   Här är avstämningsnyckeln kontonumret:

   ![](assets/wf-targetdata-sample-3.png)

1. Konfigurera sedan **[!UICONTROL Delivery]**: den skapas baserat på en mall och mottagarna anges av den inkommande övergången.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Endast data i övergången får användas för att anpassa leveransen. Anpassningsfält av typen **targetData** är bara tillgängliga för den inkommande populationen av aktiviteten **[!UICONTROL Delivery]**.

1. Använd de fält som samlats in i arbetsflödet i leveransmallen.

   Om du vill göra det infogar du **[!UICONTROL Target extension]**-typanpassningsfält.

   ![](assets/wf-targetdata-sample-5.png)

   Här vill vi infoga kundens favoritmusikgenre och medietyp (CD eller DVD) enligt den fil som samlas in i arbetsflödet.

   Dessutom kommer vi att lägga till en kupong för förmånskortinnehavare, dvs. mottagare för vilka &#39;kortet&#39; är lika med 1.

   ![](assets/wf-targetdata-sample-6.png)

   Data av typen **[!UICONTROL Target extension]** (targetData) infogas i leveranser med samma egenskaper som alla anpassningsfält. De kan också användas i ämnet, länketiketterna eller själva länkarna.

   Meddelanden adresserade till insamlade mottagare kommer att innehålla följande data:

   ![](assets/wf-targetdata-sample-7.png)
