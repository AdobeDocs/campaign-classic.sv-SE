---
product: campaign
title: Statiska element i ett webbformulär
description: Statiska element i ett webbformulär
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 1%

---

# Statiska element i ett webbformulär{#static-elements-in-a-web-form}



Du kan inkludera element som användaren inte har någon interaktion med på formulärets sidor. Det här är statiska element som bilder, HTML, ett vågrätt fält eller en hypertextlänk. Dessa element skapas med den första knappen i verktygsfältet genom att du väljer **[!UICONTROL Static elements]**.

![](assets/s_ncs_admin_survey_add_static_element.png)

Följande fälttyper är tillgängliga:

* Värdet baseras på tidigare svar (i formulärsammanhang) eller på databasen.
* Hypertextlänk, HTML, vågrätt fält. Se [Infoga HTML-innehåll](#inserting-html-content).
* Bild sparad i resursbiblioteket eller på en server som är tillgänglig för användare. Se [Infoga bilder](#inserting-images).
* Skript som körs på klientsidan och/eller serversidan. Den måste vara skriven i JavaScript och kompatibel med de flesta webbläsare för att säkerställa korrekt körning på klientsidan.

  >[!NOTE]
  >
  >På serversidan kan skriptet använda funktionerna som definierats i [Kampanj-JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv).

## Infoga HTML-innehåll {#inserting-html-content}

Du kan inkludera HTML-innehåll på en formulärsida: hypertextlänkar, bilder, formaterade stycken, videor osv.

I HTML-redigeraren kan du ange det innehåll som ska infogas på formulärsidan. Klicka på för att öppna redigeraren **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** .

Du kan ange och formatera innehållet direkt eller visa källkodsfönstret för att klistra in externt innehåll. Om du vill växla till källkodsläge klickar du på den första ikonen i verktygsfältet:

![](assets/s_ncs_admin_survey_html_editor.png)

Om du vill infoga ett databasfält använder du personaliseringsknappen.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>Strängarna som anges i HTML-redigeraren översätts bara om de definieras i **[!UICONTROL Texts]** underflik. Annars samlas de inte in. Mer information finns i [Översätta ett webbformulär](translating-a-web-form.md).

### Infoga en länk {#inserting-a-link}

Fyll i fälten i redigeringsfönstret så som visas i följande exempel:

Om du vill lägga till en hypertextlänk går du till **[!UICONTROL Static elements]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* The **[!UICONTROL Label]** är innehållet i hypertextlänken så som den kommer att visas på formulärsidan.
* The **[!UICONTROL URL]** är den önskade adressen, t.ex.: [https://www.adobe.com](https://www.adobe.com) för en webbplats, eller [info@adobe.com](mailto:info@adobe.com) för att skicka ett meddelande.
* The **[!UICONTROL Window]** I kan du välja visningsläge för länken när det gäller en plats. Du kan välja att öppna länken i ett nytt fönster, det aktuella fönstret eller i ett annat fönster.
* Du kan lägga till en knappbeskrivning enligt nedan:

  ![](assets/s_ncs_admin_survey_send_an_email.png)

* Du kan välja att visa länken som en knapp eller som en bild. Det gör du genom att välja typ av visning i dialogrutan **[!UICONTROL Type]** fält.

### Typ av länkar {#types-of-links}

Länkarna är som standard kopplade till en åtgärd av URL-typ, så att en länkmåladress kan anges i URL-fältet.

![](assets/s_ncs_admin_survey_link_url.png)

Du kan definiera andra åtgärder för länken så att användaren kan klicka på länken och göra följande:

* Uppdatera sidan

  Om du vill göra det väljer du **[!UICONTROL Refresh page]** i listrutan i **[!UICONTROL Action]** fält.

  ![](assets/s_ncs_admin_survey_link_refresh.png)

* Visa nästa/föregående sida

  Om du vill göra det väljer du **[!UICONTROL Next page]** eller **[!UICONTROL Previous page]** i listrutan i **[!UICONTROL Action]** fält.

  ![](assets/s_ncs_admin_survey_link_next.png)

  Du kan dölja **[!UICONTROL Next]** och/eller **[!UICONTROL Back]** om de ska ersättas av en länk. Se detta [page](defining-web-forms-page-sequencing.md).

  Länken ersätter **[!UICONTROL Next]** som används som standard.

  ![](assets/s_ncs_admin_survey_link_next_ex.png)

* Visa en annan sida

  The **[!UICONTROL Enable a transition]** gör att du kan visa en viss sida som är kopplad till den utgående övergången som är vald i **[!UICONTROL Transition]** fält.

  ![](assets/s_ncs_admin_survey_link_viral.png)

  Som standard har en sida bara en utdataövergång. Om du vill skapa nya övergångar markerar du sidan och klickar sedan på knappen **[!UICONTROL Add]** knappen i **[!UICONTROL Output transitions]** enligt nedan:

  ![](assets/s_ncs_admin_survey_add_transition.png)

  I diagrammet ser det här tillägget ut så här:

  ![](assets/s_ncs_admin_survey_add_transition_graph.png)

  >[!NOTE]
  >
  >Mer information om sidordningsföljd i ett webbformulär finns i [Definiera sidsekvenser för webbformulär](defining-web-forms-page-sequencing.md).

### Anpassa HTML-innehåll {#personalizing-html-content}

Du kan anpassa HTML-innehållet på en formulärsida med data som registrerats på en tidigare sida. Du kan t.ex. skapa ett webbformulär för bilförsäkring vars första sida gör att du kan ange kontaktinformation och bilens varumärke.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

Använd anpassningsfält för att mata in användarnamnet och det valda varumärket på nytt på nästa sida. Vilken syntax som ska användas beror på informationslagringsläget. Mer information finns i [Använda insamlade uppgifter](web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>Av säkerhetsskäl anges värdet i **`<%=`** formeln ersätts med escape-tecken.

I det här exemplet lagras mottagarens för- och efternamn i ett databasfält, medan deras bilmärke lagras i en variabel. Meddelandet som personaliserats på sidan 2 ska ha följande syntax:

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

Detta ger följande resultat:

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### Använda textvariabler {#using-text-variables}

The **[!UICONTROL Text]** Med -fliken kan du skapa variabelfält som kan användas i HTML mellan &lt;%= och %>-tecken med följande syntax: **$(IDENTIFIER)**.

Använd den här metoden om du enkelt vill att strängarna ska vara lokaliserade. Se [Översätta ett webbformulär](translating-a-web-form.md)

Du kan till exempel skapa en **Kontakt** fält som gör att du kan visa strängen &quot;Datum för senaste kontakt:&quot; för HTML-innehållet. Gör så här:

1. Klicka på **[!UICONTROL Text]** -fliken i HTML.
1. Klicka på **[!UICONTROL Add]** -ikon.
1. I **[!UICONTROL Identifier]** kolumn anger du namnet på variabeln
1. I **[!UICONTROL Text]** -kolumnen anger du standardvärdet.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. I HTML infogar du den här textvariabeln via **&lt;%= $(Kontakt) %>** syntax.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >Om du anger dessa tecken i HTML-redigeraren visas **&lt;** och **>** fälten ersätts med deras escape-tecken. I det här fallet måste du korrigera källkoden genom att klicka på **[!UICONTROL Display source code]** ikon för textredigeraren i HTML.

1. Öppna **[!UICONTROL Preview]** formulärets etikett för att visa det värde som anges i HTML:

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

I det här läget kan du bara definiera texten i webbformulär en gång och hantera översättningar med det integrerade översättningsverktyget. Mer information finns i [Översätta ett webbformulär](translating-a-web-form.md).

## Infoga bilder {#inserting-images}

För att bilder ska kunna inkluderas i formulär måste de sparas på en server som är tillgänglig utifrån.

Välj **[!UICONTROL Static elements]** > **[!UICONTROL Image]** -menyn.

Välj källan för bilden som ska infogas: den kan komma från det offentliga resursbiblioteket eller lagras på en extern server som är tillgänglig utifrån.

![](assets/s_ncs_admin_survey_add_img.png)

Om det här är en bild från biblioteket markerar du den i kombinationsrutan för fältet. Om den finns i en extern fil anger du åtkomstsökvägen. Etiketten visas genom att pekaren förs över bilden (sammanfaller med ett ALT-fält i HTML) eller när bilden inte visas.

Bilden kan visas i redigerarens centrala del.
