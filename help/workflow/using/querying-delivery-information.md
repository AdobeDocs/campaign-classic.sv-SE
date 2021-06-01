---
product: campaign
title: Fråga om leveransinformation
description: Lär dig hur du hämtar leveransinformation
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: b699b064-1287-41c9-8d94-1c1aa2c145ab
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 1%

---

# Fråga om leveransinformation {#querying-delivery-information}

## Antal klick för en viss leverans {#number-of-clicks-for-a-specific-delivery}

I det här exemplet försöker vi återställa antalet klick för en viss leverans. Dessa klick spelas in tack vare loggar för mottagarspårning som tagits under en viss period. Mottagaren identifieras via sin e-postadress. Den här frågan använder tabellen **[!UICONTROL Recipient tracking logs]**.

* Vilken tabell måste markeras?

   Loggspårningstabellen för mottagare (**[!UICONTROL nms:trackingLogRcp]**)

* Fält som ska markeras för utdatakolumner?

   Primär nyckel (med antal) och e-post

* Vilka kriterier kommer informationen att filtreras baserat på?

   En viss period och ett element i leveransetiketten

Så här utför du det här exemplet:

1. Öppna **[!UICONTROL Generic query editor]** och välj schemat **[!UICONTROL Recipient tracking logs]**.

   ![](assets/query_editor_tracklog_05.png)

1. I fönstret **[!UICONTROL Data to extract]** vill vi skapa en sammanställning för att samla in information. Det gör du genom att lägga till primärnyckeln (som finns ovanför huvudelementet **[!UICONTROL Recipient tracking logs]**): Spårningsloggen utförs i det här **[!UICONTROL Primary key]**-fältet. Det redigerade uttrycket kommer att vara **[!UICONTROL x=count(primary key)]**. Den länkar summan av olika spårningsloggar till en enda e-postadress.

   Så här gör du:

   * Klicka på ikonen **[!UICONTROL Add]** till höger om fältet **[!UICONTROL Output columns]**. I fönstret **[!UICONTROL Formula type]** väljer du alternativet **[!UICONTROL Edit the formula using an expression]** och klickar på **[!UICONTROL Next]**. Klicka på **[!UICONTROL Advanced selection]** i fönstret **[!UICONTROL Field to select]**.

      ![](assets/query_editor_tracklog_06.png)

   * Kör en process på sammanställningsfunktionen i fönstret **[!UICONTROL Formula type]**. Den här processen blir ett primärnyckelantal.

      Välj **[!UICONTROL Process on an aggregate function]** i avsnittet **[!UICONTROL Aggregate]** och klicka på **[!UICONTROL Count]**.

      ![](assets/query_editor_nveau_18.png)

      Klicka på **[!UICONTROL Next]**.

   * Markera fältet **[!UICONTROL Primary key (@id)]**. Utdatakolumnen **[!UICONTROL count (primary key)]** har konfigurerats.

      ![](assets/query_editor_nveau_19.png)

1. Markera det andra fältet som ska visas i utdatakolumnen. Öppna noden **[!UICONTROL Recipient]** i kolumnen **[!UICONTROL Available fields]** och välj **[!UICONTROL Email]**. Markera rutan **[!UICONTROL Group]** till **[!UICONTROL Yes]** om du vill gruppera spårningsloggarna efter e-postadress: den här gruppen länkar varje logg till mottagaren.

   ![](assets/query_editor_nveau_20.png)

1. Konfigurera kolumnsortering så att de mest aktiva mottagarna (med de flesta spårningsloggar) visas först. Markera **[!UICONTROL Yes]** i kolumnen **[!UICONTROL Descending sort]**.

   ![](assets/query_editor_nveau_64.png)

