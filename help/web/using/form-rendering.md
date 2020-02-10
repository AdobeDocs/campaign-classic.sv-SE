---
title: Formuläråtergivning
seo-title: Formuläråtergivning
description: Formuläråtergivning
seo-description: null
page-status-flag: never-activated
uuid: 714ce201-5535-4fde-b388-1605ac54edcb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 669635bd-868b-4550-b075-6294ccb71297
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Formuläråtergivning{#form-rendering}

## Välja formuläråtergivningsmall {#selecting-the-form-rendering-template}

Med formulärinställningarna kan du välja den mall som ska användas för att generera sidorna. Du öppnar dem genom att klicka på **[!UICONTROL Settings]** knappen i verktygsfältet för formulärdetaljer och sedan välja **[!UICONTROL Rendering]** fliken. Som standard finns det ett antal mallar (formatmallar).

![](assets/s_ncs_admin_survey_rendering_select.png)

I det nedre avsnittet av redigeraren kan du visa en återgivning av den valda mallen.

Med zoomfunktionen kan du redigera den valda mallen.

![](assets/s_ncs_admin_survey_render_edit.png)

Du kan ändra eller åsidosätta de här mallarna. Om du vill göra det klickar du på **[!UICONTROL Page layout...]** länken och anpassar informationen.

![](assets/s_ncs_admin_survey_render_edit_param.png)

Du kan:

* Ändra bilden som används som logotyp och anpassa dess storlek,
* Ange också sökvägen för åtkomst till förhandsvisningsbilden när användarna väljer den här återgivningsmallen.

På fliken **[!UICONTROL Headers/Footers]** kan du ändra den information som visas i sidhuvuden och sidfötter på varje formulärsida med hjälp av den här mallen.

![](assets/s_ncs_admin_survey_render_edit_header.png)

Varje rad i avsnittet **[!UICONTROL Page headers]** och **[!UICONTROL Page footers]** motsvarar en rad på HTML-sidan. Klicka **[!UICONTROL Add]** för att skapa en ny rad.

Markera en befintlig rad och klicka på **[!UICONTROL Detail]** knappen för att anpassa den.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

Du kan ändra innehållet på raden, lägga till kanter och ändra teckensnittsattributen via de relevanta flikarna. Klicka **[!UICONTROL OK]** för att bekräfta ändringarna.

I **[!UICONTROL Position]** fälten kan du definiera placeringen av element i sidhuvudet och sidfoten.

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>Återgivningsmallar lagras i **[!UICONTROL Administration > Configuration > Form rendering]** noden.\
>Mer information finns i [Anpassa formuläråtergivning](#customizing-form-rendering)

## Anpassa formuläråtergivning {#customizing-form-rendering}

### Ändra layout för element {#changing-the-layout-of-elements}

Du kan överlagra formatmallen för varje element i formuläret (inmatningsfält, bilder, alternativknappar etc.).

Använd fliken **[!UICONTROL Advanced]** om du vill göra det.

![](assets/s_ncs_admin_survey_advanced_tab.png)

Här kan du definiera följande egenskaper:

* **[!UICONTROL Label position]**: Se [Definiera placeringen av etiketter](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).
* **[!UICONTROL Label format]**: Radbyte eller Ingen radbrytning,
* **[!UICONTROL Number of cells]** : se [Placera fälten på sidan](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** (Vänster, Höger, Centrerad) och **[!UICONTROL Vertical alignment]** (Hög, Låg, Mitten),
* **[!UICONTROL Width]** för zonen: detta kan uttryckas i procent eller i måttenheter, punkter eller pixlar (standardvärde),
* Maximalt **[!UICONTROL Length]**: Högsta antal tillåtna tecken (för typografierna Text, Number och Password),
* **[!UICONTROL Lines]**: antal rader för en **[!UICONTROL Multi-line text]** typzon,
* **[!UICONTROL Style inline]**: I kan du överlagra CSS-formatmallen med ytterligare inställningar. **Dessa separeras med**; tecken enligt exemplet nedan:

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### Definiera sidhuvuden och sidfötter {#defining-headers-and-footers}

Fält ordnas i en trädstruktur vars rot har samma namn som sidan. Markera den om du vill ändra namnet.

Fönstrets namn måste anges på fliken **[!UICONTROL Page]** i fönstret för formuläregenskaper. Du kan också lägga till ett visst innehåll i sidhuvudet och sidfoten (den här informationen visas på alla sidor). Det här innehållet anges i de matchande avsnitten på **[!UICONTROL Texts]** fliken enligt nedan:

![](assets/s_ncs_admin_survey_titles_config.png)

### Lägga till element i HTML-rubriken {#adding-elements-to-html-header}

Du kan ange ytterligare element som ska infogas i HTML-huvudet på en formulärsida. Om du vill göra det anger du elementen på fliken **[!UICONTROL Header]** på den aktuella sidan.

Då kan du t.ex. referera till en ikon som visas i sidans namnlist.

![](assets/webform_header_page_tab.png)

## Definiera kontrollinställningar {#defining-control-settings}

När användaren fyller i formuläret utförs automatiskt en kontroll av vissa fält beroende på format eller konfiguration. Detta gör att du kan göra vissa fält obligatoriska (se [Definiera obligatoriska fält](#defining-mandatory-fields)) eller kontrollera formatet för de data som anges (se [Kontrollera dataformat](#checking-data-format)). Kontroller utförs under sidgodkännande (genom att klicka på en länk eller knapp som aktiverar en utdataövergång).

### Definiera obligatoriska fält {#defining-mandatory-fields}

Om du vill göra vissa fält obligatoriska väljer du det här alternativet när du skapar fältet.

![](assets/s_ncs_admin_survey_required_field.png)

Om användaren godkänner den här sidan utan att ha skrivit in fältet visas följande meddelande:

![](assets/s_ncs_admin_survey_required_default_msg.png)

Du kan anpassa det här meddelandet genom att klicka på **[!UICONTROL Personalize this message]** länken.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

Om användaren godkänner den här sidan utan att ha skrivit in fältet visas följande meddelande:

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### Kontrollerar dataformat {#checking-data-format}

För formulärkontroller vars värden lagras i ett befintligt fält i databasen, gäller reglerna för lagringsfältet.

För formulärkontroller vars värden lagras i en variabel, beror godkännandereglerna på variabelns format.

Om du till exempel skapar en **[!UICONTROL Number]** kontroll för att lagra klientnumret, som visas nedan:

![](assets/s_ncs_admin_survey_choose_format.png)

Användaren måste ange ett heltal i formulärfältet.

## Definiera villkorlig visning av fält {#defining-fields-conditional-display}

Du kan konfigurera visningen av fält på sidan som ska visas baserat på de värden som användaren väljer. Detta kan gälla ett fält eller en grupp av fält (när de grupperas i en behållare).

För varje element på sidan kan du definiera visningsvillkoren i avsnittet **[!UICONTROL Visibility]** .

![](assets/s_ncs_admin_survey_condition_edit.png)

Villkoren kan gälla värdet för databasfält eller variabler.

I fältvalsfönstret kan du välja bland följande data:

![](assets/s_ncs_admin_survey_condition_select.png)

* Huvudträdet innehåller parametrarna för formulärkontexten. Standardparametrarna är identifieraren (som matchar mottagarens krypterade identifierare), språk och ursprung.

   Mer information finns på den här [sidan](../../web/using/defining-web-forms-properties.md#form-url-parameters).

* Underträdet innehåller de inmatningsfält som är infogade i formuläret och lagrade i databasen. **[!UICONTROL Recipients]**

   Mer information finns i [Lagra data i databasen](../../web/using/web-forms-answers.md#storing-data-in-the-database).

* Underträdet innehåller de tillgängliga variablerna för det här formuläret **[!UICONTROL Variables]** . Mer information finns i [Lagra data i en lokal variabel](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable).

Mer information finns i användningsexemplet här: [Visa olika alternativ beroende på de valda värdena](../../web/using/use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values).

Du kan också ange villkor för hur formulärsidor ska visas med hjälp av **[!UICONTROL Test]** objektet. Mer information finns på den här [sidan](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

## Importera element från ett befintligt formulär {#importing-elements-from-an-existing-form}

Det går att importera fält eller behållare från andra webbformulär. På så sätt kan du skapa ett bibliotek med återanvändbara block som infogas i formulär, t.ex. adressblocket, prenumerationsområdet för nyhetsbrevet.

Så här importerar du ett element till ett formulär:

1. Redigera sidan som du vill infoga ett eller flera element i och klicka sedan på **[!UICONTROL Import an existing block]** i verktygsfältet.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. Markera det webbformulär som innehåller de fält som ska importeras och välj de behållare och fält som ska importeras.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >Med **[!UICONTROL Edit link]** ikonen till höger om källformulärnamnet kan du visa det valda webbformuläret.

1. Bekräfta infogningen genom **[!UICONTROL Ok]** att klicka.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)

