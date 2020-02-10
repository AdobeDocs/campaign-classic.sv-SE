---
title: Deduplicering
seo-title: Deduplicering
description: Deduplicering
seo-description: null
page-status-flag: never-activated
uuid: 90dee589-ac45-442e-89ef-1c14bb22200d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 83b915bd-7e23-41b5-9f9a-f7eb72026376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Deduplicering{#deduplication}

Borttagning av dubbletter tar bort dubbletter från resultatet av inkommande aktiviteter. Deduplicering kan utföras på e-postadressen, telefonnumret eller något annat fält.

## God praxis {#best-practices}

Vid borttagning av dubbletter behandlas inkommande flöden separat. Om till exempel mottagare A hittas i resultatet av fråga 1 och i resultatet av fråga 2, kommer de inte att dedupliceras.

Denna fråga måste åtgärdas på följande sätt:

* Skapa en **unionsaktivitet** för att förena varje inkommande flöde.
* Skapa en **borttagning av dubbletter** efter **unionsaktiviteten** .

![](assets/dedup_bonnepratique.png)

## Konfiguration {#configuration}

Om du vill konfigurera en borttagning av dubbletter anger du dess etikett, metod, borttagningsvillkor och alternativ för resultatet.

Klicka på **[!UICONTROL Edit configuration...]** länken för att definiera dedupliceringsläget.

![](assets/s_user_segmentation_dedup_param.png)

1. Målval

   Välj måltyp för den här aktiviteten (som standard gäller borttagning av dubbletter mottagare) och vilket kriterium som ska användas, dvs. fältet där identiska värden gör att du kan identifiera dubbletter: e-postadress, mobil- eller telefonnummer, faxnummer eller direkte-postadress.

   ![](assets/s_user_segmentation_dedup_param2.png)

   I nästa steg kan du välja vilket eller vilka villkor som ska användas: **[!UICONTROL Other]**

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Dedupliceringsmetoder

   I listrutan väljer du den borttagningsmetod som ska användas och anger antalet kopior som ska behållas.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Följande metoder är tillgängliga:

   * **[!UICONTROL Choose for me]**: markerar slumpmässigt den post som ska hållas utanför dubbletterna.
   * **[!UICONTROL Following a list of values]**: I kan du definiera en värdeprioritet för ett eller flera fält. Om du vill definiera värdena markerar du ett fält eller skapar ett uttryck och lägger sedan till värdena i rätt tabell. Om du vill definiera ett nytt fält klickar du på **[!UICONTROL Add]** knappen ovanför listan med värden.

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**: Detta gör att du kan behålla poster där värdet för det valda uttrycket inte är tomt som prioritet.

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**: I kan du behålla poster med det lägsta (eller högsta) värdet för det angivna uttrycket.

      ![](assets/s_user_segmentation_dedup_param7.png)
   Klicka **[!UICONTROL Finish]** för att godkänna den valda borttagningsmetoden.

   I fönstrets mellersta del sammanfattas den definierade konfigurationen.

   I det nedre avsnittet av aktivitetsredigeringsfönstret kan du ändra etiketten för den utgående övergången för det grafiska objektet och ange en segmentkod som ska associeras med aktivitetens resultat. Den här koden kan senare användas som riktningskriterium.

   ![](assets/s_user_segmentation_dedup_param8.png)

   Markera alternativet **[!UICONTROL Generate complement]** om du vill utnyttja den återstående populationen. Komplementet består av alla dubbletter. Därefter kommer ytterligare en övergång att läggas till i aktiviteten enligt följande:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Exempel: Identifiera dubbletter före leverans {#example--identify-the-duplicates-before-a-delivery}

I följande exempel gäller borttagningen av dubbletter kombinationen av tre frågor.

Målet med arbetsflödet är att definiera målet för en leverans genom att utesluta dubbletter så att det inte skickas till samma mottagare flera gånger.

De identifierade dubbletterna kommer också att integreras i en dedikerad dubblettlista som kan återanvändas om det behövs.

![](assets/deduplication_example.png)

1. Lägg till och länka de olika aktiviteter som krävs för att arbetsflödet ska fungera enligt ovan.

   Unionsaktiviteten används här för att&quot;sammanfoga&quot; de tre frågorna till en enda övergång. Det innebär att borttagning av dubbletter inte fungerar för varje fråga separat, utan för hela frågan. Mer information om detta finns i [Bästa praxis](#best-practices).

1. Öppna dedupliceringsaktiviteten och klicka sedan på **[!UICONTROL Edit configuration...]** länken för att definiera dedupliceringsläget.
1. I det nya fönstret väljer du **[!UICONTROL Database schema]**.
1. Välj **Mottagare** som mål och filtreringsdimensioner.
1. Markera ID-fältet för **[!UICONTROL Email]** dubbletterna om du bara vill skicka leveransen en gång till varje e-postadress och sedan klicka på **[!UICONTROL Next]**.

   Om du vill basera dubblett-ID:n på ett visst fält väljer du **[!UICONTROL Other]** att få åtkomst till listan med tillgängliga fält.

1. Välj om du bara vill behålla en post när samma e-postadress identifieras för flera mottagare.
1. Välj läget för borttagning av dubbletter så att de poster som sparas om dubbletter identifieras väljs slumpmässigt och klicka sedan på **[!UICONTROL Choose for me]** **[!UICONTROL Finish]**.

När arbetsflödet körs exkluderas alla mottagare som identifieras som dubbletter från resultatet (och därmed leveransen) och läggs till i dubblettlistan. Den här listan kan användas igen i stället för att du behöver identifiera dubbletterna igen.

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som skapas av borttagningen av dubbletter. **[!UICONTROL tableName]** är namnet på tabellen som sparar målidentifierare, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.
