---
product: campaign
title: SQL-kod och JavaScript-kod
description: Läs mer om arbetsflödesaktiviteter för SQL- och JavaScript-koder
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---

# SQL-kod och JavaScript-kod{#sql-code-and-javascript-code}

![](../../assets/common.svg)

## SQL-kod {#sql-code}

En **[!UICONTROL SQL code]**-aktivitet kör ett SQL-skript. Skriptet är en JST-mall.

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   Redigerarens centrala del innehåller skriptet som ska köras. Skriptet är en JST-mall och kan därför konfigureras enligt arbetsflödeskontexten.

* **[!UICONTROL Processing errors]**

   Se [Bearbetningsfel](monitoring-workflow-execution.md#processing-errors).

## JavaScript-kod och avancerad JavaScript-kod {#javascript-code}

**[!UICONTROL JavaScript code]** och  **[!UICONTROL Advanced JavaScript code]** aktiviteter kör ett JavaScript-skript i ett arbetsflödes sammanhang. Mer information om skript finns i avsnittet [JavaScript-skript och mallar](javascript-scripts-and-templates.md).

### Körningsfördröjning {#exec-delay}

Från och med version 20.2 har en körningsfördröjning lagts till i aktiviteterna **[!UICONTROL JavaScript code]** och **[!UICONTROL Advanced JavaScript code]**. Som standard får körningsfasen inte överskrida 1 timme. Efter den här fördröjningen avbryts processen med ett felmeddelande och aktivitetskörningen misslyckas.

Du kan ändra den här fördröjningen i fältet **[!UICONTROL Stop execution after]** som är tillgängligt i de här aktiviteterna.

Om du vill ignorera den här gränsen måste du ange värdet **0**.

### JavaScript-kod {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**: Redigerarens centrala del innehåller skriptet som ska köras.

* **[!UICONTROL Process errors]**: Se  [Bearbetningsfel](monitoring-workflow-execution.md#processing-errors).

### Avancerad JavaScript-kod {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**: Den första zonen i redigeraren innehåller skriptet som ska köras under det första anropet.
* **[!UICONTROL Next calls]**: Den andra zonen i redigeraren innehåller skriptet som ska köras under nästa anrop.
* **[!UICONTROL Transitions]**: Du kan definiera flera aktivitetsutdatagränser.
* **[!UICONTROL Schedule]**: På  **[!UICONTROL Schedule]** fliken kan du schemalägga när aktiviteten ska utlösas.

Avancerad JavaScript är en beständig uppgift och återkommer regelbundet om den inte har markerats som slutförd. Om du vill avsluta aktiviteten och förhindra framtida återkallningar måste du använda metoden **task.setCompleted()** i avsnittet **[!UICONTROL Next calls]**:

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
