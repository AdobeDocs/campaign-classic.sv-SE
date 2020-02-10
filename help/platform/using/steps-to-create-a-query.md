---
title: Steg för att skapa en fråga
seo-title: Steg för att skapa en fråga
description: Steg för att skapa en fråga
seo-description: null
page-status-flag: never-activated
uuid: 9668f49c-2da7-42c8-8728-8d644c787935
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: d538f489-f1ae-4682-9c21-d0300bd42b26
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Steg för att skapa en fråga{#steps-to-create-a-query}

Så här skapar du en fråga i Adobe Campaign:

1. Markera arbetsregistret. Gå till [steg 1 - Välj en tabell](#step-1---choose-a-table).
1. Markera de data som ska extraheras. Se [steg 2 - Välj data att extrahera](#step-2---choose-data-to-extract).
1. Definiera datasorteringssekvensen. Se [steg 3 - Sortera data](#step-3---sort-data).
1. Filtrera data. Se [steg 4 - Filtrera data](#step-4---filter-data).
1. Formatera data. Se [steg 5 - Formatera data](#step-5---format-data).
1. Visa resultatet. Se [steg 6 - Förhandsgranska data](#step-6---preview-data).

>[!NOTE]
>
>Alla dessa steg är tillgängliga i den generiska frågeredigeraren. När en fråga skapas i en annan kontext kan vissa steg utelämnas.\
>Frågeaktiviteten visas i [det här avsnittet](../../workflow/using/query.md).

## Steg 1 - Välj en tabell {#step-1---choose-a-table}

Markera tabellen som innehåller de data som du vill fråga i **[!UICONTROL Document type]** fönstret. Om det behövs kan du filtrera data med filterfältet eller **[!UICONTROL Filters]** knappen.

![](assets/query_editor_nveau_21.png)

## Steg 2 - Välj data att extrahera {#step-2---choose-data-to-extract}

Markera de data som ska visas i **[!UICONTROL Data to extract]** fönstret: Dessa fält utgör utdatakolumnerna.

Välj till exempel **[!UICONTROL Age]**, **[!UICONTROL Primary key]**, **[!UICONTROL Email domain]** och **[!UICONTROL City]**. Resultatet ordnas utifrån det här valet. Använd de blå pilarna till höger om fönstret för att ändra kolumnordningen.

![](assets/query_editor_nveau_01.png)

Du kan redigera ett uttryck genom att infoga en formel i det eller köra en process på en sammanställningsfunktion. Det gör du genom att klicka på **[!UICONTROL Expression]** kolumnfältet och sedan välja **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

Det går att gruppera utdatakolumndata: Om du vill göra det kontrollerar du **[!UICONTROL Yes]** i **[!UICONTROL Group]** kolumnen i **[!UICONTROL Data to extract]** fönstret. Den här funktionen genererar ett resultat runt den markerade grupperingsaxeln. Ett exempel på en fråga med gruppering finns i [det här avsnittet](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* Med funktionen kan du&quot;gruppera efter&quot; och välja vad som har grupperats (&quot;att&quot;). **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** Den här funktionen gäller för alla fält i utdatakolumnen. Med det här alternativet kan du till exempel gruppera alla val för en utdatakolumn och återställa en viss typ av information, till exempel mottagare mellan 35 och 50.

   Mer information finns i [det här avsnittet](../../workflow/using/querying-using-grouping-management.md).

* Med **[!UICONTROL Remove duplicate rows (DISTINCT)]** funktionen kan du duplicera identiska resultat som du får i utdatakolumnen. Om du till exempel gör en inventering genom att markera fälten Efternamn, Förnamn och E-post i utdatakolumnen, kommer de som har identiska data att tas bort eftersom det innebär att samma kontakt har angetts flera gånger i databasen: endast ett resultat kommer att beaktas.

## Steg 3 - Sortera data {#step-3---sort-data}

I **[!UICONTROL Sorting]** fönstret kan du sortera kolumninnehåll. Använd pilarna för att ändra kolumnordningen:

* I kolumnen kan du enkelt sortera och ordna kolumninnehåll från A till Ö eller i stigande ordning. **[!UICONTROL Sorting]**
* Innehållet **[!UICONTROL Descending sort]** ordnas från Ö till A och i fallande ordning. Detta är användbart för att visa postförsäljning, till exempel: de högsta siffrorna visas högst upp i listan.

I det här exemplet sorteras data i stigande ordning baserat på mottagarens ålder.

![](assets/query_editor_nveau_57.png)

## Steg 4 - Filtrera data {#step-4---filter-data}

Med frågeredigeraren kan du filtrera data för att förfina sökningen.

Vilka filter som visas beror på vilken tabell frågan gäller.

![](assets/query_editor_nveau_09.png)

När du har valt **[!UICONTROL Filtering conditions]** det här avsnittet kommer du åt **[!UICONTROL Target elements]** : på så sätt kan du definiera hur data ska filtreras för att samlas in.

* Om du vill skapa ett nytt filter markerar du de fält, operatorer och värden som krävs för att skapa formeln som ska verifieras för att data ska kunna väljas. Det går att kombinera flera villkor (mer information finns i [Definiera filtervillkor](../../platform/using/defining-filter-conditions.md)).
* Om du vill använda tidigare sparade filter öppnar du listrutan genom att klicka på **[!UICONTROL Add]** knappen, klickar **[!UICONTROL Predefined filter]** och väljer den du vill använda.

   ![](assets/query_editor_15.png)

* De filter som skapas i **[!UICONTROL Generic query editor]** är tillgängliga i andra frågeprogram och vice versa. Klicka på **[!UICONTROL Save]** ikonen om du vill spara ett filter.

   >[!NOTE]
   >
   >Mer information om hur du skapar och använder filter finns i [Filtreringsalternativ](../../platform/using/filtering-options.md).

Om du vill återställa alla mottagare med engelskspråkighet, som visas i följande exempel, väljer du: &quot;mottagarspråk **lika med** EN&quot;.

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>Du kan komma åt ett alternativ genom att skriva följande formel i fältet **Värde** : **$(options:OPTION_NAME)**.

Klicka på **[!UICONTROL Preview]** fliken för att visa resultatet av filtreringsvillkoret. I det här fallet visas alla mottagare på engelska med namn, förnamn och e-postadress.

![](assets/query_editor_nveau_98.png)

Användare som är bekanta med SQL-språk kan klicka **[!UICONTROL Generate SQL query]** för att visa frågan i SQL.

![](assets/query_editor_nveau_99.png)

## Steg 5 - Formatera data {#step-5---format-data}

När du har konfigurerat begränsningsfiltren kommer du åt **[!UICONTROL Data formatting]** fönstret. I det här fönstret kan du ordna om utdatakolumner, omforma data och ändra kolumnrubrikernas övre/nedre gemener. Du kan också använda en formel för slutresultatet med hjälp av ett beräkningsfält.

>[!NOTE]
>
>Mer information om typerna av beräkningsfält finns i [Skapa beräkningsfält](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

Omarkerade kolumner visas inte i dataförhandsgranskningsfönstret.

![](assets/query_editor_nveau_10.png)

I kolumnen kan du ändra en kolumnetikett till versaler eller gemener. **[!UICONTROL Transformation]** Markera kolumnen och klicka i **[!UICONTROL Transformation]** kolumnen. Du kan välja:

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## Steg 6 - Förhandsgranska data {#step-6---preview-data}

Fönstret **[!UICONTROL Data preview]** är sista steget. Klicka **[!UICONTROL Start the preview of the data]** för att hämta frågeresultatet. Den är tillgänglig i kolumner eller i XML-format. Klicka på **[!UICONTROL Generated SQL queries]** fliken för att visa frågan i SQL-format.

I det här exemplet sorteras data i stigande ordning baserat på mottagarens ålder.

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>Som standard visas bara de första 200 raderna i **[!UICONTROL Data preview]** fönstret. Om du vill ändra detta anger du ett nummer i **[!UICONTROL Lines to display]** rutan och klickar på **[!UICONTROL Start the preview of the data]**.