1. Du måste sedan filtrera loggarna som intresserar dig, dvs. de som är yngre än två veckor och som avser försäljningsrelaterade leveranser.

   Så här gör du:

   * Konfigurera datafiltrering. Om du vill göra det väljer du **[!UICONTROL Filter conditions]** och klickar sedan på **[!UICONTROL Next]**.

      ![](assets/query_editor_nveau_22.png)

   * Återställ spårningsloggar under en viss period för en viss leverans. Tre filtervillkor krävs: Två datumvillkor för att fastställa söktiden mellan två veckor före dagens datum och dagen före dagens datum. och ett annat villkor som begränsar sökningen till en viss leverans.

      I fönstret **[!UICONTROL Target element]** anger du det datum som börjar när spårningsloggar ska användas. Klicka på **[!UICONTROL Add]**. En villkorslinje visas. Redigera kolumnen **[!UICONTROL Expression]** genom att klicka på funktionen **[!UICONTROL Edit expression]**. Välj **[!UICONTROL Date (@logDate)]** i fönstret **[!UICONTROL Field to select]**.

      ![](assets/query_editor_nveau_23.png)

      Välj operatorn **[!UICONTROL greater than]**. Klicka på **[!UICONTROL Edit expression]** i kolumnen **[!UICONTROL Value]** och välj **[!UICONTROL Process on dates]** i fönstret **[!UICONTROL Formula type]**. I **[!UICONTROL Current date minus n days]** anger du slutligen &quot;15&quot;.

      Klicka på **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_24.png)

   * Om du vill välja slutdatum för spårningsloggssökningen skapar du ett andra villkor genom att klicka på **[!UICONTROL Add]**. Välj **[!UICONTROL Date (@logDate)]** igen i kolumnen **[!UICONTROL Expression]**.

      Välj operatorn **[!UICONTROL less than]**. Klicka på **[!UICONTROL Edit expression]** i kolumnen **[!UICONTROL Value]**. Gå till fönstret **[!UICONTROL Formula type]** och ange &quot;1&quot; i **[!UICONTROL Current date minus n days]** för datumbearbetning.

      Klicka på **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_65.png)

      Nu vill vi konfigurera det tredje filtervillkoret, dvs. den leveransetikett som vår fråga gäller.

   * Klicka på funktionen **[!UICONTROL Add]** för att skapa ett annat filtervillkor. Klicka på **[!UICONTROL Edit expression]** i kolumnen **[!UICONTROL Expression]**. I fönstret **[!UICONTROL Field to select]** väljer du **[!UICONTROL Label]** i noden **[!UICONTROL Delivery]**.

      Klicka på **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_66.png)

      Sök efter en leverans som innehåller ordet&quot;försäljning&quot;. Eftersom du inte kommer ihåg den exakta etiketten kan du välja operatorn **[!UICONTROL contains]** och ange &quot;sales&quot; i kolumnen **[!UICONTROL Value]**.

      ![](assets/query_editor_nveau_25.png)

1. Klicka på **[!UICONTROL Next]** tills du kommer till fönstret **[!UICONTROL Data preview]**: ingen formatering behövs här.
1. I fönstret **[!UICONTROL Data preview]** klickar du på **[!UICONTROL Start the preview of the data]** för att visa antalet spårningsloggar för varje leveransmottagare.

   Resultatet visas i fallande ordning.

   ![](assets/query_editor_tracklog_04.png)

   Det högsta antalet loggar för en användare är 6 för den här leveransen. 5 olika användare öppnade e-postmeddelandet eller klickade på någon av länkarna i e-postmeddelandet.

## Mottagare som inte öppnade någon leverans {#recipients-who-did-not-open-any-delivery}

I det här exemplet vill vi filtrera mottagare som inte har öppnat ett e-postmeddelande de senaste 7 dagarna.

Så här skapar du det här exemplet:

1. Dra och släpp en **[!UICONTROL Query]**-aktivitet i ett arbetsflöde och öppna aktiviteten.
1. Klicka på **[!UICONTROL Edit query]** och ställ in mål- och filterdimensionerna på **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Välj **[!UICONTROL Filtering conditions]** och klicka sedan på **[!UICONTROL Next]**.
1. Klicka på knappen **[!UICONTROL Add]** och välj **[!UICONTROL Tracking logs]**.
1. Ange **[!UICONTROL Operator]** för uttrycket **[!UICONTROL Tracking logs]** som **[!UICONTROL Do not exist such as]**.

   ![](assets/query_open_1.png)

1. Lägg till ett annat uttryck. Välj **[!UICONTROL Type]** i kategorin **[!UICONTROL URL]**.
1. Ställ sedan in **[!UICONTROL Operator]** på **[!UICONTROL equal to]** och **[!UICONTROL Value]** på **[!UICONTROL Open]**.

   ![](assets/query_open_2.png)

1. Lägg till ett annat uttryck och välj **[!UICONTROL Date]**. **[!UICONTROL Operator]** ska anges till  **[!UICONTROL on or after]**.

   ![](assets/query_open_3.png)

1. Klicka på knappen **[!UICONTROL Edit expression]** i fältet **[!UICONTROL Value]** för att ange värdet för de senaste 7 dagarna.
1. Välj **[!UICONTROL Current date minus n days]** i kategorin **[!UICONTROL Function]** och lägg till det antal dagar som du vill ha som mål. Här vill vi rikta in oss på de senaste 7 dagarna.

   ![](assets/query_open_4.png)

Din utgående övergång kommer att innehålla mottagare som inte öppnat ett e-postmeddelande de senaste 7 dagarna.

Om du däremot vill filtrera mottagare som har öppnat minst ett e-postmeddelande bör frågan vara som följer. Observera att i det här fallet ska **[!UICONTROL Filtering dimension]** vara inställt på **[!UICONTROL Tracking logs (Recipients)]**.

![](assets/query_open_5.png)

## Mottagare som har öppnat en leverans {#recipients-who-have-opened-a-delivery}

I följande exempel visas hur man riktar sig till profiler som har öppnat en leverans de senaste två veckorna:

1. Om du vill ha målprofiler som har öppnat en leverans måste du använda spårningsloggar. De lagras i en länkad tabell: börja med att markera den här tabellen i listrutan för fältet **[!UICONTROL Filtering dimension]**, vilket visas nedan:

   ![](assets/s_advuser_query_sample1.0.png)

