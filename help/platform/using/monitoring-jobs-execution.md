---
product: campaign
title: Övervaka körning av jobb
description: Lär dig övervaka körning av import- och exportjobb
feature: Monitoring
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 3%

---

# Övervaka körning av jobb {#monitoring-job-execution}



Du kan spåra körningen av import- och exportjobb direkt i listan över import-/exportjobb.

![](assets/s_ncs_user_export_list_and_details.png)

* På fliken **[!UICONTROL Journal]** kan du titta på loggmeddelanden om körning.
* Fliken **[!UICONTROL Rejects]** innehåller de avvisade posterna. Se [det här avsnittet](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

På fliken **[!UICONTROL General]** anger fältet **[!UICONTROL Status]** aktuell status för ett jobb.

Varje status representeras av en speciell ikon och etikett. Statuserna och ikonerna för dem listas nedan:

![](assets/s_ncs_user_export_status.png)

* **Redigering pågår**

  Jobbet skapas.

* **Körning pågår**

  Jobbet körs.

* **Avbryt**

  Klicka på knappen **[!UICONTROL Cancel]**: det pågående jobbet avbryts.

* **Avbryter**

  Kommandot för att avbryta har tagits med i beräkningen och jobbet avbryts.

* **Paus pågår**

  Klicka på **[!UICONTROL Pause]**: Jobbet pausas.

* **Pausad**

  Klicka på **[!UICONTROL Pause]**: Jobbet har pausats. Den kan startas om genom att klicka på **[!UICONTROL Start]**.

* **Slutförd**

  Jobbet har körts klart.

* **Slutförd med fel**

  Jobbet utfördes inte på grund av ett tekniskt fel.

* **Serveravstängning pågår**

  Jobbet avbryts eftersom Adobe Campaign-servern har stängts av.
