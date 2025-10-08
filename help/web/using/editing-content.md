---
product: campaign
title: Redigera innehåll
description: Redigera innehåll
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: 9df46ed923831ffdfb28acddfbc371cecafb251c
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---

# Redigera innehåll{#editing-content}



## Definiera ett synlighetsvillkor {#defining-a-visibility-condition}

Du kan ange ett synlighetsvillkor för ett webbsideselement: det här elementet visas bara om villkoret uppfylls.

Om du vill lägga till ett synlighetsvillkor markerar du ett block och anger villkoret i fältet **[!UICONTROL Visibility condition]** med uttrycksredigeraren.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>Avancerad uttrycksredigering visas på [den här sidan](../../platform/using/about-queries-in-campaign.md).

![](assets/dce_popup_visibilitycondition.png)

De här villkoren använder XTK-uttryckssyntaxen (till exempel **ctx.receive.@email != &quot;&quot;** eller **ctx.receive.@status==&quot;0&quot;**). Som standard är alla fält synliga.

>[!NOTE]
>
>Det går inte att redigera icke-synliga dynamiska block, till exempel nedrullningsbara menyer.

## Lägga till en kant och bakgrund {#adding-a-border-and-background}

Du kan lägga till en **kant** i ett markerat block. Kanterna definieras med hjälp av tre alternativ: stil, storlek och färg.

![](assets/dce_popup_border.png)

Du kan också definiera en **bakgrundsfärg** genom att välja en färg i färgdiagrammet.

![](assets/dce_popup_background.png)

## Redigera formulär {#editing-forms}

### Ändra dataegenskaper för ett formulär {#changing-the-data-properties-for-a-form}

Du kan länka databasfält med indatazon, alternativknapp eller kryssrutetypblock.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>Standardfälten är de som finns i webbprogrammets lagringsschema.

Med indatazonen **fält** kan du välja ett databasfält som ska länkas till formulärfältet.

Som standard finns fälten i tabellen **nms:recipient**.

![](assets/dce_field_selection.png)

Med alternativet **Obligatoriskt fält** kan du bara godkänna sidan om användaren har fyllt i fältet. Om ett obligatoriskt fält inte fylls i visas ett felmeddelande.

För alternativknappar och kryssrutor krävs **ytterligare konfiguration**.

Om mallen som används inte innehåller ett värde som standard måste du slutföra den i redigeraren.

Så här gör du:

* Klicka på ikonen **[!UICONTROL Edit]**.

  ![](assets/dce_sidebar_options.png)

* Ange det specificerade listvärdet (definierat av det markerade fältet) i fältet **[!UICONTROL Value]**.

  ![](assets/dce_sidebar_completeoptionradio.png)

### Ändra formulärfält {#modifying-form-fields}

Formulärfält som alternativknappar, indatazoner, listrutor osv. kan ändras från verktygsfälten.

Det innebär att du kan:

* Ta bort blocket som innehåller formulärfälten med hjälp av ikonen **[!UICONTROL Delete]**.
* Duplicera det markerade fältet genom att skapa ett nytt block med ikonen **[!UICONTROL Duplicate]**.
* Redigera fönstret **[!UICONTROL Form data]** om du vill länka ett databasfält till formulärzonen med hjälp av ikonen **[!UICONTROL Edit]** .

  ![](assets/dce_toolbar_formblock_edition.png)

## Lägga till en åtgärd till en knapp {#adding-an-action-to-a-button}

När användaren klickar på en knapp kan du definiera en associerad åtgärd. Om du vill göra det väljer du den åtgärd som ska utföras i listrutan.

![](assets/dce_sidebar_button.png)

Följande åtgärder är tillgängliga:

* **[!UICONTROL Refresh]** : uppdaterar den aktuella sidan.
* **[!UICONTROL Next page]** : skapar en länk till nästa sida i webbprogrammet.
* **[!UICONTROL Previous page]** : skapar en länk till föregående sida i webbprogrammet.

>[!NOTE]
>
>Värdet **[!UICONTROL None]** gör att du inte kan aktivera knappen.

Du kan ändra den etikett som är länkad till knappen i motsvarande fält.

## Lägga till en länk {#adding-a-link}

Du kan infoga en länk i vilket sidelement som helst: bild, ord, ordgrupp, textblock osv.

Det gör du genom att markera elementet och sedan använda den första ikonen på snabbmenyn.

![](assets/dce_insertlink_icon.png)

Med den här ikonen kommer du åt alla tillgängliga typer av länkar.

![](assets/dce_insertlink_menu.png)

Anpassningsblock och fält kan bara infogas i textblock.

>[!NOTE]
>
>För varje typ av länk kan du konfigurera öppningsläget: välj målfönstret i listrutan **Mål**. Det här värdet motsvarar HTML-taggen **`<target>`**.
>
>Listan med tillgängliga **mål** är följande:
>
>* Annat (IFrame)
>* Övre fönster (_top)
>* Överordnat fönster (_parent)
>* Nytt fönster (_blank)
>* Aktuellt fönster (_self)
>* Standardwebbläsarbeteende
>

### Länka till en URL {#link-to-a-url}

Med alternativet **Länka till en extern URL** kan du öppna alla URL-adresser från källinnehållet.

![](assets/dce_toolbar_imgblock_externallink.png)

Ange länkadressen i fråga i fältet **URL**. URL-fältet ska anges som: **https://www.myURL.com**.

### Länka till ett webbprogram {#link-to-a-web-application}

Med alternativet **Länka till ett webbprogram** kan du komma åt ett Adobe Campaign-webbprogram.

![](assets/dce_toolbar_imgblock_appweb.png)

