---
product: campaign
title: Återskapa scheman
description: Lär dig hur du genererar om kampanjscheman
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 6c48cfea-6d20-4462-a485-71e1575a08a7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 7%

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
