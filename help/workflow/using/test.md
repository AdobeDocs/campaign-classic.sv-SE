---
product: campaign
title: Test
description: Läs mer om aktiviteten Testa arbetsflöde
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%

---

# Test{#test}



En aktivitet av typen **Test** aktiverar den första övergången som uppfyller villkoret som är kopplat till den. Om inget villkor uppfylls och om alternativet **[!UICONTROL Use the default fork]** aktiveras aktiveras standardövergången.

Ett villkor är ett JavaScript-uttryck som måste utvärderas till &quot;true&quot; eller &quot;false&quot;. Om du vill ange uttrycket klickar du på ikonen till höger om namnet på villkoret och väljer sedan **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

Mer information om alla ytterligare JavaScript-funktioner och SOAP-metoder för programservern som är tillgängliga via arbetsflödet i JavaScript finns i [JSAPI-dokumentationen](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv).

Du kan också infoga variabler direkt från den här redigeraren. Mer information om hur du arbetar med variabler finns i [det här avsnittet](javascript-scripts-and-templates.md#variables).

Villkoren kan läggas till, tas bort eller ordnas i redigeringsfönstret för aktivitetsegenskapen, men kan också ändras från övergången.

Om resultatet av en beräkning ska återanvändas av olika villkor är det möjligt att beräkna det i aktivitetens initieringsskript. Resultatet måste lagras i en variabel av aktiviteten som ska användas av villkorsskripten (task.vars.xxx).
