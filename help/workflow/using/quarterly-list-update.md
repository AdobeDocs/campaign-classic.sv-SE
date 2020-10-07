---
title: Kvartalslistuppdatering med inkrementell fråga
description: I det här fallet används en stegvis fråga för att automatiskt uppdatera en mottagarlista.
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# Kvartalslistuppdatering med inkrementell fråga {#quarterly-list-update}

I följande exempel används en [stegvis fråga](../../workflow/using/incremental-query.md) för att automatiskt uppdatera en mottagarlista. Dessa mottagare ingår i säsongskampanjer.

Eftersom dessa kampanjer lanseras i början av varje säsong för att erbjuda relevanta sportaktiviteter uppdateras dessa listor varje kvartal. Men en mottagare här får bara anges som mål en gång var 9:e månad för den här kampanjen. Detta gör att du kan fördela mottagarens frekvens för behörighet och erbjuda aktiviteter för olika årstider under åren.

![](assets/incremental_query_example.png)

1. Lägg till en inkrementell fråga samt en listuppdateringsaktivitet i ett nytt arbetsflöde.
1. Konfigurera aktivitetens flik **[!UICONTROL Incremental query]** enligt [Skapa en fråga](../../workflow/using/query.md#creating-a-query).
1. Markera **[!UICONTROL Scheduling & History]** fliken och ange sedan en 270-dagarshistorik. Målgruppen för en mottagare som redan är målinriktad kommer inte längre att gälla under en period på 270 dagar, eller ungefär 9 månader.

   Then click the **[!UICONTROL Change...]** button.

1. Om du vill att listan ska uppdateras innan säsongen börjar väljer du **[!UICONTROL Monthly]**.
1. På nästa skärm väljer du mars, juni, september och december. Välj den 20:e i månaden och välj vilken tid du vill starta arbetsflödet.
1. Välj sedan giltighetsperioden för frågan. Om du till exempel vill att den här aktiviteten ska vara permanent aktiv väljer du **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. När du har godkänt den inkrementella frågan konfigurerar du listuppdateringsaktiviteten enligt [Listuppdatering](../../workflow/using/list-update.md).

Arbetsflödet kommer därför att startas automatiskt precis innan säsongen börjar. Listan kommer att uppdateras med nya, berättigade mottagare som kan ta emot erbjudandena.
