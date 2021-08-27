---
product: campaign
title: Gränssnitt för innehållsredigeraren
description: Gränssnitt för innehållsredigeraren
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---

# Gränssnitt för innehållsredigeraren{#content-editor-interface}

![](../../assets/common.svg)

## Redigeringsfönster {#editing-window}

DCE-redigeringsfönstret är indelat i tre olika avsnitt. De gör att du kan visa, ändra och kontrollera innehållets status.

![](assets/dce_decoupe_window_nb.png)

1. Avsnittet **top** är ett visningsområde för meddelanden till användaren. Dessa meddelanden anger status för webbprogrammet eller leveransen som skapas, liksom varningar och felmeddelanden för innehållet. Mer information finns i [HTML-innehållsstatus](content-editing-best-practices.md#html-content-statuses).
1. Avsnittet till **vänster** i fönstret är området där du redigerar innehåll. I det här området kan användaren interagera direkt med innehållet via popup-verktygsfältet: infoga en länk i en bild, ändra teckensnitt, ta bort ett fält osv. Mer information finns i [Redigera formulär](editing-content.md#editing-forms).
1. Avsnittet till **höger** i fönstret är kontrollpanelsområdet. I det här området grupperas de olika alternativen för redigeraren, särskilt de som gäller konfigurering av sidrubriken och allmänna alternativ för ett block: lägga till en kant, länka ett databasfält med en indatazon, få åtkomst till egenskaper för webbsidor, osv. Mer information finns i avsnitten [Globala alternativ](#global-options) och [Redigera innehåll](editing-content.md).

## Globala alternativ {#global-options}

I den övre högra delen av redigeraren kan du komma åt globala alternativ som gör att du kan styra det innehåll som skapas just nu.

![](assets/dce_global_options.png)

Den har fyra ikoner:

![](assets/dce_icons_sidebar.png)

* Med ikonen **Visa/dölj block** kan du visa blå bildrutor runt innehållsblocken (motsvarar HTML-taggen `<div>`).

* Med ikonen **Välj ett annat innehåll** kan användaren läsa in nytt innehåll från en mall (befintlig mall eller en mall som inte är installerad).

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >Det markerade innehållet ersätter det aktuella innehållet.

* Med ikonen **Spara som mall** kan du spara det aktuella innehållet som en mall. Du måste ange mallens etikett och interna namn. Mallar lagras i noden **[!UICONTROL Resources > Templates > Content templates]**.

   ![](assets/dce_popup_savetemplate.png)

   När mallen har sparats är den tillgänglig och kan markeras när du skapar nytt innehåll.

   ![](assets/dce_create_fromtemplate.png)

* Med ikonen **Sidegenskaper** kan du markera innehållsinformation högst upp på HTML-sidan.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >Den här informationen motsvarar HTML-taggarna **`<title>`** och **`<meta>`** på sidan.
   >
   >Nyckelorden måste avgränsas med kommatecken.

## Blockalternativ {#block-options}

Avsnittet till höger om redigeraren grupperar huvudalternativen som gör att du kan agera på innehållet. Om du vill visa dessa alternativ måste du markera ett block: vilken typ av alternativ det är beror på vilket block som är markerat.

![](assets/dce_right_section.png)

Du kan:

* Kontrollera visningen av ett eller flera block i [Definiera ett synlighetsvillkor](editing-content.md#defining-a-visibility-condition),
* Definiera kanter och ramar, se [Lägga till en kant och bakgrund](editing-content.md#adding-a-border-and-background),
* Definiera bildattribut (storlek, bildtext), se [Redigera bildegenskaper](editing-content.md#editing-image-properties),
* Länka databasen till ett formulärelement (indatazon, kryssruta), se [Ändra dataegenskaper för ett formulär](editing-content.md#changing-the-data-properties-for-a-form),
* Gör en del av ett formulär obligatorisk, se [Ändra dataegenskaperna för ett formulär](editing-content.md#changing-the-data-properties-for-a-form),
* Definiera en åtgärd för en knapp i [Lägga till en åtgärd för en knapp](editing-content.md#adding-an-action-to-a-button).

## Verktygsfältet Innehåll {#content-toolbar}

Verktygsfältet är ett **popup-element** i DCE-gränssnittet som visar olika funktioner beroende på det valda blocket.

>[!CAUTION]
>
>Du kan formatera HTML-innehållet med vissa verktygsfältsfunktioner. Om sidan innehåller en CSS-formatmall kan det emellertid visa sig att **instruktionerna** från formatmallen **prioriterar** framför instruktionerna som anges i verktygsfältet.
