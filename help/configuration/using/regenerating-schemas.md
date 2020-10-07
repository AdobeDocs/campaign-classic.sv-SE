---
title: Återskapa scheman
seo-title: Återskapa scheman
description: Återskapa scheman
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 8%

---


# Återskapa scheman{#regenerating-schemas}

När du ändrar ett schema och sparar ändringarna genereras ett utökat schema automatiskt. Du kan dock behöva generera om scheman manuellt för att tillämpa ändringarna. Så här gör du:

1. Välj de scheman som du vill återskapa.
1. Högerklicka och välj **[!UICONTROL Actions > Regenerate selected schemas...]** .
1. Klicka **[!UICONTROL OK]** för att bekräfta och starta processen.

Du kan sedan kontrollera strukturen för det genererade schemat på flikarna Förhandsgranska och Dokumentation. For more on this, refer to the [Principles](../../configuration/using/data-schemas.md#principles) section.

>[!NOTE]
>
>Om du behöver tvinga fram en omgenerering av alla scheman, till exempel för att lösa vissa beroendeproblem i de omvända länkarna, kan du starta följande kommando från Adobe Campaign programserver:
>
>**nlserver config -postupgrade -instance:`&lt;instance_name>&#39; -force**
>
>Du måste sedan starta om Adobe Campaign programserver och koppla från/återansluta till klientkonsolen.
