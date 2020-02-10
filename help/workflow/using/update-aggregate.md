---
title: Uppdatera sammanställning
seo-title: Uppdatera sammanställning
description: Uppdatera sammanställning
seo-description: null
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Uppdatera sammanställning{#update-aggregate}

Aggregat definieras på kubnivå för rapportering. En **[!UICONTROL Workflow]** flik är tillgänglig när du konfigurerar en mängd.

Mer information om kuber och hur du använder aggregat i Adobe Campaign finns i det dedikerade [avsnittet](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

Med den här **[!UICONTROL Update aggregate]** aktiviteten kan du välja vilket uppdateringsläge som ska användas: helt eller delvis.

Som standard utförs en fullständig uppdatering under varje beräkning. Om du vill aktivera en partiell uppdatering väljer du det relevanta alternativet och definierar uppdateringsvillkoren.

![](assets/s_advuser_cube_agregate_05.png)

**God praxis**: en **[!UICONTROL Scheduler]** aktivitet kan användas för att ange frekvensen för beräkningsuppdateringar.

![](assets/s_advuser_cube_agregate_04.png)

