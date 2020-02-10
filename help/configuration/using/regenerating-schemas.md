---
title: Återskapar scheman
seo-title: Återskapar scheman
description: Återskapar scheman
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Återskapar scheman{#regenerating-schemas}

När du ändrar ett schema och sparar ändringarna genereras ett utökat schema automatiskt. Du kan dock behöva generera om scheman manuellt för att tillämpa ändringarna. Så här gör du:

1. Välj de scheman som du vill återskapa.
1. Högerklicka och välj **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Klicka **[!UICONTROL OK]** för att bekräfta och starta processen.

Du kan sedan kontrollera strukturen för det genererade schemat på flikarna Förhandsgranska och Dokumentation. Mer information finns i avsnittet [Principer](../../configuration/using/data-schemas.md#principles) .

>[!NOTE]
>
>Om du behöver tvinga fram en omgenerering av alla scheman, till exempel för att lösa vissa beroendeproblem i de omvända länkarna, kan du starta följande kommando från Adobe Campaign-programservern:

>**nlserver config -postupgrade -instance:`&lt;instance_name>&#39; -force**

>Du måste sedan starta om Adobe Campaign-programservern och koppla från/återansluta till klientkonsolen.

