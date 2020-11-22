---
solution: Campaign Classic
product: campaign
title: AND-join
description: AND-join
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 6%

---


# AND-join{#and-join}

En join utlöser sin utgående övergång endast när alla inkommande övergångar är aktiverade, dvs. när alla tidigare aktiviteter är slutförda. På så sätt kan du se till att vissa aktiviteter har slutförts innan du fortsätter att köra arbetsflödet.

Du kan till exempel använda en AND-join-aktivitet när du skapar innehåll och skickar automatisering för att se till att en leverans bara startas när målfrågor och innehållsuppdateringar är klara. Ett fall för dedikerad användning finns i [det här avsnittet](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

Den utgående skickade populationen av aktiviteten bestäms genom att en huvuduppsättning väljs bland de inkommande övergångarna i aktiviteten.

Den utgående övergången kan bara innehålla en av de ingående övergångspopulationerna. Om aktiviteten inte är konfigurerad kommer den utgående övergången att slumpmässigt välja en av de inkommande populationerna.

>[!CAUTION]
>
>När det gäller aktiviteter av typen **AND-join** sammanfogas händelsevariablerna, men om samma variabel definieras två gånger uppstår en konflikt och värdet är fortfarande obestämt. Mer information om detta finns i [det här avsnittet](../../workflow/using/javascript-scripts-and-templates.md#event-variables).
