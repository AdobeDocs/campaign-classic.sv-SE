---
product: campaign
title: Kvartalsvis listuppdatering med en inkrementell fråga
description: I det här fallet används en stegvis fråga för att automatiskt uppdatera en mottagarlista.
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---

# Kvartalsvis listuppdatering med en inkrementell fråga {#quarterly-list-update}

![](../../assets/common.svg)

I följande exempel används en [inkrementell fråga](incremental-query.md) för att automatiskt uppdatera en mottagarlista. Dessa mottagare ingår i säsongskampanjer.

Eftersom dessa kampanjer lanseras i början av varje säsong för att erbjuda relevanta sportaktiviteter uppdateras dessa listor varje kvartal. Men en mottagare här får bara anges som mål en gång var 9:e månad för den här kampanjen. Detta gör att du kan fördela mottagarens frekvens för behörighet och erbjuda aktiviteter för olika årstider under åren.

![](assets/incremental_query_example.png)

1. Lägg till en inkrementell fråga samt en listuppdateringsaktivitet i ett nytt arbetsflöde.
1. Konfigurera fliken **[!UICONTROL Incremental query]** för aktiviteten enligt [Skapa en fråga](query.md#creating-a-query).
1. Välj fliken **[!UICONTROL Scheduling & History]** och ange sedan en 270-dagarshistorik. Målgruppen för en mottagare som redan är målinriktad kommer inte längre att gälla under en period på 270 dagar, eller ungefär 9 månader.

   Klicka sedan på knappen **[!UICONTROL Change...]**.

1. Välj **[!UICONTROL Monthly]** om du vill att listan ska uppdateras före början av varje säsong.
1. På nästa skärm väljer du mars, juni, september och december. Välj den 20:e i månaden och välj vilken tid du vill starta arbetsflödet.
1. Välj sedan giltighetsperioden för frågan. Om du till exempel vill att den här aktiviteten ska vara permanent aktiv väljer du **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. När du har godkänt den inkrementella frågan konfigurerar du listuppdateringsaktiviteten enligt [Listuppdatering](list-update.md).

Arbetsflödet kommer därför att startas automatiskt precis innan säsongen börjar. Listan kommer att uppdateras med nya, berättigade mottagare som kan ta emot erbjudandena.
