---
title: Inkrementell fråga
seo-title: Inkrementell fråga
description: Inkrementell fråga
seo-description: null
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Inkrementell fråga{#incremental-query}

Med en stegvis fråga kan du regelbundet välja ett mål baserat på ett villkor, samtidigt som du utesluter de personer som redan är målinriktade för det här kriteriet.

Populationen som redan är mål lagras i minnet efter arbetsflödesinstans och efter aktivitet, vilket innebär att två arbetsflöden som startas från samma mall inte delar samma logg. Två uppgifter som baseras på samma inkrementella fråga för samma arbetsflödesinstans använder däremot samma logg.

Frågan definieras på samma sätt som för vanliga frågor (se [Skapa en fråga](../../workflow/using/query.md#creating-a-query)), men körningen är schemalagd.

>[!CAUTION]
>
>Om resultatet av en inkrementell fråga är lika med **0** under en av dess körningar pausas arbetsflödet tills frågan körs nästa gång. De övergångar och aktiviteter som följer efter den stegvisa frågan bearbetas därför inte före nästa körning.

Så här gör du:

1. Välj **[!UICONTROL Scheduling & History]** alternativet på **[!UICONTROL Schedule execution]** fliken. Aktiviteten förblir aktiv när den har skapats och aktiveras endast vid de tidpunkter som anges i schemat för körning av frågan. Om alternativet är inaktiverat körs frågan omedelbart **och på en gång**.
1. Klicka på **[!UICONTROL Change]** knappen.

   I **[!UICONTROL Schedule editing wizard]** fönstret kan du konfigurera typ av frekvens, återkommande händelser och händelsegiltighetsperiod.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Klicka **[!UICONTROL Finish]** för att spara schemat.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. I det nedre avsnittet på **[!UICONTROL Scheduling & History]** fliken kan du välja hur många dagar som ska tas med i historiken.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      Mottagare som redan är målinriktade kan loggas i högst ett antal dagar från den dag då de var målinriktade. Om värdet är noll rensas mottagarna aldrig från loggen.

   * **[!UICONTROL Keep history when starting]**

      Med det här alternativet kan du inte rensa loggen när aktiviteten är aktiverad.

   * **[!UICONTROL SQL table name]**

      Med den här parametern kan du överlagra SQL-standardtabellen som innehåller historikdata.

## Exempel på en inkrementell fråga: kvartalslisteuppdatering {#example-of-an-incremental-query--quarterly-list-update}

I följande exempel används en stegvis fråga för att automatiskt uppdatera en mottagarlista. Dessa mottagare ingår i säsongskampanjer.

Eftersom dessa kampanjer lanseras i början av varje säsong för att erbjuda relevanta sportaktiviteter uppdateras dessa listor varje kvartal. Men en mottagare här får bara anges som mål en gång var 9:e månad för den här kampanjen. Detta gör att du kan fördela mottagarens frekvens för behörighet och erbjuda aktiviteter för olika årstider under åren.

![](assets/incremental_query_example.png)

1. Lägg till en inkrementell fråga samt en listuppdateringsaktivitet i ett nytt arbetsflöde.
1. Konfigurera aktivitetens flik **[!UICONTROL Incremental query]** enligt [Skapa en fråga](../../workflow/using/query.md#creating-a-query).
1. Markera **[!UICONTROL Scheduling & History]** fliken och ange sedan en 270-dagarshistorik. Målgruppen för en mottagare som redan är målinriktad kommer inte längre att gälla under en period på 270 dagar, eller ungefär 9 månader.

   Klicka sedan på **[!UICONTROL Change...]** knappen.

1. Om du vill att listan ska uppdateras innan säsongen börjar väljer du **[!UICONTROL Monthly]**.
1. På nästa skärm väljer du mars, juni, september och december. Välj den 20:e i månaden och välj vilken tid du vill starta arbetsflödet.
1. Välj sedan giltighetsperioden för frågan. Om du till exempel vill att den här aktiviteten ska vara permanent aktiv väljer du **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. När du har godkänt den inkrementella frågan konfigurerar du listuppdateringsaktiviteten enligt [Listuppdatering](../../workflow/using/list-update.md).

Arbetsflödet kommer därför att startas automatiskt precis innan säsongen börjar. Listan kommer att uppdateras med nya, berättigade mottagare som kan ta emot erbjudandena.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar den population som frågan riktar sig till. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.
