---
title: Ändra datakälla
description: Läs mer om Ändra datakällaktivitet
feature: Workflows, Data Management, Federated Data Access
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---

# Ändra datakälla {#change-data-source}

>[!NOTE]
>
> The **[!UICONTROL Change data source]** aktiviteten är bara tillgänglig med **[!UICONTROL Access to external data (Federated Data Access)]** paket. Mer information om Adobe Campaign Classic inbyggda paket finns i [page](../../installation/using/installing-campaign-standard-packages.md).

The **[!UICONTROL Change data source]** kan du ändra datakällan för ett arbetsflöde **[!UICONTROL Working table]**. Detta ger större flexibilitet att hantera data över olika datakällor, som FDA, FFDA och lokala databaser.

The **[!UICONTROL Working table]** gör att Adobe Campaign Classic arbetsflöde kan hantera data och dela data med arbetsflödesaktiviteter.
Som standard är **[!UICONTROL Working table]** skapas i samma databas som källan för de data som vi frågar efter.

När du till exempel frågar **[!UICONTROL Profiles]** tabellen, som lagras i molndatabasen, skapar du en **[!UICONTROL Working table]** i samma molndatabas.
Om du vill ändra detta kan du lägga till **[!UICONTROL Change Data Source]** aktivitet för att välja en annan datakälla för **[!UICONTROL Working table]**.

Observera att när du använder **[!UICONTROL Change Data Source]** måste du växla tillbaka till molndatabasen för att kunna fortsätta med arbetsflödeskörningen.

Så här använder du **[!UICONTROL Change Data Source]** aktivitet:

1. Skapa ett arbetsflöde.

1. Fråga målmottagarna med en **[!UICONTROL Query]** aktivitet.

   Mer information om **[!UICONTROL Query]** aktivitet, se [page](../../workflow/using/query.md#creating-a-query).

1. Från **[!UICONTROL Targeting]** flik, lägga till **[!UICONTROL Change data source]** aktivitet.

   ![](assets/change-data-source.png)

1. Dubbelklicka på **[!UICONTROL Change data source]** aktivitet att välja **[!UICONTROL Default data source]**.

   Arbetstabellen, som innehåller resultatet av frågan, flyttas sedan till PostgreSQL-standarddatabasen.

   ![](assets/change-data-source_2.png)

1. Från **[!UICONTROL Actions]** tabb, dra och släppa **[!UICONTROL JavaScript code]** för att utföra enhetsåtgärder i arbetsregistret.

   Mer information om **[!UICONTROL JavaScript code]** aktivitet, se [JavaScript-kod och avancerad JavaScript-kod](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) sida.

1. Lägg till ytterligare **[!UICONTROL Change data source]** aktivitet för att växla tillbaka till molndatabasen.

1. Dubbelklicka på aktiviteten och välj **[!UICONTROL Active FDA external account]** sedan motsvarar **[!UICONTROL External database]** externt konto.

   ![](assets/change-data-source_3.png)

1. Nu kan du starta arbetsflödet.