1. När det gäller filtreringsvillkor klickar du på ikonen **[!UICONTROL Edit expression]** för de villkor som visas i spårningsloggarnas underträdstruktur. Markera fältet **[!UICONTROL Date]**.

   ![](assets/s_advuser_query_sample1.1.png)

   Klicka på **[!UICONTROL Finish]** för att bekräfta markeringen.

   Om du bara vill återställa spårningsloggarna som är mindre än två veckor gamla väljer du operatorn **[!UICONTROL Greater than]**.

   ![](assets/s_advuser_query_sample1.4.png)

   Klicka sedan på ikonen **[!UICONTROL Edit expression]** i kolumnen **[!UICONTROL Value]** för att definiera beräkningsformeln som ska användas. Välj formeln **[!UICONTROL Current date minus n days]** och ange 15 i det relaterade fältet.

   ![](assets/s_advuser_query_sample1.5.png)

   Klicka på knappen **[!UICONTROL Finish]** i formelfönstret. Klicka på fliken **[!UICONTROL Preview]** i filtreringsfönstret för att kontrollera målinriktningsvillkoren.

   ![](assets/s_advuser_query_sample1.6.png)

## Filtrera mottagarnas beteende efter en leverans {#filtering-recipients--behavior-folllowing-a-delivery}

I ett arbetsflöde kan du välja ett beteende efter en tidigare leverans med hjälp av rutorna **[!UICONTROL Query]** och **[!UICONTROL Split]**. Markeringen görs via filtret **[!UICONTROL Delivery recipient]**.

* Syfte med exemplet

   I ett leveransarbetsflöde finns det flera sätt att följa upp en första e-postkommunikation. Den här typen av åtgärd använder du rutan **[!UICONTROL Split]**.

* Kontext

   Sommarsportserbjudandet skickas ut. Fyra dagar efter leveransen skickas två andra leveranser. Ett av dem är &quot;vattensporterbjudande&quot;, det andra är en uppföljning av det första &quot;Sommarsportserbjudandet&quot;.

   Leveransen av&quot;vattensporterbjudandet&quot; skickas till mottagare som klickade på länken&quot;vattensporter&quot; vid första leveransen. Dessa klick visar att mottagaren är intresserad av ämnet. Det är rimligt att styra dem mot liknande erbjudanden. Mottagare som inte klickade i &quot;Sommarsportserbjudandet&quot; kommer dock att få samma innehåll igen.

Följande steg visar hur du konfigurerar rutan **[!UICONTROL Split]** genom att integrera två olika beteenden:

1. Infoga **[!UICONTROL Split]**-rutan i arbetsflödet. I den här rutan delas mottagarna av den första leveransen upp i de två följande leveranserna. Uppdelningen görs utifrån de filtervillkor som är kopplade till mottagarens beteende under den första leveransen.

   ![](assets/query_editor_ex_09.png)

1. Öppna rutan **[!UICONTROL Split]**. Ange en etikett på fliken **[!UICONTROL General]**: **Dela baserat på beteende** till exempel.

   ![](assets/query_editor_ex_04.png)

1. Definiera den första delade grenen på fliken **[!UICONTROL Subsets]**. Ange till exempel etiketten **klickad** för den här grenen.
1. Välj alternativet **[!UICONTROL Add a filtering condition on the incoming population]**. Klicka på **[!UICONTROL Edit]**.
1. Dubbelklicka på filtret **[!UICONTROL Recipients of a delivery]** i fönstret **[!UICONTROL Targeting and filtering dimension]**.

   ![](assets/query_editor_ex_05.png)

1. I fönstret **[!UICONTROL Target element]** väljer du det beteende som du vill tillämpa på den här grenen: **[!UICONTROL Recipients having clicked (email)]**.

   Välj alternativet **[!UICONTROL Delivery specified by the transition]** nedan. Den här funktionen återställer automatiskt de personer som ska användas vid den första leveransen.

   Det här är erbjudandet om vattensporter.

   ![](assets/query_editor_ex_08.png)

1. Definiera den andra grenen. Den här grenen kommer att innehålla uppföljningsmejl med samma innehåll som den första leveransen. Gå till fliken **[!UICONTROL Subsets]** och klicka på **[!UICONTROL Add]** för att skapa den.

   ![](assets/query_editor_ex_06.png)

1. En annan underflik visas. Namnge den &quot;**Klick inte**&quot;.
1. Klicka på **[!UICONTROL Add a filtering condition for the incoming population]**. Klicka sedan på **[!UICONTROL Edit...]**.

   ![](assets/query_editor_ex_07.png)

1. Klicka på **[!UICONTROL Delivery recipients]** i fönstret **[!UICONTROL Targeting and filtering dimension]**.
1. I fönstret **[!UICONTROL Target element]** väljer du beteendet **[!UICONTROL Recipients who did not click (email)]**. Välj alternativet **[!UICONTROL Delivery specified by the transition]** så som visas för den senaste grenen.

   Rutan **[!UICONTROL Split]** är nu helt konfigurerad.

   ![](assets/query_editor_ex_03.png)

Nedan finns en lista över de olika komponenter som konfigurerats som standard:

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

   ![](assets/query_editor_ex_02.png)
