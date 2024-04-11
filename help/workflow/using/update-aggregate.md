---
product: campaign
title: Uppdatera aggregat
description: Läs mer om aktiviteten Uppdatera aggregerat arbetsflöde
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# Uppdatera aggregat{#update-aggregate}



Aggregat definieras på kubnivå för rapportering. A **[!UICONTROL Workflow]** -fliken är tillgänglig när du konfigurerar en mängd.

Aggregat är användbara när du hanterar stora datavolymer. De uppdateras automatiskt baserat på inställningarna som anges i den dedikerade arbetsflödesrutan, så att de data som samlats in senast kan integreras med indikatorerna

Aggregat definieras på den relevanta fliken för varje kub.

![](assets/s_advuser_cube_agregate_01.png)


The **[!UICONTROL Update aggregate]** Med -aktiviteten kan du välja det uppdateringsläge som ska användas: helt eller delvis.

Som standard utförs en fullständig uppdatering under varje beräkning. Om du vill aktivera en partiell uppdatering väljer du det relevanta alternativet och definierar uppdateringsvillkoren.

![](assets/s_advuser_cube_agregate_05.png)

**God praxis**: a **[!UICONTROL Scheduler]** kan användas för att ange frekvensen för uppdateringar av beräkningar.

![](assets/s_advuser_cube_agregate_04.png)
