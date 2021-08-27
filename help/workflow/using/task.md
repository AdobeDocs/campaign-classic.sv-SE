---
product: campaign
title: Uppgift
description: Läs mer om aktivitetsarbetsflödesaktiviteten
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 8549bf8c-ba23-44cb-95f2-c50f2d0f5479
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 3%

---

# Uppgift{#task}

![](../../assets/common.svg)

>[!AVAILABILITY]
>
>:warning: Den här funktionen är bara tillgänglig i Campaign Classic v7. [Läs mer](../../mrm/using/creating-and-managing-tasks.md)

I ett kampanjarbetsflöde kan du ange två scenarier med aktiviteten **[!UICONTROL Task]**: den första om uppgiften är slutförd och den andra om uppgiften inte är slutförd (om den markerats manuellt som ofullständig eller om den förfaller).

![](assets/mrm_task_in_workflow.png)

Hur du konfigurerar och kör en åtgärd beskrivs i [Campaign Classic v7-dokumentationen](../../mrm/using/creating-and-managing-tasks.md).

![](assets/wkf_task_activity.png)

Med alternativet **[!UICONTROL Resources]** kan du definiera flera operatorer samt ett godkännandeschema för aktiviteten. Om personen som godkänner avvisar, leder detta inte till att själva uppgiften avvisas.
