---
solution: Campaign Classic
product: campaign
title: Om webbformulär
description: Om webbformulär
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 5%

---


# Om webbformulär{#about-web-forms}

Adobe Campaign integrerar en grafisk modul för att definiera och publicera webbformulär för att skapa sidor som innehåller inmatnings- och urvalsfält, och som kan innehålla data i databasen. På så sätt kan du utforma och publicera webbsidor som användare kan komma åt för att visa eller ange information.

I det här kapitlet beskrivs hur du skapar och hanterar webbformulär, hur du hanterar fält och sidor samt lagrings- och sparlägen.

>[!CAUTION]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

## Steg för att skapa ett webbformulär {#steps-for-creating-a-web-form}

I det här kapitlet beskrivs de steg som krävs för att utforma ett **webForm** -formulär i Adobe Campaign samt tillgängliga alternativ och konfigurationer. Med Adobe Campaign kan du göra det här webbformuläret tillgängligt för användare samt samla in och arkivera svar i databasen.

>[!CAUTION]
>
>När du konfigurerar webbprogram och webbformulär behöver du en lodrät upplösning på minst 900 pixlar (t.ex.: 1600x900).

Webbformulär öppnas via menyn Webbprogram på fliken **Kampanjer** . I Adobe Campaign-trädet grupperas de under **[!UICONTROL Resources > Online > Web Applications]** -noden.

Om du vill skapa ett webbformulär klickar du på **[!UICONTROL Create]** knappen ovanför listan med webbprogram.

![](assets/webapp_create_new.png)

Välj webbformulärmallen ( **[!UICONTROL newWebForm]** som standard).

![](assets/s_ncs_admin_survey_select_template.png)

Du kommer då till formulärets kontrollpanel.

![](assets/webapp_empty_dashboard.png)

På fliken **[!UICONTROL Edit]** kan du skapa innehåll.

![](assets/webapp_edit_tab.png)

Så här definierar du konfigurationen och innehållet i webbformuläret:

* Börja med att skapa de sidor och kontroller som krävs: inmatningsfält, nedrullningsbara listor, HTML-innehåll osv.

   Det här steget beskrivs nedan.

* Definiera sidsekvenser och villkor för visningen.

   Det här steget beskrivs i [Definiera sidsekvenser](../../web/using/defining-web-forms-page-sequencing.md)för webbformulär.

* Översätt innehållet om det behövs.

   Det här steget beskrivs närmare i [Översätta ett webbformulär](../../web/using/translating-a-web-form.md).

## Om webbformulär {#about-web-forms-designing}

Formulärets sidor skapas via en specifik redigerare där du kan definiera och konfigurera indatagränser (text), urvalsfält (listor, kryssrutor osv.) och statiska element (bilder, HTML-innehåll osv.). De kan grupperas i behållare och deras layout ändras efter dina behov (mer information finns i [Skapa behållare](../../web/using/defining-web-forms-layout.md#creating-containers)).

I följande avsnitt beskrivs hur du definierar innehåll och layout för formulärskärmar:

* [Lägga till fält i ett webbformulär](../../web/using/adding-fields-to-a-web-form.md),
* [Infoga HTML-innehåll](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [Statiska element i ett webbformulär](../../web/using/static-elements-in-a-web-form.md),
* [Definiera ett webbformulärs layout](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* Under siddesignen kan du visa den slutliga återgivningen på **[!UICONTROL Preview]** fliken. Spara formuläret först om du vill se ändringarna. Eventuella fel visas på **[!UICONTROL Log]** fliken.
>* Aktivera felsökningsläget i webbformuläret för att säkerställa att sidvisning och informationslagring sker i rätt sekvens. Det gör du genom att gå till **[!UICONTROL Preview]** underfliken och markera **[!UICONTROL Enable debug mode]** rutan: all insamlad information och eventuella körningsfel visas längst ned på varje sida.

>



### Använda ikonerna i verktygsfältet {#using-the-icons-in-the-toolbar}

Du kan också använda ikonerna i verktygsfältet eller högerklicka för att infoga en indatazon.

![](assets/s_ncs_admin_webform_add_selection.png)

I det här fallet börjar du med att välja vilken typ av fält som ska läggas till och svarslagringsläget.

![](assets/s_ncs_admin_webform_select_storage.png)

Click **[!UICONTROL Ok]** to approve the selection.

![](assets/s_ncs_admin_webform_confirm_storage.png)

