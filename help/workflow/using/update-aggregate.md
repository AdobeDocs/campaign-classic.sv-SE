---
title: Uppdatera aggregat
seo-title: Uppdatera aggregat
description: Uppdatera aggregat
seo-description: null
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 8%

---


# Uppdatera aggregat{#update-aggregate}

Aggregat definieras på kubnivå för rapportering. En **[!UICONTROL Workflow]** flik är tillgänglig när du konfigurerar en mängd.

Mer information om kuber och hur du använder aggregat i Adobe Campaign finns i det dedikerade [avsnittet](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

Med den här **[!UICONTROL Update aggregate]** aktiviteten kan du välja vilket uppdateringsläge som ska användas: helt eller delvis.

Som standard utförs en fullständig uppdatering under varje beräkning. Om du vill aktivera en partiell uppdatering väljer du det relevanta alternativet och definierar uppdateringsvillkoren.

![](assets/s_advuser_cube_agregate_05.png)

**God praxis**: en **[!UICONTROL Scheduler]** aktivitet kan användas för att ange frekvensen för beräkningsuppdateringar.

![](assets/s_advuser_cube_agregate_04.png)

