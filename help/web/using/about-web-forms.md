---
product: campaign
title: Kom igång med webbformulär
description: Kom igång med webbformulär i Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Landing Pages, Web Forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 1%

---

# Kom igång med webbformulär{#about-web-forms}



Adobe Campaign integrerar en grafisk modul för att definiera och publicera webbformulär för att skapa sidor som innehåller inmatnings- och urvalsfält, och som kan innehålla data i databasen. På så sätt kan du utforma och publicera webbsidor som användare kan komma åt för att visa eller ange information.

I det här kapitlet beskrivs hur du skapar och hanterar webbformulär, hur du hanterar fält och sidor samt lagrings- och sparlägen.

>[!CAUTION]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

## Steg för att skapa ett webbformulär {#steps-for-creating-a-web-form}

I det här kapitlet beskrivs de steg som krävs för att utforma ett **webForm**-typformulär i Adobe Campaign samt tillgängliga alternativ och konfigurationer. Med Adobe Campaign kan du göra det här webbformuläret tillgängligt för användare samt samla in och arkivera svar i databasen.

>[!CAUTION]
>
>När du konfigurerar webbprogram och webbformulär behöver du en lodrät upplösning på minst 900 pixlar (t.ex. 1 600 × 900).

Webbformulär öppnas via menyn Webbprogram på fliken **Kampanjer** . I Adobe Campaign-trädet grupperas de under noden **[!UICONTROL Resources > Online > Web Applications]**.

Om du vill skapa ett webbformulär klickar du på knappen **[!UICONTROL Create]** ovanför listan med webbprogram.

![](assets/webapp_create_new.png)

Välj webbformulärmallen ( **[!UICONTROL newWebForm]** som standard).

![](assets/s_ncs_admin_survey_select_template.png)

Du kommer då till formulärets kontrollpanel.

![](assets/webapp_empty_dashboard.png)

På fliken **[!UICONTROL Edit]** kan du skapa ditt innehåll.

![](assets/webapp_edit_tab.png)

Så här definierar du konfigurationen och innehållet i webbformuläret:

* Börja med att skapa de sidor och kontroller som krävs: inmatningsfält, listrutor, HTML-innehåll osv.

  Det här steget beskrivs nedan.

* Definiera sidsekvenser och villkor för visningen.

  Det här steget beskrivs i [Definiera sidsekvenser för webbformulär](defining-web-forms-page-sequencing.md).

* Översätt innehållet om det behövs.

  Det här steget beskrivs närmare i [Översätta ett webbformulär](translating-a-web-form.md).

## Om webbformulär {#about-web-forms-designing}

Formulärets sidor skapas via en specifik redigerare där du kan definiera och konfigurera indatagränser (text), urvalsfält (listor, kryssrutor osv.) och statiska element (bilder, HTML-innehåll osv.). De kan grupperas i behållare och deras layout ändras efter dina behov (mer information finns i [Skapa behållare](defining-web-forms-layout.md#creating-containers)).

I följande avsnitt beskrivs hur du definierar innehåll och layout för formulärskärmar:

* [Lägga till fält i ett webbformulär](adding-fields-to-a-web-form.md),
* [Infogar innehåll i HTML](static-elements-in-a-web-form.md#inserting-html-content),
* [Statiska element i ett webbformulär](static-elements-in-a-web-form.md),
* [Definierar webbformulärlayout](defining-web-forms-layout.md).

>[!NOTE]
>
>* Under siddesignen kan du visa den slutliga återgivningen på fliken **[!UICONTROL Preview]**. Spara formuläret först om du vill se ändringarna. Eventuella fel visas på fliken **[!UICONTROL Log]**.
>* Aktivera felsökningsläget i webbformuläret för att säkerställa att sidvisning och informationslagring sker i rätt sekvens. Det gör du genom att gå till underfliken **[!UICONTROL Preview]** och markera kryssrutan **[!UICONTROL Enable debug mode]**: all insamlad information och eventuella körningsfel visas längst ned på varje sida.
>

### Använda ikonerna i verktygsfältet {#using-the-icons-in-the-toolbar}

Du kan också använda ikonerna i verktygsfältet eller högerklicka för att infoga en indatazon.

![](assets/s_ncs_admin_webform_add_selection.png)

I det här fallet börjar du med att välja vilken typ av fält som ska läggas till och svarslagringsläget.

![](assets/s_ncs_admin_webform_select_storage.png)

Klicka på **[!UICONTROL Ok]** för att godkänna markeringen.

![](assets/s_ncs_admin_webform_confirm_storage.png)
