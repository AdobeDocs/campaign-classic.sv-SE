---
solution: Campaign Classic
product: campaign
title: Övervaka körning av jobb
description: Lär dig hur du övervakar körning av import- och exportjobb.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 3%

---


# Körning av övervakningsjobb {#monitoring-job-execution}

Du kan spåra körningen av import- och exportjobb direkt i listan över import-/exportjobb.

![](assets/s_ncs_user_export_list_and_details.png)

* På fliken **[!UICONTROL Journal]** kan du titta i loggmeddelanden om körning.
* Fliken **[!UICONTROL Rejects]** innehåller de avvisade posterna. Se [det här avsnittet](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

På fliken **[!UICONTROL General]** anger fältet **[!UICONTROL Status]** aktuell status för ett jobb.

Varje status representeras av en speciell ikon och etikett. Statuserna och ikonerna för dem listas nedan:

![](assets/s_ncs_user_export_status.png)

* **Redigering pågår**

   Jobbet skapas.

* **Körning pågår**

   Jobbet körs.

* **Avbryt**

   Klicka på knappen **[!UICONTROL Cancel]**: jobbet avbryts.

* **Avbokning pågår**

   Kommandot för att avbryta har tagits med i beräkningen och jobbet avbryts.

* **Paus pågår**

   Klicka på **[!UICONTROL Pause]**: jobbet pausas.

* **Pausad**

   Klicka på **[!UICONTROL Pause]**: jobbet har pausats. Du kan starta om den genom att klicka på **[!UICONTROL Start]**.

* **Slutförd**

   Jobbet har körts klart.

* **Slutförd med fel**

   Jobbet utfördes inte på grund av ett tekniskt fel.

* **Serveravstängning pågår**

   Jobbet avbryts eftersom Adobe Campaign-servern har stängts av.
