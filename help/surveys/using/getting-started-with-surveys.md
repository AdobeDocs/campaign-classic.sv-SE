---
product: campaign
title: Viktiga steg för att skapa en undersökning
description: Skapa din första enkät med Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Surveys
exl-id: 22e14b24-59ba-4a92-8ffb-f5336793d64f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---

# Viktiga steg för att skapa en undersökning{#getting-started-with-surveys}



Här följer en kort översikt över de viktigaste stegen för att skapa en enkel enkät med hjälp av följande inbyggda mall:

![](assets/s_ncs_admin_survey_result.png)

De här stegen är:

1. [Steg 1 - Skapa en undersökning](#step-1---creating-a-survey),
1. [Steg 2 - Välj mallen](#step-2---selecting-the-template),
1. [Steg 3 - Bygg undersökningen](#step-3---building-the-survey),
1. [Steg 4 - Skapa sidinnehållet](#step-4---creating-the-page-content),
1. [Steg 5 - Lagra undersökningsdata](#step-5---storing-the-survey-data-),
1. [Steg 6 - Publish sidorna](#step-6---publishing-the-pages),
1. [Steg 7 - Dela din onlineundersökning](#step-7---sharing-your-online-survey).

## Steg 1 - Skapa en undersökning {#step-1---creating-a-survey}

Om du vill skapa en ny undersökning går du till fliken **[!UICONTROL Campaigns]** eller **[!UICONTROL Profiles and targets]** och klickar på menyn **[!UICONTROL Web Applications]**. Klicka på knappen **[!UICONTROL Create]** ovanför listan med formulär.

![](assets/s_ncs_admin_survey_create.png)

## Steg 2 - Välj en mall {#step-2---selecting-the-template}

Välj en undersökningsmall och ge sedan undersökningen ett namn. Det här namnet visas inte för slutanvändarna, men det gör att undersökningen kan identifieras i Adobe Campaign. Klicka på **[!UICONTROL Save]** om du vill lägga till enkäten i listan över webbprogram.

![](assets/s_ncs_admin_survey_wz_00.png)

## Steg 3 - Skapa enkäten {#step-3---building-the-survey}

Undersökningar byggs i ett diagram där följande element är placerade: den eller de sidor där innehållet ska skapas, stegen för att förhandsladda och spara data samt testfaserna. Skript och frågor kan också infogas.

Om du vill skapa diagrammet klickar du på formuläret **[!UICONTROL Edit]** i enkäten.

En undersökning måste innehålla **minst** av följande tre komponenter: en sida, en lagringsruta och en slutsida.

* Om du vill skapa en sida markerar du objektet **[!UICONTROL Page]** i den vänstra delen av redigeraren och placerar det i den mellersta delen enligt nedan:

  ![](assets/s_ncs_admin_survey_new_page.png)

* Sedan markerar du objektet **[!UICONTROL Storage]** och placerar det på sidans utdataövergång.
* Markera slutligen objektet **[!UICONTROL End]** och placera det i slutet av lagringsrutans utdataövergång för att få följande diagram:

  ![](assets/s_ncs_admin_survey_end.png)

## Steg 4 - Skapa sidinnehållet {#step-4---creating-the-page-content}

I följande exempel använder vi en **[!UICONTROL Page (v5 compatibility)]**-typsida. Den här sidtypen nås via den avancerade menyn på fliken **[!UICONTROL Edit]**.

![](assets/s_ncs_admin_survey_pagev5.png)

* **Lägg till inmatningsfält**

  Om du vill skapa sidans innehåll måste du redigera det: om du vill göra det dubbelklickar du på objektet **[!UICONTROL Page]**. Klicka på den första ikonen i verktygsfältet för att öppna den här assistenten. Välj **[!UICONTROL Edit a recipient]** om du vill skapa ett inmatningsfält för användarnamnet som ska lagras i det matchande fältet i mottagarens profil.

  ![](assets/s_ncs_admin_survey_add_field_menu.png)

  Klicka på knappen **[!UICONTROL Next]** för att välja fältet för datalagring i databasen. I det här fallet fältet &#39;Efternamn&#39;.

  ![](assets/s_ncs_admin_survey_choose_field.png)

  Klicka på **[!UICONTROL Finish]** för att bekräfta att fält har skapats.

  När informationen lagras i ett fält som redan finns i databasen får fältet som standard det markerade fältets namn, dvs. &quot;Efternamn&quot; i det här exemplet. Du kan ändra den här etiketten enligt nedan:

  ![](assets/s_ncs_admin_survey_change_label.png)

  Skapa nu ett inmatningsfält för användarkontonumret. Upprepa åtgärden och välj Kontonr fält.

  Använd samma procedur för att lägga till ett fält där användaren kan ange en e-postadress.

* **Skapa en fråga**

  Om du vill skapa en fråga högerklickar du på det sista elementet i trädet och väljer **[!UICONTROL Containers > Question]** eller klickar på ikonen **[!UICONTROL Containers]** och väljer **[!UICONTROL Question]**.

  ![](assets/s_ncs_admin_survey_add_qu.png)

  Ange etiketten för frågan och infoga svarsfälten som en underavdelning till frågan. För att göra detta måste den nod som är länkad till frågan vara markerad när du skapar svarsfältet. Lägg till en **[!UICONTROL drop-down listx]** med ikonen **[!UICONTROL Selection controls]** eller genom att högerklicka, som visas nedan:

  ![](assets/s_ncs_admin_survey_add_list.png)

  Välj ett lagringsutrymme: välj ett uppräkningsfält om du vill hämta värdena automatiskt (i det här fallet e-postformatet).

  ![](assets/s_ncs_admin_survey_add_itz_list.png)

  Klicka på länken **[!UICONTROL Initialize the list of values from the database]** på fliken **[!UICONTROL General]**: värdetabellen anges automatiskt.

  ![](assets/s_ncs_admin_survey_add_value.png)

  Klicka på **[!UICONTROL OK]** för att stänga redigeraren och på **[!UICONTROL Save]** för att spara ändringarna.

  >[!NOTE]
  >
  >För varje fält eller fråga kan du anpassa sidlayouten efter dina behov, tack vare alternativen på fliken **[!UICONTROL Advanced]**. Layouten för undersökningsskärmar beskrivs i [det här avsnittet](../../web/using/about-web-forms.md).

  Klicka på fliken **[!UICONTROL Preview]** på detaljskärmen för att visa återgivningen av den undersökning du just har skapat.

  ![](assets/s_ncs_admin_survey_preview.png)

## Steg 5 - Lagra undersökningsdata {#step-5---storing-the-survey-data-}

I lagringsrutan kan du spara användarsvaren i databasen. Du måste välja en avstämningsnyckel för att identifiera de profiler som redan finns i databasen.

Om du vill göra det redigerar du rutan och väljer det fält som ska användas som avstämningsnyckel när data lagras.

I exemplet nedan uppdateras profilen när du sparar (bekräftar) och en profil sparas i databasen med samma kontonummer som den som anges i formuläret. Om profilen inte finns skapas den.

![](assets/s_ncs_admin_survey_save_edit.png)

Klicka på **[!UICONTROL OK]** för att bekräfta och klicka sedan på **[!UICONTROL Save]** för att spara undersökningen

## Steg 6 - Publish sidorna {#step-6---publishing-the-pages}

För att användare ska kunna komma åt HTML-sidorna måste programmet vara tillgängligt. Den får inte längre vara i redigeringsskedet, utan i produktion. Om du vill publicera en undersökning måste du publicera den. Så här gör du:

* Klicka på knappen **[!UICONTROL Publish]** ovanför kontrollpanelen för enkäten.
* Klicka på **[!UICONTROL Start]** för att starta publikationen och stänga assistenten.

  ![](assets/s_ncs_admin_survey_start_publ.png)

  Status för undersökningen ändras till: **Online**.

  ![](assets/survey_published.png)

## Steg 7 - Dela din nätundersökning {#step-7---sharing-your-online-survey}

När enkäten är i produktion är den tillgänglig på servern och du kan leverera den. URL:en för att komma åt undersökningen visas på kontrollpanelen.

![](assets/survey_url_from_dashboard.png)

Om du vill leverera enkäten kan du skicka ett meddelande som innehåller en åtkomstlänk till målpopulationen eller placera URL:en för enkäten på en webbsida, till exempel.

Du kan sedan övervaka användarsvar via rapporter och loggar. Se [Svarsspårning](../../surveys/using/publish-track-and-use-collected-data.md#response-tracking).

>[!CAUTION]
>
>Den offentliga URL:en innehåller undersökningens interna namn. När det interna namnet ändras uppdateras URL:en automatiskt: alla länkar till undersökningen måste också uppdateras.
>
>Om leveranser som innehåller länken till formuläret redan har skickats, kommer länken inte längre att fungera.
