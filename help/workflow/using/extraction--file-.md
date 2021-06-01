---
product: campaign
title: Dataextrahering (fil)
description: Läs mer om arbetsflödesaktiviteten för dataextrahering (fil)
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---

# Dataextrahering (fil){#extraction-file}

Du kan extrahera data från en arbetsflödestabell i en extern fil med aktiviteten **[!UICONTROL Data extraction (file)]**.

>[!CAUTION]
>
>Den här aktiviteten måste alltid ha en inkommande övergång som innehåller de data som ska extraheras.

Så här konfigurerar du dataextrahering:

1. Ange namnet på utdatafilen: det här namnet kan innehålla variabler, infogade via personaliseringsknappen till höger om fältet.
1. Klicka på **[!UICONTROL Edit the file format...]** för att markera de data som ska extraheras.

   ![](assets/s_advuser_extract_file_param.png)

   Alternativet **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** lägger till ett extra steg för att filtrera slutresultatet av sammanställningen, till exempel för en viss inköpsordertyp, kunder som har beställt mer än 10 gånger osv.

1. Om det behövs kan du lägga till nya kolumner i utdatafilen, t.ex. genom att beräkna eller bearbeta resultat. Det gör du genom att klicka på ikonen **[!UICONTROL Add]**.

   ![](assets/s_advuser_extract_file_add_col.png)

   Klicka på ikonen **[!UICONTROL Edit expression]** på den extra raden för att definiera innehållet i den nya kolumnen.

   ![](assets/s_advuser_extract_file_add_exp.png)

   Sedan kommer du åt urvalsfönstret. Klicka på **[!UICONTROL Advanced selection]** för att välja vilken process som ska användas på data.

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   Välj önskad formel i listan.

   ![](assets/s_advuser_extract_file_agregate_values.png)

Du kan definiera en efterprocess som ska köras under dataextraheringen så att du kan komprimera eller kryptera filerna. För att göra detta måste det önskade kommandot läggas till på aktivitetens **[!UICONTROL Script]**-flik.

Mer information finns i följande avsnitt: [Zippa eller kryptera en fil](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

![](assets/postprocessing_dataextraction.png)

## Lista över sammanställningsfunktioner {#list-of-aggregate-functions}

Här följer en lista över tillgängliga sammanställningsfunktioner:

* **[!UICONTROL Count]** att räkna alla värden som inte är null i det fält som ska aggregeras, inklusive dubblettvärden (i det aggregerade fältet),

   **[!UICONTROL Distinct]** att räkna det totala antalet olika och icke-null-värden för det fält som ska aggregeras (dubblettvärden exkluderas före beräkningen),

* **[!UICONTROL Sum]** beräkna summan av värdena för ett numeriskt fält,
* **[!UICONTROL Minimum value]** beräkna minimivärdena för ett fält (numeriskt eller på annat sätt),
* **[!UICONTROL Maximum value]** att beräkna de högsta värdena för ett fält (numeriskt eller på annat sätt),
* **[!UICONTROL Average]** för att beräkna medelvärdet för ett numeriskt fälts värden.
