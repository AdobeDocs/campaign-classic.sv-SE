---
title: Ändra datakälla
description: Läs mer om Ändra datakällaktivitet
audience: workflow
content-type: reference
topic-tags: targeting-activities
source-git-commit: 9fc4add3f12e3f06b031c4969bd8409c67e4359e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Ändra datakälla {#change-data-source}

>[!NOTE]
>
> Aktiviteten **[!UICONTROL Change data source]** är bara tillgänglig med **[!UICONTROL Access to external data (Federated Data Access)]**-paketet. Mer information om Adobe Campaign Classic inbyggda paket finns på den här [sidan](../../installation/using/installing-campaign-standard-packages.md).

Med aktiviteten **[!UICONTROL Change data source]** kan du ändra datakällan för ett arbetsflöde **[!UICONTROL Working table]**. Detta ger större flexibilitet att hantera data över olika datakällor, som FDA, FFDA och lokala databaser.

Med **[!UICONTROL Working table]** kan Adobe Campaign Classic-arbetsflödet hantera data och dela data med arbetsflödesaktiviteterna.
Som standard skapas **[!UICONTROL Working table]** i samma databas som källan för de data vi söker efter.

Om du till exempel skickar en fråga till tabellen **[!UICONTROL Profiles]** som finns i molndatabasen, skapar du en **[!UICONTROL Working table]** i samma molndatabas.
Om du vill ändra detta kan du lägga till aktiviteten **[!UICONTROL Change Data Source]** och välja en annan datakälla för din **[!UICONTROL Working table]**.

Observera, att när du använder aktiviteten **[!UICONTROL Change Data Source]** måste du växla tillbaka till molndatabasen för att kunna fortsätta med arbetsflödeskörningen.

Så här använder du aktiviteten **[!UICONTROL Change Data Source]**:

1. Skapa ett arbetsflöde.

1. Fråga målmottagarna med en **[!UICONTROL Query]**-aktivitet.

   Mer information om aktiviteten **[!UICONTROL Query]** finns på den här [sidan](../../workflow/using/query.md#creating-a-query).

1. Lägg till en **[!UICONTROL Change data source]**-aktivitet från fliken **[!UICONTROL Targeting]**.

   ![](assets/change-data-source.png)

1. Dubbelklicka på din **[!UICONTROL Change data source]**-aktivitet för att välja **[!UICONTROL Default data source]**.

   Arbetstabellen, som innehåller resultatet av frågan, flyttas sedan till PostgreSQL-standarddatabasen.

   ![](assets/change-data-source_2.png)

1. Dra och släpp en **[!UICONTROL JavaScript code]**-aktivitet från fliken **[!UICONTROL Actions]** för att utföra enhetsåtgärder i arbetsregistret.

   Mer information om aktiviteten **[!UICONTROL JavaScript code]** finns på sidan [JavaScript-kod och Avancerad JavaScript-kod](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

1. Lägg till ytterligare en **[!UICONTROL Change data source]**-aktivitet för att växla tillbaka till molndatabasen.

1. Dubbelklicka på din aktivitet och välj **[!UICONTROL Active FDA external account]** och sedan det motsvarande externa **[!UICONTROL External database]**-kontot.

   ![](assets/change-data-source_3.png)

1. Nu kan du starta arbetsflödet.
