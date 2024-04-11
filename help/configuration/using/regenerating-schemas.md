---
product: campaign
title: Återskapa scheman
description: Lär dig hur du genererar om kampanjscheman
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 2%

---

# Återskapa scheman{#regenerating-schemas}

När du ändrar ett schema och sparar ändringarna genereras ett utökat schema automatiskt. Du kan dock behöva generera om scheman manuellt för att tillämpa ändringarna. Så här gör du:

1. Välj de scheman som du vill återskapa.
1. Högerklicka och välj **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Klicka **[!UICONTROL OK]** för att bekräfta och starta processen.

Du kan sedan kontrollera strukturen för det genererade schemat på flikarna Förhandsgranska och Dokumentation. Mer information finns i [Principer](../../configuration/using/data-schemas.md#principles) -avsnitt.

>[!NOTE]
>
>Om du behöver tvinga fram en omgenerering av alla scheman, till exempel för att lösa vissa beroendeproblem i de omvända länkarna, kan du starta följande kommando från Adobe Campaign programserver:
>
> `nlserver config -postupgrade -instance:`&lt;instance_name>` -force`
>
>Du måste sedan starta om Adobe Campaign programserver och koppla från/återansluta till klientkonsolen.
