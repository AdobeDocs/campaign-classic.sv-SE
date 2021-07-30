---
product: campaign
title: Designa en undersökning
description: Lär dig viktiga steg för att utforma en enkät
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
source-git-commit: 86963746d3de3396963d221ddbd1ef7d89733d2f
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 2%

---

# Designa en undersökning{#building-a-survey}

## Skapa en ny undersökning {#creating-a-new-survey}

I det här kapitlet beskrivs hur du utformar ett **undersökningsformulär** med Adobe Campaign, samt vilka alternativ och konfigurationer som är tillgängliga. Med Adobe Campaign kan du göra enkäten tillgänglig för användare och samla in och arkivera svar i databasen.

Webbformulär nås via noden **[!UICONTROL Resources > Online > Web applications]** i trädet. Om du vill skapa en undersökning klickar du på **[!UICONTROL New]** ovanför listan med program eller högerklickar på listan och väljer **[!UICONTROL New]**.

Välj undersökningsmallen (**[!UICONTROL newSurvey]** som standard).

![](assets/s_ncs_admin_survey_select_template.png)

Formulärets sidor skapas med en särskild redigerare där du kan definiera och konfigurera (text) inmatningsfält, urvalsfält (listor, kryssrutor osv.) och statiska element (bilder, HTML-innehåll osv.). De kan samlas in i &quot;behållare&quot; och utformas enligt kraven. [Läs mer](#adding-questions)).

>[!NOTE]
>
>Mer information om hur du definierar innehåll och skapar skärmlayouter för ett webbformulär finns i [det här dokumentet](../../web/using/about-web-forms.md).

## Lägg till fält {#adding-fields}

Fälten i ett formulär gör det möjligt för användare att ange information och välja alternativ. För varje sida i formuläret skapas de via den första knappen i verktygsfältet med hjälp av menyn **[!UICONTROL Add using the wizard]**.

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>Du kan också använda ett högerklick och infoga en indatazon. Som standard infogas zonen i slutet av det markerade trädet. Flytta det med pilarna i verktygsfältet.

### Typ av fält {#types-of-fields}

När du lägger till ett fält i en undersökning måste du välja dess typ. Följande alternativ är tillgängliga:

1. **[!UICONTROL Answer a question]**: Med det här alternativet kan du deklarera ett nytt fält (som kallas arkiverat fält) för att lagra svar. I det här fallet sparas alla insamlade värden, även när en deltagare fyller i formuläret mer än en gång. Det här lagringsläget är endast tillgängligt i **undersökningar**. [Läs mer](../../surveys/using/managing-answers.md#storing-collected-answers).
1. **[!UICONTROL Edit a recipient]**: Med det här alternativet kan du markera ett fält i databasen. I det här fallet lagras användarnas svar i det här fältet. För varje deltagare behålls endast det senast sparade värdet och läggs till i profildata.
1. **[!UICONTROL Add a variable]**: Med det här alternativet kan du skapa en konfiguration så att information inte lagras i databasen. Lokala variabler kan deklareras uppströms. Du kan också lägga till dem direkt när du skapar fältet.
1. **[!UICONTROL Import an existing question]**: Med det här alternativet kan du importera befintliga frågor som har skapats i andra undersökningar.

   >[!NOTE]
   >
   >Lagringslägen och fältimporter beskrivs i [det här avsnittet](../../surveys/using/managing-answers.md#storing-collected-answers).

Typ av fält som ska läggas till (nedrullningsbar lista, textfält, kryssrutor osv.) anpassar sig till det valda lagringsläget. Du kan ändra den med hjälp av fältet **[!UICONTROL Type]** på fliken **[!UICONTROL General]**, men se till att den är konsekvent med datatypen.

![](assets/s_ncs_admin_survey_change_type.png)

De olika typerna av tillgängliga fält beskrivs i [det här avsnittet](../../web/using/about-web-forms.md).

## Undersökningsspecifika element {#survey-specific-elements}

Onlineundersökningar bygger på webbprogrammens funktioner. Undersökningsspecifika funktioner beskrivs nedan.

### Flera alternativ {#multiple-choice}

För **[!UICONTROL Multiple choice]**-typkontroller kan du definiera ett minsta och högsta antal markeringar. Med det här alternativet kan du t.ex. tvinga markeringen till minst **2**-värden och högst **4**-värden från de tillgängliga alternativen:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Om antalet markeringar är för stort eller för litet visas rätt meddelande.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>I det här fallet markeras alternativen med kryssrutor. När bara ett alternativ är möjligt används alternativknappar.

Motsvarande konfiguration är följande:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

Dessutom måste lagringsplatsen för det här inmatningsfältet vara av typen **[!UICONTROL Multiple values]** **arkiverat fält**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Den här funktionen är bara tillgänglig för **enkät**-typformulär.
>* Det här alternativet är inte kompatibelt med slumpmässig frågevisning. [Läs mer](#adding-questions).


### Lägg till frågor {#adding-questions}

Det finns två typer av behållare: standard och fråga. Standardbehållare används för att konfigurera sidlayout och villkorsstyrd visning på en sida. [Läs mer](../../web/using/about-web-forms.md).

Använd en **fråge**-behållare för att lägga till en fråga på sidan och för att infoga möjliga svar nedan i hierarkin. Användarsvar på frågor som placeras i den här typen av behållare kan analyseras i rapporter.

>[!CAUTION]
>
>Infoga aldrig en **Fråga**-behållare under en annan **Fråga**-behållare i hierarkin.

![](assets/s_ncs_admin_question_label.png)

Frågeetiketten anges i etikettfältet. I det här fallet används formatet från formulärets formatmall. Välj alternativet **[!UICONTROL Enter the title in HTML format]** för att anpassa det. Då får du tillgång till HTML-redigeraren.

>[!NOTE]
>
>Mer information om hur du använder HTML-redigeraren finns i [det här dokumentet](../../web/using/about-web-forms.md).

Exempel:

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

I exemplet ovan återges på följande sätt:

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Varje fråga har en **Query**-typbehållare.

Du kan aktivera slumpmässig anpassning av frågor via Adobe Campaign. Det går sedan att ange hur många frågor som ska visas på sidan i fältet längst ned i konfigurationsfönstret.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

Återgivningen ser ut så här:

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

När sidan uppdateras är de visade frågorna inte desamma.

>[!CAUTION]
>
>När du visar en fråga slumpmässigt (**[!UICONTROL Display randomly]** alternativ markerat på sidan) ska du se till att inte använda flervalsfrågor där en eller flera markeringar är obligatoriska.