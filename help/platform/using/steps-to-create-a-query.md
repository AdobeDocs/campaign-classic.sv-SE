---
product: campaign
title: Steg för att skapa en fråga
description: Steg för att skapa en fråga
feature: Query Editor
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 2%

---

# Steg för att skapa en fråga{#steps-to-create-a-query}



Så här skapar du en fråga i Adobe Campaign:

1. Markera arbetsregistret. Se [Steg 1 - Välj en tabell](#step-1---choose-a-table).
1. Markera de data som ska extraheras. Se [Steg 2 - Välj data att extrahera](#step-2---choose-data-to-extract).
1. Definiera datasorteringssekvensen. Se [Steg 3 - Sortera data](#step-3---sort-data).
1. Filtrera data. Se [Steg 4 - Filtrera data](#step-4---filter-data).
1. Formatera data. Se [Steg 5 - Formatera data](#step-5---format-data).
1. Visa resultatet. Se [Steg 6 - Förhandsgranska data](#step-6---preview-data).

>[!NOTE]
>
>Alla dessa steg är tillgängliga i den allmänna frågeredigeraren. När en fråga skapas i en annan kontext kan vissa steg utelämnas.\
>Frågeaktiviteten visas i [det här avsnittet](../../workflow/using/query.md).

## Steg 1 - Välj en tabell {#step-1---choose-a-table}

Markera tabellen som innehåller de data du vill fråga i dialogrutan **[!UICONTROL Document type]** -fönstret. Om det behövs kan du filtrera data med filterfältet eller **[!UICONTROL Filters]** -knappen.

![](assets/query_editor_nveau_21.png)

## Steg 2 - Välj data att extrahera {#step-2---choose-data-to-extract}

I **[!UICONTROL Data to extract]** markerar du de data som ska visas: dessa fält utgör utdatakolumnerna.

Välj till exempel **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** och **[!UICONTROL City]**. Resultatet ordnas utifrån det här valet. Använd de blå pilarna till höger om fönstret för att ändra kolumnordningen.

![](assets/query_editor_nveau_01.png)

Du kan redigera ett uttryck genom att infoga en formel i det eller köra en process på en sammanställningsfunktion. Klicka på **[!UICONTROL Expression]** kolumnfält och sedan markera **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

Det går att gruppera utdatakolumndata: det gör du genom att markera **[!UICONTROL Yes]** i **[!UICONTROL Group]** kolumn i **[!UICONTROL Data to extract]** -fönstret. Den här funktionen genererar ett resultat runt den markerade grupperingsaxeln. Ett exempel på en fråga med gruppering finns i [det här avsnittet](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* The **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** kan du &quot;gruppera efter&quot; och välja vad som har grupperats (&quot;att&quot;). Den här funktionen gäller för alla fält i utdatakolumnen. Med det här alternativet kan du till exempel gruppera alla val för en utdatakolumn och återställa en viss typ av information, till exempel mottagare mellan 35 och 50.

  Mer information om detta finns i [det här avsnittet](../../workflow/using/querying-using-grouping-management.md).

* The **[!UICONTROL Remove duplicate rows (DISTINCT)]** kan du duplicera identiska resultat som du får i utdatakolumnen. Om du till exempel gör en inventering genom att markera fälten Efternamn, Förnamn och E-post i utdatakolumnen, kommer de som har identiska data att tas bort, eftersom det innebär att samma kontakt har angetts flera gånger i databasen: endast ett resultat kommer att tas med i beräkningen.

## Steg 3 - Sortera data {#step-3---sort-data}

The **[!UICONTROL Sorting]** I kan du sortera kolumninnehåll. Använd pilarna för att ändra kolumnordningen:

* The **[!UICONTROL Sorting]** I kan du sortera och ordna kolumninnehåll från A till Z eller i stigande ordning.
* The **[!UICONTROL Descending sort]** Ordnar innehållet från Z till A och i fallande ordning. Det här är användbart för att visa postförsäljning, till exempel: de högsta siffrorna visas högst upp i listan.

I det här exemplet sorteras data i stigande ordning baserat på mottagarens ålder.

![](assets/query_editor_nveau_57.png)

## Steg 4 - Filtrera data {#step-4---filter-data}

Med frågeredigeraren kan du filtrera data för att förfina sökningen.

Vilka filter som visas beror på vilken tabell frågan gäller.

![](assets/query_editor_nveau_09.png)

När du valt **[!UICONTROL Filtering conditions]** du kommer åt **[!UICONTROL Target elements]** -sektion: här kan du definiera hur data ska filtreras.

* Om du vill skapa ett nytt filter markerar du de fält, operatorer och värden som krävs för att skapa formeln som ska verifieras för att data ska kunna väljas. Det går att kombinera flera villkor (mer information finns i [Definiera filtervillkor](../../platform/using/defining-filter-conditions.md)).
* Om du vill använda tidigare sparade filter öppnar du listrutan genom att klicka på **[!UICONTROL Add]** knapp, klicka **[!UICONTROL Predefined filter]** och välj den du vill ha.

  ![](assets/query_editor_15.png)

* De filter som skapas i **[!UICONTROL Generic query editor]** är tillgängliga i andra frågeprogram och vice versa. Om du vill spara ett filter klickar du på **[!UICONTROL Save]** -ikon.

  >[!NOTE]
  >
  >Mer information om hur du skapar och använder filter finns i [Filtreringsalternativ](../../platform/using/filtering-options.md).

Om du vill återställa alla mottagare med engelskspråkighet, som visas i följande exempel, väljer du:&quot;mottagarspråk **lika med** EN&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>Du kommer åt ett alternativ direkt genom att skriva följande formel i **Värde** fält: **$(options:OPTION_NAME)**.

Klicka på **[!UICONTROL Preview]** om du vill visa resultatet av filtreringsvillkoret. I det här fallet visas alla mottagare på engelska med namn, förnamn och e-postadress.

![](assets/query_editor_nveau_98.png)

Användare som är bekanta med SQL-språket kan klicka **[!UICONTROL Generate SQL query]** för att visa frågan i SQL.

![](assets/query_editor_nveau_99.png)

## Steg 5 - Formatera data {#step-5---format-data}

När du har konfigurerat begränsningsfiltren får du tillgång till **[!UICONTROL Data formatting]** -fönstret. I det här fönstret kan du ordna om utdatakolumner, omforma data och ändra kolumnrubrikernas övre/nedre gemener. Du kan också använda en formel för slutresultatet med hjälp av ett beräkningsfält.

>[!NOTE]
>
>Mer information om olika typer av beräkningsfält finns i [Skapa beräknade fält](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Omarkerade kolumner visas inte i dataförhandsgranskningsfönstret.

![](assets/query_editor_nveau_10.png)

The **[!UICONTROL Transformation]** kan du ändra en kolumnetikett till versaler eller gemener. Markera kolumnen och klicka på **[!UICONTROL Transformation]** kolumn. Du kan välja:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Steg 6 - Förhandsgranska data {#step-6---preview-data}

The **[!UICONTROL Data preview]** -fönstret är det sista steget. Klicka **[!UICONTROL Start the preview of the data]** för att få fram resultatet av din fråga. Den är tillgänglig i kolumner eller i XML-format. Klicka på **[!UICONTROL Generated SQL queries]** för att visa frågan i SQL-format.

I det här exemplet sorteras data i stigande ordning baserat på mottagarens ålder.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Som standard visas endast de första 200 raderna i **[!UICONTROL Data preview]** -fönstret. Om du vill ändra det här anger du ett tal i dialogrutan **[!UICONTROL Lines to display]** och klicka **[!UICONTROL Start the preview of the data]**.
