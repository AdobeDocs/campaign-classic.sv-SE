---
product: campaign
title: Arkitektur
description: Arbetsflöden hanteras av en specifik modul, som kan startas på flera servrar för att dela bearbetningsbelastningen
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# Arkitektur {#architecture}



Arbetsflöden hanteras av en specifik modul. Den här modulen kan startas på flera servrar för att dela bearbetningsbelastningen.

![](assets/architecture.png)

* Processen &#39;Workflow Instance Runner&#39; (runwf) kör alla åtgärder i en viss arbetsflödesinstans. När det inte finns några uppgifter att utföra just nu blir den&quot;passiv&quot;, det vill säga sparar dess status i databasen och sedan stoppas.
* Modulen Arbetsflödesserver (wfserver) övervakar aktuella arbetsflödesinstanser. När det finns en uppgift att utföra skapar den här modulen en process för att aktivera (eller återaktivera) motsvarande instans.
