---
solution: Campaign Classic
product: campaign
title: Uppdatera aggregat
description: Läs mer om aktiviteten Uppdatera aggregerat arbetsflöde
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---


# Uppdatera aggregat{#update-aggregate}

Aggregat definieras på kubnivå för rapportering. En **[!UICONTROL Workflow]**-flik är tillgänglig när du konfigurerar en mängd.

Mer information om kuber och hur du använder aggregat i Adobe Campaign finns i [avsnittet](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

Med aktiviteten **[!UICONTROL Update aggregate]** kan du välja det uppdateringsläge som ska användas: helt eller delvis.

Som standard utförs en fullständig uppdatering under varje beräkning. Om du vill aktivera en partiell uppdatering väljer du det relevanta alternativet och definierar uppdateringsvillkoren.

![](assets/s_advuser_cube_agregate_05.png)

**God praxis**: en  **[!UICONTROL Scheduler]** aktivitet kan användas för att ange frekvensen för uppdateringar av beräkningar.

![](assets/s_advuser_cube_agregate_04.png)

