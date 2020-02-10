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
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# SQL-kod och JavaScript-kod{#sql-code-and-javascript-code}

En **SQL-kodaktivitet** kör ett SQL-skript. Skriptet är en JST-mall.

* **[!UICONTROL Script]**

   Redigerarens centrala del innehåller skriptet som ska köras. Skriptet är en JST-mall och kan därför konfigureras enligt arbetsflödeskontexten.

* **[!UICONTROL Processing errors]**

   Se [Bearbetningsfel](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

**JavaScript-kodtypsaktiviteter** kör ett JavaScript-skript i ett arbetsflödes kontext. Mer information om skript finns i avsnittet [JavaScript-skript och -mallar](../../workflow/using/javascript-scripts-and-templates.md) .

* **[!UICONTROL Script]**

   Redigerarens centrala del innehåller skriptet som ska köras.

* **[!UICONTROL Processing errors]**

   Se [Bearbetningsfel](../../workflow/using/monitoring-workflow-execution.md#processing-errors).

En **avancerad JavaScript-kodaktivitet** kör ett JavaScript-skript i ett arbetsflödes sammanhang. Mer information om skript finns i [JavaScript-skript och -mallar](../../workflow/using/javascript-scripts-and-templates.md).

* **[!UICONTROL First call]**

   Den första zonen i redigeraren innehåller skriptet som ska köras under det första anropet.

* **[!UICONTROL Next calls]**

   Den andra zonen i redigeraren innehåller skriptet som ska köras under nästa anrop.

* **[!UICONTROL Transitions]**

   Du kan definiera flera aktivitetsutdatagränser.

* **[!UICONTROL Schedule]**

   På fliken **[!UICONTROL Schedule]** kan du schemalägga när aktiviteten ska utlösas.

