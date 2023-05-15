---
product: campaign
title: Målinrikta data
description: Läs mer om måldata i ett arbetsflöde
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Query Editor, Data Management
exl-id: 74b82019-bdab-4442-84cf-5ad18d0db788
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1924'
ht-degree: 4%

---

# Måldata{#targeting-data}



## Skapa frågor {#creating-queries}

### Markera data {#selecting-data}

A **[!UICONTROL Query]** Med -aktivitet kan du välja grundläggande data för att skapa målpopulationen. Mer information finns i [Skapa en fråga](query.md#creating-a-query).

Du kan även använda följande aktiviteter för att fråga efter och finjustera data från databasen: [Inkrementell fråga](incremental-query.md), [Läslista](read-list.md).

Det är möjligt att samla in ytterligare data som ska vidarebefordras och behandlas under arbetsflödets hela livscykel. Mer information finns i [Lägga till data](query.md#adding-data) och [Redigera ytterligare data](#editing-additional-data).

### Redigera ytterligare data {#editing-additional-data}

När ytterligare data har lagts till kan du redigera dem eller använda dem för att förfina det mål som definierats i frågeaktiviteten.

The **[!UICONTROL Edit additional data...]** kan du visa tillagda data och ändra dem eller lägga till i dem.

![](assets/wf_add_data_edit_link.png)

Om du vill lägga till data i de tidigare definierade utdatakolumnerna markerar du dem i listan med tillgängliga fält. Om du vill skapa en ny utdatakolumn klickar du på **[!UICONTROL Add]** ikonen, markera fältet och klicka på **[!UICONTROL Edit expression]**.

![](assets/query_add_an_output_column.png)

Definiera ett beräkningssätt för det fält som ska läggas till, t.ex. en mängd.

![](assets/query_add_an_output_column_formula.png)

The **[!UICONTROL Add a sub-item]** kan du bifoga beräknade data till samlingen. På så sätt kan du välja ytterligare data från samlingen eller definiera aggregeringsberäkningar för samlingselement.

![](assets/query_add_columns_subscription_sub-element.png)

Underelementen representeras i underträdet till den samling som de mappas till.

Samlingar visas i **[!UICONTROL Collections]** underflik. Du kan filtrera de insamlade elementen genom att klicka på **[!UICONTROL Detail]** ikonen för den valda samlingen. Med filterguiden kan du välja insamlade data och ange de filtreringsvillkor som ska tillämpas på data i samlingen.

![](assets/query_add_columns_collection.png)

### Förfina målet med ytterligare data {#refining-the-target-using-additional-data}

Med de ytterligare data som samlas in kan du förfina datafiltreringen i databasen. Om du vill göra det klickar du på **[!UICONTROL Refine the target using additional data...]** länk: på så sätt kan du överfiltrera på tillagda data.

![](assets/wf_add_data_use_additional_data.png)

### Homogenisera data {#homogenizing-data}

I **[!UICONTROL Union]** eller **[!UICONTROL Intersection]** typaktiviteter kan du välja att bara behålla delade ytterligare data för att hålla data konsekventa. I det här fallet kommer den temporära utdatatabellen för den här aktiviteten endast att innehålla de ytterligare data som finns i alla inkommande uppsättningar.

![](assets/option-common_additionnal_col_only.png)

### Avstämning med ytterligare data {#reconciliation-with-additional-data}

Under datavstämningsfaserna (**[!UICONTROL Union]**, **[!UICONTROL Intersection]**, osv. aktiviteter) kan du välja vilka kolumner som ska användas för datavstämning från de andra kolumnerna. Det gör du genom att konfigurera en avstämning för ett urval kolumner och ange huvuduppsättningen. Markera sedan kolumnerna i fönstrets nedre kolumn, så som visas i följande exempel:

![](assets/select-column-and-join.png)

### Skapa delmängder {#creating-subsets}

The **[!UICONTROL Split]** Med -aktivitet kan du skapa delmängder på villkor som definieras via extraheringsfrågor. När du redigerar ett filtervillkor för populationen för varje delmängd får du sedan tillgång till standardfrågeaktiviteten som gör att du kan definiera målsegmenteringsvillkoren.

Du kan dela upp ett mål i flera delmängder genom att endast använda ytterligare data som filtreringsvillkor, eller utöver måldata. Du kan också använda externa data om du har köpt **Åtkomst till federerade data** alternativ.

Mer information finns i [Skapa delmängder med aktiviteten Dela](#creating-subsets-using-the-split-activity).

## Segmentdata {#segmenting-data}

### Kombinera flera mål (unionen) {#combining-several-targets--union-}

Med unionsaktiviteten kan du kombinera resultatet av flera aktiviteter i en övergång. Satser behöver inte nödvändigtvis vara homogena.

![](assets/join_reconciliation_options.png)

Följande datavstämningsalternativ är tillgängliga:

* **[!UICONTROL Keys only]**

   Detta alternativ kan användas om indatapulserna är homogena.

* **[!UICONTROL All columns in common]**

   Med det här alternativet kan du stämma av data baserat på alla kolumner som är gemensamma för målets olika populationer.

   Adobe Campaign identifierar kolumner utifrån deras namn. Tröskelvärdet accepteras: En &quot;E-post&quot;-kolumn kan till exempel tolkas som identisk med en &#39;@email&#39;-kolumn.

* **[!UICONTROL A selection of columns]**

   Välj det här alternativet om du vill definiera en lista över kolumner som datavstämning ska tillämpas på.

   Börja med att markera huvuduppsättningen (den som innehåller källdata) och sedan de kolumner som ska användas för kopplingen.

   ![](assets/join_reconciliation_options_01.png)

   >[!CAUTION]
   >
   >Under datavstämning dedupliceras inte populationer.

   Du kan begränsa populationsstorleken till ett visst antal poster. Om du vill göra det klickar du på lämpligt alternativ och anger antalet poster som ska sparas.

   Ange även prioriteten för inkommande populationer: I fönstrets nedre del visas de inkommande övergångarna för unionsaktiviteten och du kan sortera dem med de blå pilarna till höger om fönstret.

   Posterna hämtas först från populationen i den första ingående övergången i listan och sedan, om det maximala antalet inte har uppnåtts, tas de från populationen i den andra ingående övergången osv.

   ![](assets/join_limit_nb_priority.png)

### Extrahera leddata (skärning) {#extracting-joint-data--intersection-}

![](assets/traitements.png)

Med skärningspunkten kan du bara återställa de linjer som delas av populationerna av inkommande övergångar. Denna aktivitet ska konfigureras som unionsaktiviteten.

Dessutom är det bara möjligt att behålla ett urval av kolumner, eller bara de kolumner som delas av den inkommande populationen.

Skärningsaktiviteten beskrivs i [Skärningspunkt](intersection.md) -avsnitt.

### Uteslut en population (Uteslutning) {#excluding-a-population--exclusion-}

Med exkluderingsaktiviteten kan du utesluta element i ett mål från en annan målpopulation. Den här aktivitetens målgruppsdimension kommer att vara huvuduppsättningens.

Om det behövs kan du ändra inkommande tabeller. För att utesluta ett mål från en annan dimension måste detta mål återställas till samma måldimension som huvudmålet. Klicka på **[!UICONTROL Add]** och ange villkoren för dimensionsändring.

Datavstämning utförs antingen via en identifierare, en axel som ändras eller en koppling. Ett exempel finns i [Använda data från en lista: Läslista](../../platform/using/import-export-workflows.md#using-data-from-a-list--read-list).

![](assets/exclusion_edit_add_rule_01.png)

### Skapa delmängder med aktiviteten Dela {#creating-subsets-using-the-split-activity}

The **[!UICONTROL Split]** är en standardaktivitet som gör att du kan skapa så många uppsättningar som behövs via en eller flera filterdimensioner, samt generera antingen en utdataövergång per delmängd eller en unik övergång.

Ytterligare data som förmedlas av den inkommande övergången kan användas i filtreringsvillkoren.

För att konfigurera det måste du först välja villkor:

1. Dra och släpp en **[!UICONTROL Split]** aktivitet.
1. I **[!UICONTROL General]** väljer du ett alternativ: **[!UICONTROL Use data from the target and additional data]**, **[!UICONTROL Use the additional data only]** eller **[!UICONTROL Use external data]**.
1. Om **[!UICONTROL Use data from the target and additional data]** Om du väljer det här alternativet kan du använda alla data som överförs av den inkommande övergången med målinriktningsdimensionen.

   ![](assets/split-general-tab-options.png)

   När delmängder skapas används de ovannämnda filterparametrarna.

   Om du vill definiera filtreringsvillkor väljer du **[!UICONTROL Add a filtering condition on the inbound population]** och klicka på **[!UICONTROL Edit...]** länk. Ange sedan filtervillkoren för att skapa den här delmängden.

   ![](assets/split-subset-config-all-data.png)

   Ett exempel som visar hur du använder filtervillkor i **[!UICONTROL Split]** aktiviteten att dela in målet i olika populationer beskrivs i [det här avsnittet](cross-channel-delivery-workflow.md).

   The **[!UICONTROL Label]** I kan du ge den nyskapade delmängden ett namn som matchar den utgående övergången.

   Du kan också tilldela en segmentkod till delmängden för att identifiera den och använda den för att ange målpopulationen.

   Om det behövs kan du ändra målinriktnings- och filtreringsdimensionerna individuellt för varje delmängd som du vill skapa. Det gör du genom att redigera delmängdens filtreringsvillkor och kontrollera **[!UICONTROL Use a specific filtering dimension]** alternativ.

   ![](assets/split-subset-config-specific-filtering.png)

1. Om **[!UICONTROL Use the additional data only]** Om du väljer det här alternativet erbjuds endast ytterligare data för delmängdsfiltrering.

   ![](assets/split-subset-config-additional-data-only.png)

1. Om **Åtkomst till federerade data** är aktiverat, **[!UICONTROL Use external data]** I kan du bearbeta data i en extern databas som redan är konfigurerad, eller skapa en ny anslutning till en databas.

   ![](assets/split-subset-config-add_external_data.png)

   Beroende på vilken Campaign-version du har finns mer information i följande avsnitt:

   ![](assets/do-not-localize/v7.jpeg)[  Dokumentation om Campaign v7](../../installation/using/about-fda.md)

   ![](assets/do-not-localize/v8.png)[  Dokumentation om Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/fda.html?lang=en)

Sedan måste vi lägga till nya delmängder:

1. Klicka på **[!UICONTROL Add]** och ange filtervillkoren.

   ![](assets/wf_split_add_a_tab.png)

1. Definiera filterdimensionen i **[!UICONTROL General]** aktivitetens flik (se ovan). Den gäller som standard för alla delmängder.

   ![](assets/wf_split_edit_filtering.png)

1. Om det behövs kan du ändra filtreringsdimensionen för varje delmängd individuellt. Detta gör att du kan skapa en uppsättning för alla Gold-kortinnehavare, en för alla mottagare som klickade i det senaste nyhetsbrevet och en tredjedel för personer mellan 18 och 25 år som gjorde ett köp i butiken de senaste 30 dagarna, alla med samma delade aktivitet. Om du vill göra det väljer du **[!UICONTROL Use a specific filtering dimension]** och välj datafiltreringssammanhang.

   ![](assets/wf_split_change_dimension.png)

   >[!NOTE]
   >
   >Om du har skaffat **Åtkomst till federerade data** kan du skapa delmängder baserat på informationen i en extern bas. Det gör du genom att välja schemat för den externa tabellen i **[!UICONTROL Targeting dimension]** fält. Mer information finns i [Åtkomst till en extern databas (FDA)](accessing-an-external-database--fda-.md).

När deluppsättningar har skapats visar den delade aktiviteten som standard så många utdataövergångar som det finns deluppsättningar:

![](assets/wf_split_multi_outputs.png)

Du kan gruppera alla dessa delmängder i en enda utdataövergång. I det här fallet visas länken till respektive delmängd i segmentkoden. Om du vill göra det väljer du **[!UICONTROL Generate all subsets in the same table]** alternativ.

![](assets/wf_split_select_option_single_output.png)

Du kan till exempel placera en enda leveransaktivitet och anpassa leveransinnehållet baserat på segmentkoden för varje mottagaruppsättning:

![](assets/wf_split_single_output.png)

Du kan också skapa delmängder med **[!UICONTROL Cells]** aktivitet. Mer information finns i [Celler](cells.md) -avsnitt.

### Använd måldata {#using-targeted-data}

När data har identifierats och beretts kan de användas i följande sammanhang:

* Du kan uppdatera data i databasen efter dataändringar i de olika arbetsflödesstegen.

   Mer information finns här: [Uppdatera data](update-data.md).

* Du kan även uppdatera innehållet i befintliga listor.

   Mer information finns i [Listuppdatering](list-update.md).

* Du kan förbereda eller starta leveranser direkt i arbetsflödet.

   Mer information finns i [Leverans](delivery.md), [Leveranskontroll](delivery-control.md) och [Kontinuerlig leverans](continuous-delivery.md).

## Datahantering {#data-management}

I Adobe Campaign kombinerar datahanteringen en uppsättning aktiviteter för att lösa komplexa målgruppsproblem genom att erbjuda mer effektiva och flexibla verktyg. På så sätt kan ni implementera en konsekvent hantering av all kommunikation med en kontakt genom att använda information som hör till deras kontrakt, prenumerationer, reaktivitet av leveranser osv. Datahantering låter dig följa datas livscykeln under segmenteringsåtgärder och då särskilt:

* Förenkla och optimera målinriktningsprocesser genom att inkludera data som inte är modellerad i datakartläggningen (skapa nya tabeller: lokalt tillägg till varje arbetsflöde per målgrupp beroende på konfiguration).
* Behålla och överföra buffertberäkningar. Särskilt under faserna då målgrupper konstrueras eller för databasadministration.
* Åtkomst till externa baser (tillval): heterogena databaser som beaktas under målinriktningsprocessen.

För att genomföra dessa åtgärder erbjuder Adobe Campaign

* Datainsamling: [Filöverföring](file-transfer.md), [Inläsning av data (fil)](data-loading--file-.md), [Datainläsning (RDBMS)](data-loading--rdbms-.md), [Uppdatera data](update-data.md). Detta första steg i datainsamlingen förbereder data så att de kan behandlas i andra aktiviteter. Flera parametrar måste övervakas för att arbetsflödet ska fungera korrekt och ge de förväntade resultaten. När du till exempel importerar data måste primärnyckeln (Pkey) för dessa data vara unik för varje post.
* Målinriktade aktiviteter har förbättrats med datahanteringsalternativ: [Fråga](query.md), [Union](union.md), [Skärningspunkt](intersection.md), [Dela](split.md). På så sätt kan du konfigurera en union eller en skärning mellan data från flera olika måldimensioner, så länge datavstämning är möjligt.
* Dataomvandlingsaktiviteter: [Berikning](enrichment.md), [Ändra dimension](change-dimension.md).

>[!CAUTION]
>
>När två arbetsflöden är länkade innebär det inte att alla data som är länkade till dem tas bort om du tar bort ett källtabellselement.
>  
>Om du t.ex. tar bort en mottagare via ett arbetsflöde tas inte hela mottagarens leveranshistorik bort. Om du tar bort en mottagare direkt i mappen Mottagare tas alla data som är länkade till den här mottagaren bort.

### Förbättra och ändra data {#enriching-and-modifying-data}

Förutom måldimensionen kan du med filtreringsdimensionen ange vilken typ av insamlade data som ska användas. Se [Målinriktning och filtrering](building-a-workflow.md#targeting-and-filtering-dimensions).

Identifierade och insamlade data kan berikas, aggregeras och ändras för att optimera målkonstruktionen. För att göra detta, utöver de databehandlingsaktiviteter som beskrivs i [Segmentera data](#segmenting-data) använder du följande:

* The **[!UICONTROL Enrichment]** kan du snabbt lägga till kolumner i ett schema samt lägga till information i vissa element. Den beskrivs i [Berikning](enrichment.md) i databasen med aktiviteter.
* The **[!UICONTROL Edit schema]** kan du ändra strukturen för ett schema. Den beskrivs i [Redigera schema](edit-schema.md) i databasen med aktiviteter.
* The **[!UICONTROL Change dimension]** kan du ändra målinriktningsdimensionen under målkonstruktionscykeln. Den beskrivs i [Ändra dimension](change-dimension.md) -avsnitt.
