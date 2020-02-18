---
title: Fråga
seo-title: Fråga
description: Fråga
seo-description: null
page-status-flag: never-activated
uuid: 32f4f467-5083-414f-8616-1aa4bf2b5867
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: b53d9810-f61f-4257-b410-e4d30f78429d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f8cf2f72dcf2ab48a42faf7931ca831b6431548d

---


# Fråga{#query}

## Skapa en fråga {#creating-a-query}

Med en fråga kan du välja ett mål enligt villkor. Du kan koppla en segmentkod till frågeresultatet och infoga ytterligare data i den.
Mer information om frågeexempel finns i det här [avsnittet](../../workflow/using/querying-recipient-table.md).

>[!NOTE]
>
>Frågeaktiviteter är inte kompatibla med CLOB-fält när Oracle används.

![](assets/s_user_segmentation_wizard_9.png)

Mer information om hur du använder och hanterar ytterligare data finns i [Lägga till data](#adding-data).

Med **[!UICONTROL Edit query...]** länken kan du definiera måltyp, begränsningar och urvalskriterier för populationen på följande sätt:

1. Välj målinriktning och filtreringsdimension. Som standard är målet markerat bland mottagarna. Listan med begränsningsfilter är densamma som de som används för leveransmål.

   Målgruppsdimensionen sammanfaller med den typ av element som vi kommer att arbeta med, t.ex. målgruppen för insatsen.

   Filtreringsdimensionen gör det möjligt att samla in dessa element, t.ex. information om målpersonen (kontrakt, fullständiga och slutliga kvittningar osv.).

   Mer information finns i [Målinriktning och filtrering](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   En fråga kan baseras på data från den inkommande övergången, om det behövs, genom att välja **[!UICONTROL Temporary schema]** när du väljer mål- och filtreringsdimensioner.

   ![](assets/query_temporary_table.png)

1. Definiera populationerna med guiden. Fälten som ska anges kan variera beroende på måltyp. Du kan förhandsgranska målpopulationen med de aktuella villkoren på **[!UICONTROL Preview]** fliken.

   Mer information om hur du skapar och använder filter och frågor finns i det här [avsnittet](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. Om du har valt **[!UICONTROL Filtering conditions]** i steg 1 eller med alternativet **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** måste du lägga till filtervillkor manuellt senare.

   Du kan också lägga till villkor för datagruppering genom att markera motsvarande ruta. För att göra detta måste filtreringsdimensionen skilja sig från frågemålets dimension. Mer information om gruppering finns i det här [avsnittet](../../workflow/using/querying-using-grouping-management.md).

   Du kan också lägga till fler villkor genom att använda uttrycksverktyget och kombinera det med de logiska alternativen AND, OR och EXCEPT. Du kan sedan förhandsvisa kombinationen **[!UICONTROL Corresponding SQL query...]** för dina villkor. Mer information finns i det här [avsnittet](../../platform/using/defining-filter-conditions.md#building-expressions).

   Spara filtret om du vill återanvända det senare.

   ![](assets/s_user_segmentation_query_advanced.png)

## Lägga till data {#adding-data}

Med de extra kolumnerna kan du samla in ytterligare information om målpopulationen, t.ex. avtalsnummer, prenumerationer på nyhetsbrev eller ursprung. Dessa data kan lagras i Adobe Campaign-databasen eller i en extern databas.

Med hjälp av **[!UICONTROL Add data...]** länken kan du välja vilka ytterligare data som ska samlas in.

![](assets/wf_add_data_link.png)

Börja med att välja vilken typ av data som ska läggas till:

![](assets/wf_add_data_1st_option.png)

* Välj **[!UICONTROL Data linked to the filtering dimension]** om du vill välja data i Adobe Campaign-databasen.
* Välj **[!UICONTROL External data]** att lägga till data från en extern databas. Det här alternativet är bara tillgängligt om du har köpt alternativet **Federated Data Access** . Mer information finns i [Åtkomst till en extern databas (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).
* Välj alternativet **[!UICONTROL An offer proposition]** om du vill lägga till en uppsättning kolumner där du kan lagra det bästa erbjudande som genereras av erbjudandemotorn. Det här alternativet är bara tillgängligt om du har köpt **interaktionsmodulen** .

Om ingen valfri modul är installerad på plattformen visas inte det här steget. Du kommer att gå direkt till nästa steg.

Så här lägger du till data från Adobe Campaign-databasen:

1. Välj den typ av data som du vill lägga till. Detta kan vara data som tillhör filterdimensionen eller data som lagras i länkade tabeller.

   ![](assets/query_add_columns.png)

1. Om data tillhör frågefiltret markerar du dem i listan med tillgängliga fält så att de visas i utdatakolumnerna.

   ![](assets/wf_add_data_field_selection.png)

   Du kan lägga till:

   * Ett fält som beräknas baserat på data från målpopulationen eller ett aggregat (antal väntande inköp under den senaste månaden, genomsnittligt belopp för ett kvitto osv.). Du kan till exempel gå till [Markera data](../../workflow/using/targeting-data.md#selecting-data).
   * Ett nytt fält som skapats med **[!UICONTROL Add]** knappen till höger om listan med utdatakolumner.

      Du kan också lägga till en samling information, till exempel en lista över kontrakt, de fem senaste leveranserna osv. Samlingar sammanfaller med fält som kan ha flera värden för samma profil (1-N-relation). Mer information finns i [Redigera ytterligare data](../../workflow/using/targeting-data.md#editing-additional-data).

Så här lägger du till en samling information som är länkad till en målpopulation:

1. I det första steget i guiden väljer du **[!UICONTROL Data linked to the filtering dimension]** :
1. Markera tabellen som innehåller den information som du vill samla in och klicka på **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. Ange vid behov antalet element i samlingen som du vill behålla genom att välja ett av värdena i **[!UICONTROL Data collected]** fältet. Som standard återskapas alla rader i samlingen och filtreras sedan enligt villkoren som anges i följande steg.

   * Om ett enskilt element i samlingen sammanfaller med filtervillkoren för den här samlingen väljer du **[!UICONTROL Single row]** i **[!UICONTROL Data collected]** fältet.

      >[!IMPORTANT]
      >
      >I det här läget optimeras den SQL-fråga som genereras tack vare en direkt överlappning av samlingselementen.
      >
      >Om det inledande villkoret inte uppfylls kan resultatet bli bristfälligt (saknade eller överlappande linjer).

   * Om du återställer flera rader (**[!UICONTROL Limit the line count]**) kan du ange hur många rader som ska samlas in.
   * Om de insamlade kolumnerna innehåller aggregat, t.ex. antalet fel som deklarerats, genomsnittliga utgifter på en webbplats, osv. du kan använda **[!UICONTROL Aggregates]** värdet.
   ![](assets/query_add_collection_param.png)

1. Ange delmarkeringen för samlingen. Till exempel: endast de senaste 15 dagarna.

   ![](assets/query_add_columns_collection_filter.png)

1. Om du har valt **[!UICONTROL Limit the line count]** alternativet anger du i vilken ordning de insamlade data ska filtreras. När antalet rader som samlas in är fler än antalet rader som du har angett att de ska behållas kan du ange vilka rader som ska behållas i filtreringsordningen.

## Exempel: Riktning på enkla mottagarattribut {#example--targeting-on-simple-recipient-attributes}

I följande exempel syftar frågan till att identifiera män mellan 18 och 30 år och som bor i Frankrike. Den här frågan kommer att användas i ett arbetsflöde som t.ex. syftar till att göra dem till ett exklusivt erbjudande.

>[!NOTE]
>
>Ytterligare frågeexempel visas i [det här avsnittet](../../workflow/using/querying-recipient-table.md).

1. Ge frågan ett namn och välj sedan **[!UICONTROL Edit query...]** länken.
1. Välj **[!UICONTROL Filtering conditions]** i listan över tillgängliga filtertyper.
1. Ange olika villkor för det föreslagna målet. Här kombineras villkor med alternativet AND. För att kunna inkluderas i urvalet måste mottagarna uppfylla följande fyra villkor:

   * Mottagare vars titel är&quot;Mr.&quot; (kan också hittas med fältet **Genus** och välja **Male** som värde).
   * Mottagare under 30 år.
   * Mottagare över 18 år.
   * Mottagare som bor i Frankrike.
   ![](assets/query_example.png)

   Du kan visa SQL som matchar din villkorskombination:

   ![](assets/query_example_sql.png)

1. Du kan kontrollera att villkoren är korrekta genom att förhandsgranska de mottagare som matchar frågan på fliken:

   ![](assets/query_example_preview.png)

1. Spara filtren så att du kan använda dem igen vid ett senare tillfälle genom att klicka på **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. Fortsätt redigera arbetsflödet genom att lägga till andra aktiviteter i det. När det har startats och föregående frågesteg är klart visas antalet mottagare. Du kan visa mer information med hjälp av snabbmenyn (högerklicka på övergången > **[!UICONTROL Display the target...]**).

   ![](assets/query_example_result.png)

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar den population som frågan riktar sig till. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Det här värdet är arbetstabellens schema. Den här parametern är giltig för alla övergångar med **[!UICONTROL tableName]** och **[!UICONTROL schema]**.

## Optimera frågor {#optimizing-queries}

I avsnittet nedan beskrivs de effektivaste strategierna för att optimera frågor som körs i Adobe Campaign för att begränsa arbetsbördan för databasen och förbättra användarupplevelsen.

### Kopplingar och index {#joins-and-indexes}

* Effektiva frågor bygger på index.
* Använd ett index för alla kopplingar.
* När du definierar länkar i schemat bestäms kopplingsvillkoren. Den länkade tabellen ska ha ett unikt index för primärnyckeln och kopplingen ska vara i det här fältet.
* Utför kopplingar genom att definiera nycklar i numeriska fält i stället för strängfält.
* Undvik yttre kopplingar. Använd posten med noll-ID när det är möjligt för att få en yttre kopplingsfunktion.
* Använd rätt datatyp för kopplingar.

   Se till att `where` satsen är av samma typ som fältet.

   Ett vanligt misstag är: `iBlacklist='3'` där `iBlacklist` är ett numeriskt fält och `3` anger ett textvärde.

   Kontrollera att du vet vilken körningsplan din fråga kommer att ha. Undvik fullständiga tabellsökningar, särskilt för realtidsfrågor eller nästan realtidsfrågor som körs varje minut.

Mer information finns[i avsnitten om datamodellens bästa praxis](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html) och [Databasmappning](../../configuration/using/database-mapping.md) .

### Funktioner {#functions}

* Se upp för funktioner som `Lower(...)`. När funktionen Nedre används används inte indexvärdet.
* Kontrollera frågor med &quot;gilla&quot;-instruktionen eller &quot;övre&quot; eller &quot;nedre&quot; instruktionerna noggrant. Använd &quot;Upper&quot; på användarindata, inte i databasfältet.

   Mer information om funktioner finns i [det här avsnittet](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Filtrera dimensioner {#filtering-dimensions}

Använd frågans filtreringsdimension i stället för att använda operatorn &quot;finns som&quot;.

![](assets/optimize-queries-filtering.png)

I frågor är villkoret &quot;finns till exempel&quot; i filter inte effektivt. De motsvarar en underfråga i SQL:

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

Det bästa sättet är att använda frågefiltret i stället:

![](assets/optimize-queries-filtering2.png)

Motsvarigheten till filterdimensionen i SQL är den inre kopplingen:

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

Mer information om filtreringsdimensioner finns i [det här avsnittet](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).

### Arkitektur {#architecture}

* Bygg en utvecklingsplattform med liknande volymer, parametrar och arkitektur som produktionsplattformen.
* Använd samma värden för utvecklings- och produktionsmiljöer. Använd så mycket som möjligt på samma sätt:

   * Operativsystem,
   * Version,
   * Data,
   * Program,
   * Volymer.
   >[!NOTE]
   >
   >En funktion som fungerar i en utvecklingsmiljö kanske inte fungerar i en produktionsmiljö där data kan vara annorlunda. Försök att identifiera de viktigaste skillnaderna för att förutse risker och förbereda lösningar.

* Gör konfigurationer som matchar målvolymerna. Stora volymer kräver särskilda konfigurationer. En konfiguration som fungerade för 100 000 mottagare kanske inte fungerar för 10 000 000 mottagare.

   Tänk på hur systemet skalförändras när det publiceras. Bara för att något fungerar i liten skala innebär det inte att det är lämpligt med större volymer. Testerna bör utföras med liknande volymer som produktionsvolymen. Du bör också utvärdera effekten av volymförändringar (antal anrop, databasens storlek) vid högsta antal timmar, högsta antal dagar och under projektets hela livstid.
