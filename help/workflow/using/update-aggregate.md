---
title: Uppdatera aggregat
description: Läs mer om aktiviteten Uppdatera aggregerat arbetsflöde
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---


# Uppdatera aggregat{#update-aggregate}

Aggregat definieras på kubnivå för rapportering. En **[!UICONTROL Workflow]** flik är tillgänglig när du konfigurerar en mängd.

Mer information om kuber och hur du använder aggregat i Adobe Campaign finns i det dedikerade [avsnittet](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

Med den här **[!UICONTROL Update aggregate]** aktiviteten kan du välja vilket uppdateringsläge som ska användas: helt eller delvis.

Som standard utförs en fullständig uppdatering under varje beräkning. Om du vill aktivera en partiell uppdatering väljer du det relevanta alternativet och definierar uppdateringsvillkoren.

![](assets/s_advuser_cube_agregate_05.png)

**God praxis**: en **[!UICONTROL Scheduler]** aktivitet kan användas för att ange frekvensen för beräkningsuppdateringar.

![](assets/s_advuser_cube_agregate_04.png)

