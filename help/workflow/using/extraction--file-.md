---
title: Dataextrahering (fil)
description: Läs mer om arbetsflödesaktiviteten för dataextrahering (fil)
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---


# Dataextrahering (fil){#extraction-file}

Du kan extrahera data från en arbetsflödestabell i en extern fil med hjälp av **[!UICONTROL Data extraction (file)]** aktiviteten.

>[!CAUTION]
>
>Den här aktiviteten måste alltid ha en inkommande övergång som innehåller de data som ska extraheras.

Så här konfigurerar du dataextrahering:

1. Ange namnet på utdatafilen: det här namnet kan innehålla variabler, infogade via personaliseringsknappen till höger om fältet.
1. Klicka **[!UICONTROL Edit the file format...]** för att markera de data som ska extraheras.

   ![](assets/s_advuser_extract_file_param.png)

   Alternativet **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** lägger till ett extra steg för att filtrera slutresultatet av sammanställningen, till exempel för en viss inköpsordertyp, kunder som har beställt mer än 10 gånger osv.

1. Om det behövs kan du lägga till nya kolumner i utdatafilen, t.ex. genom att beräkna eller bearbeta resultat. Klicka på **[!UICONTROL Add]** ikonen om du vill göra det.

   ![](assets/s_advuser_extract_file_add_col.png)

   Klicka på **[!UICONTROL Edit expression]** ikonen på den andra raden för att definiera innehållet i den nya kolumnen.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Sedan kommer du åt urvalsfönstret. Klicka **[!UICONTROL Advanced selection]** för att välja vilken process som ska användas på data.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Välj önskad formel i listan.

   ![](assets/s_advuser_extract_file_agregate_values.png)

Du kan definiera en efterprocess som ska köras under dataextraheringen så att du kan komprimera eller kryptera filerna. För att kunna göra detta måste du lägga till det önskade kommandot på aktivitetens **[!UICONTROL Script]** flik.

Mer information finns i följande avsnitt: [Zippa eller kryptera en fil](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

![](assets/postprocessing_dataextraction.png)

## List of aggregate functions {#list-of-aggregate-functions}

Här följer en lista över tillgängliga sammanställningsfunktioner:

* **[!UICONTROL Count]** att räkna alla värden som inte är null i det fält som ska aggregeras, inklusive dubblettvärden (i det aggregerade fältet),

   **[!UICONTROL Distinct]** att räkna det totala antalet olika och icke-null-värden för det fält som ska aggregeras (dubblettvärden exkluderas före beräkningen),

* **[!UICONTROL Sum]** beräkna summan av värdena för ett numeriskt fält,
* **[!UICONTROL Minimum value]** beräkna minimivärdena för ett fält (numeriskt eller på annat sätt),
* **[!UICONTROL Maximum value]** att beräkna de högsta värdena för ett fält (numeriskt eller på annat sätt),
* **[!UICONTROL Average]** för att beräkna medelvärdet för ett numeriskt fälts värden.

