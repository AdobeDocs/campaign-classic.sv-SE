---
title: Publicera, spåra och använda insamlade data
seo-title: Publicera, spåra och använda insamlade data
description: Publicera, spåra och använda insamlade data
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Publicera, spåra och använda insamlade data{#publish-track-and-use-collected-data}

När formuläret har skapats, konfigurerats och publicerats kan du dela länken med målgruppen och spåra svaren.

>[!NOTE]
>
>Livscykeln för en enkät i Adobe Campaign och dess publicerings- och leveranssätt liknar den för webbformulär: beskrivs i [detta avsnitt](../../web/using/about-web-forms.md).

## Kontrollpanel för undersökning {#survey-dashboard}

Varje undersökning har en egen kontrollpanel där du kan visa status, beskrivning, offentlig URL och tillgänglighetsschema. Här kan du även visa tillgängliga rapporter. Mer information finns i [Rapporter om undersökningar](#reports-on-surveys).

Undersökningens offentliga URL visas på kontrollpanelen:

![](assets/survey_public_url.png)

## Svarsspårning {#response-tracking}

Du kan spåra svaren på undersökningen i loggar och rapporter.

### Undersökningsloggar {#survey-logs}

För varje enkät som levereras kan du spåra svaren på **[!UICONTROL Logs]** fliken. På den här fliken visas en lista med de användare som har slutfört undersökningen och deras ursprung:

![](assets/s_ncs_admin_survey_logs.png)

Dubbelklicka på en rad för att visa enkätformuläret ifyllt av svaranden. Du kan bläddra igenom hela undersökningen och få tillgång till svaren i sin helhet. Dessa kan exporteras i en extern fil. Mer information finns i [Exportera svar](#exporting-answers).

Ursprunget anges i URL:en för undersökningen genom att följande tecken läggs till:

```
?origin=xxx
```

medan undersökningen redigeras innehåller URL-adressen parametern **[!UICONTROL __uuid]**, vilket anger att den är i testfasen och inte online än. När du kommer åt undersökningen via den här URL:en beaktas inte de poster som skapas i spårningen (rapporter). Ursprunget tvingas till värdet **[!UICONTROL Adobe Campaign]**.

Mer information om URL-parametrar finns på [den här sidan](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Rapporter om undersökningar {#reports-on-surveys}

På fliken Kontrollpanel kan du få åtkomst till undersökningsrapporter. Klicka på ett rapportnamn för att visa det.

![](assets/s_ncs_admin_survey_report_doc.png)

Undersökningsstrukturen visas i **[!UICONTROL Documentation]** rapporten.

Två andra rapporter om webbundersökningar finns på fliken **[!UICONTROL Reports]** för enkäterna: **[!UICONTROL General]** och **[!UICONTROL Breakdown of responses]**.

* Allmänt

   Rapporten innehåller allmän information om undersökningen: hur antalet svar ändras över tid och fördelningen per ursprung och språk.

   Exempel på en allmän rapport:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Uppdelning av svar

   Den här rapporten visar hur svaren för varje fråga är uppdelade. Den här uppdelningen är bara tillgänglig för svar som ges till fält som lagras i **[!UICONTROL Question]** typbehållare. Den är bara giltig för markeringskontroller (ingen uppdelning på textfält, till exempel).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Exportera svar {#exporting-answers}

Svar på en undersökning kan exporteras i en extern fil som kan bearbetas senare. Det finns två sätt att göra detta:

1. Exporterar rapportdata

   Om du vill exportera rapportdata klickar du på **[!UICONTROL Export]** knappen och väljer exportformat.

   Mer information om hur du exporterar rapportdata finns i [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md).

1. Exportera svar

   Om du vill exportera svaren klickar du på fliken **[!UICONTROL Responses]** i enkäten och högerklickar. Välj **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Ange sedan den information du vill exportera och lagringsfilen.

   Du kan konfigurera innehåll och format för utdatafilen i exportguiden.

   På så sätt kan du:

   * lägga till kolumner i utdatafilen och återskapa informationen om mottagaren (som lagras i databasen),
   * formatera exporterade data,
   * Välj kodningsformat för informationen i filen.
   Om undersökningen du vill exportera innehåller flera **[!UICONTROL Multi-line text]** eller **[!UICONTROL HTML text]** fält måste den exporteras i **[!UICONTROL XML]** format. Det gör du genom att välja det här formatet i listrutan i **[!UICONTROL Output format]** fältet enligt nedan:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Klicka **[!UICONTROL Start]** för att köra exporten.

   >[!NOTE]
   >
   >Dataexport och konfigurationsstadierna beskrivs i [det här avsnittet](../../platform/using/generic-imports-and-exports.md).

## Använda insamlade data {#using-the-collected-data}

Den information som samlas in via online-enkäter kan återvinnas inom ramen för ett målinriktat arbetsflöde. Använd **[!UICONTROL Survey responses]** rutan för att göra detta.

I följande exempel vill vi göra ett webberbjudande speciellt för de fem mottagarna med minst två barn och med högst poäng i en nätundersökning. Svaren på den här enkäten är:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

I arbetsflödet för målanpassning **[!UICONTROL Survey responses]** kommer den att konfigureras enligt följande:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Börja med att välja den berörda enkäten och sedan de data som ska extraheras i fönstrets centrala del. I det här fallet måste vi extrahera minst spalten eftersom den kommer att användas i delningsrutan för att återställa de fem högsta poängen.

Ange filtreringsvillkoren för svar genom att klicka på **[!UICONTROL Edit query...]** länken.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Starta arbetsflödet för målinriktning. Frågan återställer 8 mottagare.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Högerklicka på utdataövergången för samlingsrutan för att visa dem.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Placera sedan en delad ruta i arbetsflödet för att återställa de fem mottagare som har högst poäng.

Konfigurera delningsrutan genom att redigera den:

* Börja med att välja lämpligt schema på **[!UICONTROL General]** fliken och konfigurera sedan delmängden:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Gå till **[!UICONTROL Sub-sets]** fliken och markera **[!UICONTROL Limit the selected records]** alternativet och klicka sedan på **[!UICONTROL Edit...]** länken.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Markera **[!UICONTROL Keep only the first records after sorting]** alternativet och markera sorteringskolumnen. Markera **[!UICONTROL Descending sort]** alternativet.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Klicka på **[!UICONTROL Next]** knappen och begränsa antalet poster till 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Klicka **[!UICONTROL Finish]** och starta sedan om arbetsflödet för att godkänna målanpassning.

## Standardisera data {#standardizing-data}

Det går att skapa standardiseringsprocesser i Adobe Campaign för data som samlas in med alias. På så sätt kan du standardisera de data som lagras i databasen: För att göra detta definierar du alias i de specificerade listorna som innehåller relevant information.

Mer information finns på [den här sidan](../../platform/using/managing-enumerations.md#about-enumerations).
