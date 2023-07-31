---
product: campaign
title: Övervaka körning av jobb
description: Lär dig övervaka körning av import- och exportjobb
feature: Monitoring
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 5%

---

# Övervaka körning av jobb {#monitoring-job-execution}



Du kan spåra körningen av import- och exportjobb direkt i listan över import-/exportjobb.

![](assets/s_ncs_user_export_list_and_details.png)

* The **[!UICONTROL Journal]** -fliken kan du titta i loggmeddelanden som rör körning.
* The **[!UICONTROL Rejects]** -fliken innehåller de avvisade posterna. Se [det här avsnittet](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error).

I **[!UICONTROL General]** -fliken, **[!UICONTROL Status]** fältet anger aktuell status för ett jobb.

Varje status representeras av en speciell ikon och etikett. Statuserna och ikonerna för dem listas nedan:

![](assets/s_ncs_user_export_status.png)

* **Redigering pågår**

  Jobbet skapas.

* **Körning pågår**

  Jobbet körs.

* **Avbryt**

  Klicka på **[!UICONTROL Cancel]** knapp: det pågående jobbet avbryts.

* **Avbokning pågår**

  Kommandot för att avbryta har tagits med i beräkningen och jobbet avbryts.

* **Paus pågår**

  Klicka **[!UICONTROL Pause]**: jobbet pausas.

* **Pausad**

  Klicka **[!UICONTROL Pause]**: jobbet har pausats. Du kan starta om programmet genom att klicka på **[!UICONTROL Start]**.

* **Slutförd**

  Jobbet har körts klart.

* **Slutförd med fel**

  Jobbet utfördes inte på grund av ett tekniskt fel.

* **Serveravstängning pågår**

  Jobbet avbryts eftersom Adobe Campaign-servern har stängts av.
