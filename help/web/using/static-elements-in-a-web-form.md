---
product: campaign
title: Statiska element i ett webbformulär
description: Statiska element i ett webbformulär
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 3%

---

# Statiska element i ett webbformulär{#static-elements-in-a-web-form}

![](../../assets/common.svg)

Du kan inkludera element som användaren inte har någon interaktion med på formulärets sidor; det är statiska element som bilder, HTML-innehåll, ett vågrätt fält eller en hypertextlänk. Dessa element skapas med den första knappen i verktygsfältet genom att välja **[!UICONTROL Static elements]**.

![](assets/s_ncs_admin_survey_add_static_element.png)

Följande fälttyper är tillgängliga:

* Värdet baseras på tidigare svar (i formulärsammanhang) eller på databasen.
* Hypertextlänk, HTML, vågrätt fält. Se [Infoga HTML-innehåll](#inserting-html-content).
* Bild sparad i resursbiblioteket eller på en server som är tillgänglig för användare. Se [Infoga bilder](#inserting-images).
* Skript som körs på klientsidan och/eller serversidan. Den måste vara skriven i JavaScript och kompatibel med de flesta webbläsare för att säkerställa korrekt körning på klientsidan.

   >[!NOTE]
   >
   >På serversidan kan skriptet använda de funktioner som definieras i [Kampanj-JSAPI-dokumentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

## Infoga HTML-innehåll {#inserting-html-content}

Du kan inkludera HTML-innehåll på en formulärsida: hypertextlänkar, bilder, formaterade stycken, videoklipp med mera.

Med HTML-redigeraren kan du ange det innehåll som ska infogas på formulärsidan. Om du vill öppna redigeraren klickar du på **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** .

Du kan ange och formatera innehållet direkt eller visa källkodsfönstret för att klistra in externt innehåll. Om du vill växla till källkodsläge klickar du på den första ikonen i verktygsfältet:

![](assets/s_ncs_admin_survey_html_editor.png)

Om du vill infoga ett databasfält använder du personaliseringsknappen.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>Strängarna som anges i HTML-redigeraren översätts bara om de definieras i underfliken **[!UICONTROL Texts]**. Annars samlas de inte in. Mer information finns i [Översätta ett webbformulär](translating-a-web-form.md).

### Infoga en länk {#inserting-a-link}

Fyll i fälten i redigeringsfönstret enligt följande exempel:

Om du vill lägga till en hypertextlänk går du till **[!UICONTROL Static elements]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* **[!UICONTROL Label]** är innehållet i hypertextlänken så som den kommer att visas på formulärsidan.
* **[!UICONTROL URL]** är den önskade adressen, t.ex.: [https://www.adobe.com](https://www.adobe.com) för en webbplats eller [info@adobe.com](mailto:info@adobe.com) för att skicka ett meddelande.
* I fältet **[!UICONTROL Window]** kan du välja visningsläge för länken om det gäller en plats. Du kan välja att öppna länken i ett nytt fönster, det aktuella fönstret eller i ett annat fönster.
* Du kan lägga till en knappbeskrivning enligt nedan:

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* Du kan välja att visa länken som en knapp eller som en bild. Det gör du genom att välja typ av visning i fältet **[!UICONTROL Type]**.

### Typ av länkar {#types-of-links}

Som standard är länkarna kopplade till en åtgärd av URL-typ, så att en länkmåladress kan anges i URL-fältet.

![](assets/s_ncs_admin_survey_link_url.png)

Du kan definiera andra åtgärder för länken så att användaren kan klicka på länken och göra följande:

* Uppdatera sidan

   Det gör du genom att välja alternativet **[!UICONTROL Refresh page]** i listrutan för fältet **[!UICONTROL Action]**.

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* Visa nästa/föregående sida

   Det gör du genom att välja **[!UICONTROL Next page]** eller **[!UICONTROL Previous page]** i listrutan för fältet **[!UICONTROL Action]**.

   ![](assets/s_ncs_admin_survey_link_next.png)

   Du kan dölja knapparna **[!UICONTROL Next]** och/eller **[!UICONTROL Back]** om de ska ersättas av en länk. Se den här [sidan](defining-web-forms-page-sequencing.md).

   Länken ersätter den **[!UICONTROL Next]**-knapp som används som standard.

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* Visa en annan sida

   Med alternativet **[!UICONTROL Enable a transition]** kan du visa en specifik sida som är associerad med den utgående övergång som är markerad i fältet **[!UICONTROL Transition]**.

   ![](assets/s_ncs_admin_survey_link_viral.png)

   Som standard har en sida bara en utdataövergång. Om du vill skapa nya övergångar markerar du sidan och klickar sedan på knappen **[!UICONTROL Add]** i **[!UICONTROL Output transitions]**-avsnittet enligt nedan:

   ![](assets/s_ncs_admin_survey_add_transition.png)

   I diagrammet ser det här tillägget ut så här:

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >Mer information om sidordningsföljd i ett webbformulär finns i [Definiera sidsekvenser för webbformulär](defining-web-forms-page-sequencing.md).

### Anpassa HTML-innehåll {#personalizing-html-content}

Du kan anpassa HTML-innehållet på en formulärsida med data som registrerats på en tidigare sida. Du kan t.ex. skapa ett webbformulär för bilförsäkring vars första sida gör att du kan ange kontaktinformation och bilens varumärke.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

Använd anpassningsfält för att mata in användarnamnet och det valda varumärket på nytt på nästa sida. Vilken syntax som ska användas beror på informationslagringsläget. Mer information finns i [Använda insamlad information](web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>Av säkerhetsskäl ersätts det värde som anges i formeln **`<%=`** med escape-tecken.

I det här exemplet lagras mottagarens för- och efternamn i ett databasfält, medan deras bilmärke lagras i en variabel. Meddelandet som personaliserats på sidan 2 ska ha följande syntax:

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

Detta ger följande resultat:

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### Använda textvariabler {#using-text-variables}

På fliken **[!UICONTROL Text]** kan du skapa variabelfält som kan användas i HTML mellan &lt;%=- och %>-tecken med följande syntax: **$(IDENTIFIER)**.

Använd den här metoden om du enkelt vill att strängarna ska vara lokaliserade. Se [Översätta ett webbformulär](translating-a-web-form.md)

Du kan till exempel skapa ett **kontaktfält** som gör att du kan visa strängen &quot;Datum för senaste kontakt:&quot; för HTML-innehållet. Följ stegen nedan för att göra detta:

1. Klicka på fliken **[!UICONTROL Text]** i HTML-texten.
1. Klicka på ikonen **[!UICONTROL Add]**.
1. I kolumnen **[!UICONTROL Identifier]** anger du namnet på variabeln
1. Ange standardvärdet i kolumnen **[!UICONTROL Text]**.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. Infoga den här textvariabeln via syntaxen **&lt;%= $(Contact) %>** i HTML-innehållet.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >Om du anger dessa tecken i HTML-redigeraren ersätts fälten **&lt;** och **>** med deras escape-tecken. I det här fallet måste du korrigera källkoden genom att klicka på ikonen **[!UICONTROL Display source code]** i HTML-textredigeraren.

1. Öppna etiketten **[!UICONTROL Preview]** för formuläret för att visa det värde som anges i HTML:

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

I det här läget kan du bara definiera texten i webbformulär en gång och hantera översättningar med det integrerade översättningsverktyget. Mer information finns i [Översätta ett webbformulär](translating-a-web-form.md).

## Infoga bilder {#inserting-images}

För att bilder ska kunna inkluderas i formulär måste de sparas på en server som är tillgänglig utifrån.

Välj menyn **[!UICONTROL Static elements]** > **[!UICONTROL Image]**.

Välj bildkällan som ska infogas: den kan komma från det offentliga resursbiblioteket eller lagras på en extern server som är tillgänglig utifrån.

![](assets/s_ncs_admin_survey_add_img.png)

Om det här är en bild från biblioteket markerar du den i kombinationsrutan för fältet. Om den finns i en extern fil anger du sökvägen. Etiketten visas genom att pekaren förs över bilden (sammanfaller med ett ALT-fält i HTML) eller när bilden inte visas.

Bilden kan visas i redigerarens centrala del.
