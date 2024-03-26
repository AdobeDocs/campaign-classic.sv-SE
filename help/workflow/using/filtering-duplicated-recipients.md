---
product: campaign
title: Filtrera duplicerade mottagare
description: Lär dig filtrera duplicerade mottagare
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 8%

---

# Filtrera duplicerade mottagare {#filtering-duplicated-recipients}



I det här exemplet vill vi filtrera mottagare som visas två gånger eller flera gånger i en leverans för att återskapa duplicerade profiler.

Så här skapar du det här exemplet:

1. Dra och släpp en **[!UICONTROL Query]** i ett arbetsflöde och öppna aktiviteten.
1. Klicka **[!UICONTROL Edit query]** och ange mål- och filterdimensionerna till **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definiera följande filtervillkor för målmottagaren som finns i leveransloggen. Välj **Mottagarens leveranslogg (utsändningslogg)** i **Uttryck** kolumn, välja **finns som** i **Operator** kolumn.

   ![](assets/query_recipients_2.png)

1. Definiera följande filtervillkor för att ange leveransmålet. Välj **[!UICONTROL Internal name]** i kolumnen Uttryck och **[!UICONTROL equal to]** i kolumnen Operator.
1. Lägg till det interna namnet för målleveransen i värdekolumnen.

   ![](assets/query_recipients_3.png)

1. Med **[!UICONTROL AND]** -operatorn, upprepa samma åtgärder för att rikta in sig på andra leveranser.

   ![](assets/query_recipients_4.png)

Din utgående övergång innehåller de dubblettmottagare som är angivna i leveranserna.
