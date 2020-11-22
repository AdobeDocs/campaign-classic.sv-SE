---
solution: Campaign Classic
product: campaign
title: SQL-kod och JavaScript-kod
description: Läs mer om arbetsflödesaktiviteter för SQL- och JavaScript-koder
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 5%

---


# SQL-kod och JavaScript-kod{#sql-code-and-javascript-code}

## SQL-kod {#sql-code}

En **[!UICONTROL SQL code]** aktivitet kör ett SQL-skript. Skriptet är en JST-mall.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   Redigerarens centrala del innehåller skriptet som ska köras. Skriptet är en JST-mall och kan därför konfigureras enligt arbetsflödeskontexten.

* **[!UICONTROL Processing errors]**

   Se [Bearbetningsfel](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

## JavaScript-kod och avancerad JavaScript-kod {#javascript-code}

**[!UICONTROL JavaScript code]** och **[!UICONTROL Advanced JavaScript code]** aktiviteter kör ett JavaScript-skript i ett arbetsflödes kontext. Mer information om skript finns i avsnittet [JavaScript-skript och -mallar](../../workflow/using/javascript-scripts-and-templates.md) .

>[!NOTE]
>
>Som standard får körningsfasen för **[!UICONTROL JavaScript code]** och **[!UICONTROL Advanced JavaScript code]** aktiviteter inte överskrida 1 timme. Efter den här fördröjningen avbryts processen med ett felmeddelande och aktivitetskörningen misslyckas.
>
>Du kan ändra den här fördröjningen i det **[!UICONTROL Stop execution after]** fält som är tillgängligt i aktivitetens egenskaper.

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**: Redigerarens centrala del innehåller skriptet som ska köras.
   * **[!UICONTROL Processing errors]**: Se [Bearbetningsfel](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**: Den första zonen i redigeraren innehåller skriptet som ska köras under det första anropet.
   * **[!UICONTROL Next calls]**: Den andra zonen i redigeraren innehåller skriptet som ska köras under nästa anrop.
   * **[!UICONTROL Transitions]**: Du kan definiera flera aktivitetsutdatagränser.
   * **[!UICONTROL Schedule]**: På fliken **[!UICONTROL Schedule]** kan du schemalägga när aktiviteten ska utlösas.
