---
product: campaign
title: Hantera och anpassa listor
description: Lär dig hur du bläddrar i och konfigurerar listor
feature: Audiences, Data Management
exl-id: 21656cc2-15a1-4156-8897-ea4fe3e9b97f
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 2%

---

# Hantera och anpassa listor{#manage-and-customize-lists}

![](../../assets/common.svg)

Du kan komma åt listor med poster i Campaign-databasen med Utforskaren. Du kan filtrera dessa listor, köra sökningar, lägga till information, filtrera och sortera data.

## Räkna poster {#counting-records}

Som standard läser Adobe Campaign in de första 200 posterna i en lista. Det innebär att visningen inte nödvändigtvis visar alla poster i tabellen som du visar. Du kan räkna antalet poster i listan och läsa in fler poster.

I den nedre högra delen av listskärmen visas en **[!UICONTROL counter]** visar hur många poster som har lästs in och det totala antalet poster i databasen (efter att eventuella filter har använts):

![](assets/s_ncs_user_nb_200_0.png)

Om en **?**&quot; visas i stället för siffran till höger. Klicka på räknaren för att starta beräkningen.

### Läs in fler poster {#loading-more-records}

Om du vill läsa in (och därför visa) ytterligare poster (200 rader som standard) klickar du på **[!UICONTROL Continue loading]**.

![](assets/s_ncs_user_load_list.png)

Om du vill läsa in alla poster högerklickar du på listan och väljer **[!UICONTROL Load all]**.

>[!CAUTION]
>
>Beroende på antalet poster kan tiden för inläsning av den fullständiga listan vara lång.

### Ändra standardantal poster {#change-default-number-of-records}

Om du vill ändra standardantalet inlästa poster klickar du på **[!UICONTROL Configure list]** längst ned till höger i listan.

![](assets/s_ncs_user_configure_list.png)

Klicka på **[!UICONTROL Advanced parameters]** (längst ned till vänster) och ändra antalet rader som ska hämtas.

![](assets/s_ncs_user_configurelist_advancedparam.png)

## Konfigurera listor {#configuring-lists}

### Lägg till kolumner {#add-columns}

Det finns två sätt att lägga till en kolumn i en lista.

Du kan snabbt lägga till en kolumn i en lista från detaljerna i en post. Så här gör du:

1. På en detaljskärm högerklickar du på det fält som du vill visa i en kolumn.
1. Välj **[!UICONTROL Add in the list]**.

   Kolumnen läggs till till höger om de befintliga kolumnerna.

![](assets/s_ncs_user_add_in_list.png)

Ett annat sätt att lägga till kolumner, till exempel om du vill visa data som inte visas på detaljskärmen, är att använda listkonfigurationsfönstret. Så här gör du:

1. Klicka **[!UICONTROL Configure list]** nedan och till höger om listan.

   ![](assets/s_ncs_user_configure_list.png)

