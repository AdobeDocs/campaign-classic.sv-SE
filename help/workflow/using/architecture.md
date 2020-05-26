---
title: Arkitektur
description: Arbetsflödena hanteras av en specifik modul som kan startas på flera servrar för att dela bearbetningsbelastningen.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# Arkitektur {#architecture}

Arbetsflöden hanteras av en specifik modul. Den här modulen kan startas på flera servrar för att dela bearbetningsbelastningen.

![](assets/architecture.png)

* Processen &#39;Workflow Instance Runner&#39; (runwf) kör alla åtgärder i en viss arbetsflödesinstans. När det inte finns några uppgifter att utföra just nu blir den&quot;passiv&quot;, det vill säga sparar dess status i databasen och sedan stoppas.
* Modulen Arbetsflödesserver (wfserver) övervakar aktuella arbetsflödesinstanser. När det finns en uppgift att utföra skapar den här modulen en process för att aktivera (eller återaktivera) motsvarande instans.

När en operator utför en åtgärd i ett arbetsflöde (start, stopp, paus osv.), utförs åtgärden inte direkt av modulen nlserver, utan placeras i en kö för att bearbetas av arbetsflödesmodulen.
