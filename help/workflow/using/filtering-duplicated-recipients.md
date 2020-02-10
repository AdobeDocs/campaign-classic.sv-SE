---
title: Filtrera duplicerade mottagare
description: Lär dig filtrera duplicerade mottagare
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Filtrera duplicerade mottagare {#filtering-duplicated-recipients}

I det här exemplet vill vi filtrera mottagare som visas två gånger eller flera gånger i en leverans för att återskapa duplicerade profiler.

Så här skapar du det här exemplet:

1. Dra och släpp en **[!UICONTROL Query]** aktivitet i ett arbetsflöde och öppna aktiviteten.
1. Klicka **[!UICONTROL Edit query]** och ange mål- och filtreringsdimensioner till **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definiera följande filtervillkor för målmottagaren som finns i leveransloggen. Välj **Leveranslogg för mottagare (utsändningslogg)** i kolumnen **Uttryck** . Välj **till exempel** i kolumnen **Operator** .

   ![](assets/query_recipients_2.png)

1. Definiera följande filtervillkor för att ange leveransmålet. Välj **[!UICONTROL Internal name]** i kolumnen Uttryck och **[!UICONTROL equal to]** i kolumnen Operator.
1. Lägg till det interna namnet för målleveransen i värdekolumnen.

   ![](assets/query_recipients_3.png)

1. Använd en **[!UICONTROL AND]** operator och upprepa samma åtgärder för att rikta in andra leveranser.

   ![](assets/query_recipients_4.png)

Din utgående övergång innehåller de dubblettmottagare som är angivna i leveranserna.