Välj webbprogrammet från motsvarande fält.

Listan med föreslagna webbprogram motsvarar de tillgängliga programmen i noden **[!UICONTROL Resources > Online > Web Applications]**.

### Länka till en åtgärd {#link-to-an-action}

Med alternativet **Länk som definierar en åtgärd** kan du konfigurera en åtgärd när du klickar på ett källelement.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>Tillgängliga åtgärder beskrivs i avsnittet [Lägga till en åtgärd för en knapp](#adding-an-action-to-a-button).

### Ta bort en länk {#delete-a-link}

När en länk har infogats innehåller verktygsfältet två nya ikoner: **Redigera länk** och **Bryt länken** som gör att du kan interagera med den skapade länken.

* Med **[!UICONTROL Edit link]** kan du visa ett fönster med alla länkens parametrar.
* Med **[!UICONTROL Break the link]** kan du ta bort länken och alla relaterade parametrar efter bekräftelse.

>[!NOTE]
>
>Om länken tas bort behålls innehållet fortfarande.

## Ändra teckensnittsattribut {#changing-font-attributes}

När du markerar ett textelement kan du ändra teckensnittsattribut (format, format).

![](assets/dce_toolbar_txt.png)

De tillgängliga alternativen är följande:

* **Förstora teckensnitt**: ökar den markerade textens storlek (lägg till `<span style="font size:">`)
* **Ikonen** Minska teckensnitt: minskar den markerade textens storlek (lägg till `<span style="font size:">`)
* **Fet**-ikon: gör markerad text fet (radbryt text med taggen `<strong> </strong>`)
* **Kursiv** ikon: gör markerad text kursiv (figursätt text med taggen `<em> </em>`)
* **Understruken**-ikon: gör markerad text understruken (figursätt text med taggen `<span style="text-decoration: underline;">` )
* **Justera vänster** -ikon: justerar text till vänster om det markerade blocket (add style=&quot;text-align: left;&quot;)
* **Centrera**-ikon: centrerar texten för det markerade blocket (lägg till style=&quot;text-align: center;&quot;)
* **Högerjustera**-ikon: justerar text till höger om det markerade blocket (add style=&quot;text-align: right;&quot;)
* **Ändra bakgrundsfärg** -ikon: gör att du kan ändra bakgrundsfärg för det markerade blocket (lägg till style=&quot;background-color: rgba(170, 86, 255, 0.87))
* **Ikon för att ändra textfärg**: gör att du kan ändra textfärgen i det markerade blocket eller bara i den markerade texten (`<span style="color: #CODE">`)

>[!NOTE]
>
>* Ikonen **Ta bort**: tar bort blocket och allt dess innehåll.
>
>* **Duplicera**-ikon: duplicerar blocket samt alla format som hör till blocket.

## Hantera bilder och animeringar {#managing-images-and-animations}

Med Digital Content Editor kan du arbeta med **alla typer av bilder** som är kompatibla med webbläsare.

>[!CAUTION]
>
>Du får inte anropa externa filer i en **script** -tagg på HTML-sidan. Dessa filer kommer inte att importeras till Adobe Campaign-servern.

### Lägga till/ta bort/duplicera en bild {#adding---deleting---duplicating-an-image}

Om du vill infoga en bild markerar du ett bildtypsblock och klickar på ikonen **Bild** .

![](assets/dce_insert_image.png)

Välj en bildfil som har sparats lokalt.

![](assets/dce_popup_imgupload.png)

Ikonen **Ta bort** tar bort taggen som innehåller bilden.

Ikonen **Duplicera** duplicerar taggen och dess innehåll.

>[!CAUTION]
>
>När du duplicerar en bild tas de identifierare som hör till den nya bilden bort.

### Redigera bildegenskaper {#editing-image-properties}

När du markerar ett block som innehåller en bild får du tillgång till följande egenskaper:

* Med **bildtext** kan du definiera bildtexten som är länkad till bilden (motsvarar HTML-attributet **alt**).
* Med **Dimensioner** kan du ange bildstorleken i pixlar.

  ![](assets/dce_popup_imgsize.png)

## Lägga till innehåll för personalisering {#adding-personalization-content}

### Infoga ett anpassningsfält {#inserting-a-personalization-field}

Med alternativet **Personalization-fält** för infogningsikonen kan du lägga till ett databasfält i innehållet, till exempel mottagarens namn. Det här alternativet är bara tillgängligt för textblock.

![](assets/dce_toolbar_textblock_persofield.png)

Som standard finns fälten från tabellen **[!UICONTROL Recipient]**. Om det behövs kan du redigera webbprogrammets egenskaper och välja en annan tabell.

Fältnamnet visas i redigeraren, markerat med gult. Den ersätts av målmottagarens profil när personaliseringen genereras (t.ex. när en landningssida förhandsgranskas).

Ett exempel visas i avsnittet [Infoga ett anpassningsfält](creating-a-landing-page.md#inserting-a-personalization-field).

### Infoga ett personaliseringsblock {#inserting-a-personalization-block}

Med alternativet **Personalization-block** kan du infoga dynamiska och personliga block i innehållet. Du kan till exempel lägga till en logotyp eller ett gratulationsmeddelande. Det är inte tillgängligt för textblock.

![](assets/dce_toolbar_textblock_persoblock.png)

När personaliseringsblocknamnet har infogats visas det i redigeraren, markerat med gult. Den anpassas automatiskt till mottagarprofilen när personalisering genereras.

Mer information om inbyggda anpassningsblock och hur du definierar anpassade anpassningsblock finns på [den här sidan](../../delivery/using/personalization-blocks.md).
