---
title: SQL-kod och JavaScript-kod
seo-title: SQL-kod och JavaScript-kod
description: SQL-kod och JavaScript-kod
seo-description: null
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 16e35b62cdf42c04139cc17645095a3d1f6e0fa7

---


# SQL-kod och JavaScript-kod{#sql-code-and-javascript-code}

## SQL-kod {#sql-code}

En **[!UICONTROL SQL code*]* -aktivitet kör ett SQL-skript. Skriptet är en JST-mall.

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

   * **[!UICONTROL Script]**:Redigerarens centrala del innehåller skriptet som ska köras.
   * **[!UICONTROL Processing errors]**:Se [Bearbetningsfel](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**:Den första zonen i redigeraren innehåller skriptet som ska köras under det första anropet.
   * **[!UICONTROL Next calls]**:Den andra zonen i redigeraren innehåller skriptet som ska köras under nästa anrop.
   * **[!UICONTROL Transitions]**:Du kan definiera flera aktivitetsutdatagränser.
   * **[!UICONTROL Schedule]**:På fliken **[!UICONTROL Schedule]** kan du schemalägga när aktiviteten ska utlösas.
