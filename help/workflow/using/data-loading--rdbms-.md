---
title: Datainläsning (RDBMS)
seo-title: Datainläsning (RDBMS)
description: Datainläsning (RDBMS)
seo-description: null
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Datainläsning (RDBMS){#data-loading-rdbms}

Med den här **[!UICONTROL Data loading (RDBMS)]** aktiviteten kan du få åtkomst till den externa databasen direkt och bara samla in de data som krävs för målinriktning.

För att förbättra prestandan rekommenderar vi att du använder frågeaktiviteten (där data i en extern databas kan användas). Mer information finns i [Åtkomst till en extern databas (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

Åtgärden är följande:

1. Markera datakällan i listan och ange namnet på tabellen som innehåller de data som ska extraheras.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Namnet på tabellen som anges i motsvarande fält används som mall för datainsamling i den externa databasen. Namnet på tabellen som bearbetas av arbetsflödet kan beräknas eller förmedlas av den inkommande övergången för datainläsningsaktiviteten. Om du vill markera tabellen som ska användas klickar du på **[!UICONTROL Advanced..]**. och välj **[!UICONTROL Specified in the transition]** alternativet eller **[!UICONTROL Explicit]** .

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Klicka på **[!UICONTROL Select the columns to extract...]** länken för att välja vilka data som ska samlas in i databasen.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Du kan definiera ett filter för dessa data. Klicka på **[!UICONTROL Edit query....]** länken om du vill göra det.

   De data som samlas in på det här sättet kan användas under hela arbetsflödets livscykel.

