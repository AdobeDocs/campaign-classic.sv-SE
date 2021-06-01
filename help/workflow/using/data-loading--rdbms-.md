---
product: campaign
title: Datainläsning (RDBMS)
description: Läs mer om arbetsflödesaktivitet för datainläsning (RDBMS)
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# Datainläsning (RDBMS){#data-loading-rdbms}

Med aktiviteten **[!UICONTROL Data loading (RDBMS)]** kan du komma åt den här externa databasen direkt och endast samla in de data som krävs för målanpassning.

För att förbättra prestandan rekommenderar vi att du använder frågeaktiviteten (där data i en extern databas kan användas). Mer information finns i [Åtkomst till en extern databas (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

Åtgärden är följande:

1. Markera datakällan i listan och ange namnet på tabellen som innehåller de data som ska extraheras.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Namnet på tabellen som anges i motsvarande fält används som mall för datainsamling i den externa databasen. Namnet på tabellen som bearbetas av arbetsflödet kan beräknas eller förmedlas av den inkommande övergången för datainläsningsaktiviteten. Klicka på **[!UICONTROL Advanced..]** om du vill välja vilken tabell som ska användas. och välj alternativet **[!UICONTROL Specified in the transition]** eller **[!UICONTROL Explicit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Klicka på länken **[!UICONTROL Select the columns to extract...]** för att välja vilka data som ska samlas in i databasen.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Du kan definiera ett filter för dessa data. Det gör du genom att klicka på länken **[!UICONTROL Edit query....]**.

   De data som samlas in på det här sättet kan användas under hela arbetsflödets livscykel.
