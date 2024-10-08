---
product: campaign
title: Publicera, spåra och använd insamlade data
description: Lär dig publicera, spåra och använda data som samlats in i en undersökning
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 2%

---

# Publicera, spåra och använd insamlade data{#publish-track-and-use-collected-data}



När formuläret har skapats, konfigurerats och publicerats kan du dela länken med målgruppen och spåra svaren.

>[!NOTE]
>
>Livscykeln för en enkät i Adobe Campaign och dess publicerings- och leveranssätt liknar den för webbformulär: dessa beskrivs i [det här avsnittet](../../web/using/about-web-forms.md).

## Kontrollpanel för undersökning {#survey-dashboard}

Varje undersökning har en egen kontrollpanel där du kan visa status, beskrivning, offentlig URL och tillgänglighetsschema. Här kan du även visa tillgängliga rapporter. [Läs mer](#reports-on-surveys).

Undersökningens offentliga URL visas på kontrollpanelen:

![](assets/survey_public_url.png)

## Svarsspårning {#response-tracking}

Du kan spåra svaren på undersökningen i loggar och rapporter.

### Undersökningsloggar {#survey-logs}

Du kan spåra svaren på fliken **[!UICONTROL Logs]** för varje enkät som levereras. På den här fliken visas en lista med de användare som har slutfört undersökningen och deras ursprung:

![](assets/s_ncs_admin_survey_logs.png)

Dubbelklicka på en rad för att visa enkätformuläret ifyllt av svaranden. Du kan bläddra igenom hela undersökningen och få tillgång till svaren i sin helhet. Dessa kan exporteras i en extern fil. Mer information finns i [Exportera svar](#exporting-answers).

Ursprunget anges i undersökningens URL genom att följande tecken läggs till:

```
?origin=xxx
```

När enkäten redigeras innehåller URL-adressen parametern **[!UICONTROL __uuid]**, vilket anger att den är i testfasen och inte online än. När du kommer åt undersökningen via den här URL:en beaktas inte de poster som skapas i spårningen (rapporter). Ursprunget tvingas till värdet **[!UICONTROL Adobe Campaign]**.

Mer information om URL-parametrar finns på [den här sidan](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Rapporter om undersökningar {#reports-on-surveys}

På fliken Kontrollpanel kan du få åtkomst till undersökningsrapporter. Klicka på ett rapportnamn för att visa det.

![](assets/s_ncs_admin_survey_report_doc.png)

Undersökningsstrukturen visas i rapporten **[!UICONTROL Documentation]**.

Två andra rapporter om webbundersökningar finns på fliken **[!UICONTROL Reports]** i enkäterna: **[!UICONTROL General]** och **[!UICONTROL Breakdown of responses]**.

* Allmänt

  Den här rapporten innehåller allmän information om undersökningen: hur antalet svar ändras över tiden och fördelningen per ursprung och språk.

  Exempel på en allmän rapport:

  ![](assets/s_ncs_admin_survey_report_0.png)

* Uppdelning av svar

  Den här rapporten visar hur svaren för varje fråga är uppdelade. Den här uppdelningen är bara tillgänglig för svar som ges till fält som lagras i **[!UICONTROL Question]**-typbehållare. Den är bara giltig för markeringskontroller (ingen uppdelning på textfält, till exempel).

  ![](assets/s_ncs_admin_survey_report_2.png)

## Exportera svar {#exporting-answers}

Svar på en undersökning kan exporteras i en extern fil som kan bearbetas senare. Det finns två sätt att göra detta:

1. Exporterar rapportdata

   Om du vill exportera rapportdata klickar du på knappen **[!UICONTROL Export]** och väljer exportformat.

   Mer information om hur du exporterar rapportdata finns i [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md).

1. Exportera svar

   Om du vill exportera svar klickar du på fliken **[!UICONTROL Responses]** i enkäten och högerklickar. Välj **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Ange sedan den information du vill exportera och lagringsfilen.

   Du kan konfigurera innehåll och format för utdatafilen i exportassistenten.

   På så sätt kan du:

   * lägga till kolumner i utdatafilen och återskapa informationen om mottagaren (som lagras i databasen),
   * formatera exporterade data,
   * Välj kodningsformat för informationen i filen.

   Om undersökningen som du vill exportera innehåller flera **[!UICONTROL Multi-line text]**- eller **[!UICONTROL HTML text]**-fält måste den exporteras i **[!UICONTROL XML]**-format. Om du vill göra det väljer du det här formatet i listrutan för fältet **[!UICONTROL Output format]**, vilket visas nedan:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Klicka på **[!UICONTROL Start]** för att köra exporten.

   >[!NOTE]
   >
   >Dataexport och konfigurationsstadierna beskrivs i [det här avsnittet](../../platform/using/about-generic-imports-exports.md).

## Använda insamlade data {#using-the-collected-data}

Den information som samlas in via online-enkäter kan återvinnas inom ramen för ett målinriktat arbetsflöde. Använd rutan **[!UICONTROL Survey responses]** om du vill göra det.

I följande exempel vill vi göra ett webberbjudande speciellt för de fem mottagarna med minst två barn och med högst poäng i en nätundersökning. Svaren på den här enkäten är:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

I målarbetsflödet kommer **[!UICONTROL Survey responses]** att konfigureras enligt följande:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Börja med att välja den berörda enkäten och sedan de data som ska extraheras i fönstrets centrala del. I det här fallet måste vi extrahera minst spalten eftersom den kommer att användas i delningsrutan för att återställa de fem högsta poängen.

Ange filtreringsvillkoren för svar genom att klicka på länken **[!UICONTROL Edit query...]**.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Starta arbetsflödet för målinriktning. Frågan återställer 8 mottagare.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Högerklicka på utdataövergången för samlingsrutan för att visa dem.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Placera sedan en delad ruta i arbetsflödet för att återställa de fem mottagare som har högst poäng.

Konfigurera delningsrutan genom att redigera den:

* Börja med att välja lämpligt schema på fliken **[!UICONTROL General]** och konfigurera sedan delmängden:

  ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Gå till fliken **[!UICONTROL Sub-sets]**, välj alternativet **[!UICONTROL Limit the selected records]** och klicka sedan på länken **[!UICONTROL Edit...]**.

  ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Välj alternativet **[!UICONTROL Keep only the first records after sorting]** och markera sorteringskolumnen. Markera alternativet **[!UICONTROL Descending sort]**.

  ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Klicka på knappen **[!UICONTROL Next]** och begränsa antalet poster till 5.

  ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Klicka på **[!UICONTROL Finish]** och starta sedan om arbetsflödet för att godkänna mål.

## Standardisera data {#standardizing-data}

Det är möjligt att skapa standardiseringsprocesser i Adobe Campaign för data som samlas in med alias. På så sätt kan du standardisera de data som lagras i databasen: för att göra det definierar du alias i de specificerade listorna som innehåller relevant information. [Läs mer](../../platform/using/managing-enumerations.md#about-enumerations)
