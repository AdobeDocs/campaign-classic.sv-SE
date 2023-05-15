---
product: campaign
title: Publicera, spåra och använd insamlade data
description: Lär dig publicera, spåra och använda data som samlats in i en undersökning
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '831'
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

För varje enkät som levereras kan du följa svaren i **[!UICONTROL Logs]** -fliken. På den här fliken visas en lista med de användare som har slutfört undersökningen och deras ursprung:

![](assets/s_ncs_admin_survey_logs.png)

Dubbelklicka på en rad för att visa enkätformuläret ifyllt av svaranden. Du kan bläddra igenom hela undersökningen och få tillgång till svaren i sin helhet. Dessa kan exporteras i en extern fil. Mer information finns i [Exportera svar](#exporting-answers).

Ursprunget anges i URL:en för undersökningen genom att följande tecken läggs till:

```
?origin=xxx
```

medan enkäten redigeras innehåller URL-adressen parametern **[!UICONTROL __uuid]**, vilket anger att den är i testfas och ännu inte är online. När du kommer åt undersökningen via den här URL:en beaktas inte de poster som skapas i spårningen (rapporter). Ursprunget tvingas till värdet **[!UICONTROL Adobe Campaign]**.

Mer information om URL-parametrar finns i [den här sidan](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### Rapporter om undersökningar {#reports-on-surveys}

På fliken Kontrollpanel kan du få åtkomst till undersökningsrapporter. Klicka på ett rapportnamn för att visa det.

![](assets/s_ncs_admin_survey_report_doc.png)

Undersökningsstrukturen visas i **[!UICONTROL Documentation]** rapport.

Två andra rapporter om webbundersökningar finns i **[!UICONTROL Reports]** fliken för enkäterna: **[!UICONTROL General]** och **[!UICONTROL Breakdown of responses]**.

* Allmänt

   Rapporten innehåller allmän information om undersökningen: hur antalet svar ändras över tid och fördelningen per ursprung och språk.

   Exempel på en allmän rapport:

   ![](assets/s_ncs_admin_survey_report_0.png)

* Uppdelning av svar

   Den här rapporten visar hur svaren för varje fråga är uppdelade. Uppdelningen är bara tillgänglig för svar som ges till fält som lagras i **[!UICONTROL Question]** typbehållare. Den är bara giltig för markeringskontroller (ingen uppdelning på textfält, till exempel).

   ![](assets/s_ncs_admin_survey_report_2.png)

## Exportera svar {#exporting-answers}

Svar på en undersökning kan exporteras i en extern fil som kan bearbetas senare. Det finns två sätt att göra detta:

1. Exporterar rapportdata

   Om du vill exportera rapportdata klickar du på **[!UICONTROL Export]** och välj exportformat.

   Mer information om hur du exporterar rapportdata finns i [det här avsnittet](../../reporting/using/about-reports-creation-in-campaign.md).

1. Exportera svar

   Om du vill exportera svaren klickar du på **[!UICONTROL Responses]** -fliken i enkäten och högerklicka. Välj **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   Ange sedan den information du vill exportera och lagringsfilen.

   Du kan konfigurera innehåll och format för utdatafilen i exportguiden.

   På så sätt kan du:

   * lägga till kolumner i utdatafilen och återskapa informationen om mottagaren (som lagras i databasen),
   * formatera exporterade data,
   * Välj kodningsformat för informationen i filen.

   Om undersökningen du vill exportera innehåller flera **[!UICONTROL Multi-line text]** eller **[!UICONTROL HTML text]** fält, måste exporteras i **[!UICONTROL XML]** format. Välj det här formatet i listrutan i dialogrutan **[!UICONTROL Output format]** fält, enligt nedan:

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   Klicka **[!UICONTROL Start]** för att köra exporten.

   >[!NOTE]
   >
   >Dataexport och konfigurationsstadierna beskrivs i [det här avsnittet](../../platform/using/about-generic-imports-exports.md).

## Använda insamlade data {#using-the-collected-data}

Den information som samlas in via online-enkäter kan återvinnas inom ramen för ett målinriktat arbetsflöde. Om du vill göra det använder du **[!UICONTROL Survey responses]** box.

I följande exempel vill vi göra ett webberbjudande speciellt för de fem mottagarna med minst två barn och med högst poäng i en nätundersökning. Svaren på den här enkäten är:

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

I arbetsflödet för målinriktning **[!UICONTROL Survey responses]** kommer att konfigureras enligt följande:

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

Börja med att välja den berörda enkäten och sedan de data som ska extraheras i fönstrets centrala del. I det här fallet måste vi extrahera minst spalten eftersom den kommer att användas i delningsrutan för att återställa de fem högsta poängen.

Ange filtreringsvillkoren för svar genom att klicka på **[!UICONTROL Edit query...]** länk.

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

Starta arbetsflödet för målinriktning. Frågan återställer 8 mottagare.

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

Högerklicka på utdataövergången för samlingsrutan för att visa dem.

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

Placera sedan en delad ruta i arbetsflödet för att återställa de fem mottagare som har högst poäng.

Konfigurera delningsrutan genom att redigera den:

* Börja med att välja lämpligt schema i dialogrutan **[!UICONTROL General]** och sedan konfigurera delmängden:

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* Gå till **[!UICONTROL Sub-sets]** och väljer **[!UICONTROL Limit the selected records]** och sedan klicka på **[!UICONTROL Edit...]** länk.

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* Välj **[!UICONTROL Keep only the first records after sorting]** och markera sorteringskolumnen. Markera alternativet **[!UICONTROL Descending sort]**.

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* Klicka på **[!UICONTROL Next]** och begränsa antalet poster till 5.

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* Klicka **[!UICONTROL Finish]** starta sedan om arbetsflödet för att godkänna målanpassning.

## Standardisera data {#standardizing-data}

Det är möjligt att skapa standardiseringsprocesser i Adobe Campaign för data som samlas in med alias. På så sätt kan du standardisera de data som lagras i databasen: För att göra detta definierar du alias i de specificerade listorna som innehåller relevant information. [Läs mer](../../platform/using/managing-enumerations.md#about-enumerations)
