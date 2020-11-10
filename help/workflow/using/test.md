---
title: Test
description: Läs mer om aktiviteten Testa arbetsflöde
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 5%

---


# Test{#test}

A **Test** type activity activates the first transition that satisfies the condition associated with it. If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

Ett villkor är ett JavaScript-uttryck som måste utvärderas till true eller false. Om du vill ange uttrycket klickar du på ikonen till höger om namnet på villkoret och väljer sedan **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Mer information om alla ytterligare JavaScript-funktioner och SOAP-metoder för programservern som är tillgängliga via JavaScript i arbetsflödet finns i [JSAPI-dokumentationen](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Du kan också infoga variabler direkt från den här redigeraren. Mer information om hur du arbetar med variabler finns i [det här avsnittet](../../workflow/using/javascript-scripts-and-templates.md#variables).

Villkoren kan läggas till, tas bort eller ordnas i redigeringsfönstret för aktivitetsegenskapen, men kan också ändras från övergången.

Om resultatet av en beräkning ska återanvändas av olika villkor är det möjligt att beräkna det i aktivitetens initieringsskript. Resultatet måste lagras i en variabel av aktiviteten som ska användas av villkorsskripten (task.vars.xxx).