1. Dubbelklicka på det fält som ska läggas till i listan i konfigurationsfönstret **[!UICONTROL Available fields]** för att lägga till den i **[!UICONTROL Output columns]**.

   ![](assets/s_ncs_user_configurelist.png)

   >[!NOTE]
   >
   >Som standard visas inte avancerade fält. Om du vill visa dem klickar du på **Visa avancerade fält** nedan och till höger om listan med tillgängliga fält.
   >
   >Etiketterna visas per tabell och sedan i alfabetisk ordning.
   >
   >Använd **Sök** om du vill göra en sökning i de tillgängliga fälten. Mer information finns i [det här avsnittet](#sorting-a-list).
   >
   >Fält identifieras av specifika ikoner: SQL-fält, länkade tabeller, beräknade fält osv. För varje markerat fält visas beskrivningen under listan med tillgängliga fält. [Läs mer](#configuring-lists).
   >
   >Du kan också sortera och filtrera data. Se [det här avsnittet](../../platform/using/filtering-options.md).

1. Upprepa för varje kolumn som ska visas.
1. Använd pilarna för att ändra **visningsordning**. Den högsta kolumnen finns till vänster i listan med poster.

   ![](assets/s_ncs_user_columns_order_down.png)

1. Om du vill kan du klicka **[!UICONTROL Distribution of values]** om du vill visa ompartitionen av värden för det valda fältet i den aktuella mappen.

   ![](assets/s_ncs_user_configurelist_values.png)

1. Klicka **[!UICONTROL OK]** för att bekräfta konfigurationen och visa resultatet.

### Skapa en ny kolumn {#create-a-new-column}

Du kan skapa nya kolumner för att visa ytterligare fält i listan. Så här gör du:

1. Klicka **[!UICONTROL Configure the list]** nedan och till höger om listan.
1. Klicka **[!UICONTROL Add]** om du vill visa ett nytt fält i listan.

### Ta bort en kolumn {#remove-a-column}

Du kan maskera en eller flera kolumner i en lista med poster med **[!UICONTROL Configure list]** som finns nedanför och till höger om listan.

![](assets/s_ncs_user_configure_list.png)

I listkonfigurationsfönstret väljer du den kolumn som ska maskeras på menyn **[!UICONTROL Output columns]** och klicka på knappen Ta bort.

![](assets/s_ncs_user_removecolumn_icon.png)

Upprepa för varje kolumn som ska maskeras. Klicka **[!UICONTROL OK]** för att bekräfta konfigurationen och visa resultatet.

### Justera kolumnbredd {#adjust-column-width}

När en lista är aktiv, d.v.s. minst en rad är markerad, kan du använda F9 för att justera bredden på kolumnerna så att alla kolumner kan visas på skärmen.

### Visa data i undermappar {#display-sub-folders-records}

Listor kan visa:

* Antingen posterna i den valda mappen,
* Eller posterna i den markerade mappen OCH dess undermappar.

Om du vill växla från ett visningsläge till ett annat klickar du på **[!UICONTROL Display sub-levels]** i verktygsfältet.

![](assets/s_ncs_user_display_children_icon.png)

## Spara en listkonfiguration {#saving-a-list-configuration}

Listkonfigurationerna definieras lokalt på arbetsstationsnivå. När den lokala cachen rensas inaktiveras lokala konfigurationer.

Som standard gäller de definierade visningsparametrarna för alla listor med motsvarande mapptyp. När du ändrar hur listan med mottagare visas från en mapp kommer den här konfigurationen att användas för alla övriga mottagarmappar.

Det går dock att spara mer än en konfiguration som ska användas på olika mappar av samma typ. Konfigurationen sparas med egenskaperna för den mapp som innehåller data och kan tillämpas igen.

För en leveransmapp är det till exempel möjligt att konfigurera följande visning:

![](assets/s_ncs_user_folder_save_config_1.png)

Följ stegen nedan för att spara listkonfigurationen så att den kan återanvändas:

1. Högerklicka på mappen som innehåller de data som visas.
1. Välj **[!UICONTROL Properties]**.
1. Klicka **[!UICONTROL Advanced settings]** och ange sedan ett namn i **[!UICONTROL Configuration]** fält.

   ![](assets/s_ncs_user_folder_save_config_2.png)

1. Klicka **[!UICONTROL OK]** och sedan klicka **[!UICONTROL Save]**.

Du kan sedan använda den här konfigurationen på en annan **Leverans** mapp:

![](assets/s_ncs_user_folder_save_config_3.png)

Klicka **[!UICONTROL Save]** i fönstret för mappegenskaper. Listvisningen har ändrats så att den matchar den angivna konfigurationen:

![](assets/s_ncs_user_folder_save_config_5.png)

## Exportera en lista {#exporting-a-list}

Om du vill exportera data från en lista måste du använda en exportguide. Du kommer åt den genom att markera elementen som ska exporteras i listan, högerklicka och välja **[!UICONTROL Export...]**.

Användningen av import- och exportfunktionerna förklaras i [Allmän import och export](../../platform/using/about-generic-imports-exports.md).

>[!CAUTION]
>
>Element från en lista får inte exporteras med funktionen Kopiera/Klistra in.

## Sortera en lista {#sorting-a-list}

Listor kan innehålla en stor mängd data. Du kan sortera dessa data eller använda enkla eller avancerade filter. Med sortering kan du visa data i stigande eller fallande ordning. Med filter kan du definiera och kombinera villkor så att endast markerade data visas.

Klicka på kolumnrubriken om du vill använda en stigande eller fallande sortering eller om du vill avbryta sorteringen. Aktiv sorteringsstatus och sorteringsordning anges med en blå pil före kolumnetiketten. Ett rött streck före kolumnetiketten betyder att sorteringen tillämpas på data som indexeras från databasen. Den här sorteringsmetoden används för att optimera sorteringsjobb.

Du kan också konfigurera sortering eller kombinera sorteringsvillkor. Följ stegen nedan för att göra detta:

1. **[!UICONTROL Configure list]** nedan och till höger om listan.

   ![](assets/s_ncs_user_configure_list.png)

1. Klicka på knappen **[!UICONTROL Sorting]** -fliken.
1. Markera de fält som ska sorteras och sorteringsriktningen (stigande eller fallande).

   ![](assets/s_ncs_user_configurelist_sort.png)

1. Sorteringsprioriteten definieras av sorteringskolumnernas ordning. Om du vill ändra prioriteten använder du lämpliga ikoner för att ändra ordningen på kolumnerna.

   ![](assets/s_ncs_user_configurelist_move.png)

   Sorteringsprioriteten påverkar inte visningen av kolumnerna i listan.

1. Klicka **[!UICONTROL Ok]** för att bekräfta konfigurationen och visa resultatet i listan.

### Söka efter element {#running-a-search}

Du kan göra en sökning i de tillgängliga fälten i en redigerare med hjälp av **[!UICONTROL Search]** fält ovanför fältlistan. Tryck **Retur** på tangentbordet eller bläddra i listan. Fälten som matchar sökningen får feta etiketter.

>[!NOTE]
>
>Du kan skapa filter för att endast visa en del av data i en lista. [Läs mer](../../platform/using/creating-filters.md).
