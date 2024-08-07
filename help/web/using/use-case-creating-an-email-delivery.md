---
product: campaign
title: Använd fall - skapa e-postleverans
description: Använd fall - skapa e-postleverans
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# Användningsfall: skapa en e-postleverans{#use-case-creating-an-email-delivery}



I det här fallet får du lära dig hur du utformar en e-postleverans med Adobe Campaign Digital Content Editor (DCE).

Vårt sista mål är att skapa en leverans med en personlig mall som innehåller:

* En direkt adress till en mottagare (med för- och efternamn)
* Två typer av länkar till en extern URL
* En spegelsida
* En länk till ett webbprogram

>[!NOTE]
>
>Innan du börjar måste du ha konfigurerat minst en **HTML-mall** som värd för innehållet i framtida leveranser.
>
>Kontrollera att **[!UICONTROL Content editing mode]** (på fliken **[!UICONTROL Advanced]**) är inställt på **[!UICONTROL DCE]** i leveransen **[!UICONTROL Properties]**. Mer information om hur du optimerar redigeringsprogrammet finns i [Bästa tillvägagångssätt för innehållsredigering](content-editing-best-practices.md).

## Steg 1 - Skapa en leverans {#step-1---creating-a-delivery}

Om du vill skapa en ny leverans placerar du markören på fliken **Kampanjer** och klickar på **Leveranser**. Klicka sedan på knappen **Skapa** ovanför listan över befintliga leveranser. Mer information om hur du skapar leveranser finns på [den här sidan](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Steg 2 - Välja en mall {#step-2---selecting-a-template}

Välj en leveransmall och ge sedan leveransen ett namn. Det här namnet visas endast för användare av Adobe Campaign-konsolen och inte för dina mottagare, men den här rubriken visas i din lista över leveranser. Klicka på **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Steg 3 - Markera ett innehåll {#step-3---selecting-a-content}

Redigeraren för digitalt innehåll innehåller olika färdiga mallar med olika strukturer (kolumner, textområden osv.).

Markera den innehållsmall som du vill använda och klicka sedan på knappen **[!UICONTROL Start with the selected content]** för att visa mallen i den skapade leveransen.

![](assets/dce_select_model.png)

Du kan även importera HTML-innehåll som har skapats utanför Adobe Campaign genom att välja **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Du kan spara innehållet som en mall för framtida bruk. När du har skapat en personlig innehållsmall kan du förhandsgranska den i listan med mallar. Mer information finns i [Mallhantering](template-management.md).

>[!CAUTION]
>
>Om du använder **Adobe Campaign webbgränssnitt** måste du importera en ZIP-fil som innehåller HTML-innehåll och relaterade bilder.

## Steg 4 - Utforma meddelandet {#step-4---designing-the-message}

* Visa de första och andra namnen på mottagarna

  Om du vill infoga mottagarnas för- och efternamn i ett textfält i leveransen klickar du på det valda textfältet och placerar sedan markören där du vill att de ska visas. Klicka på den första ikonen i popup-verktygsfältet och klicka sedan på **[!UICONTROL Personalization block]**. Välj **[!UICONTROL Greetings]** och klicka sedan på **[!UICONTROL OK]**.

  ![](assets/dce_personalizationblock_greetings.png)

* Infoga en länk i en bild

  Om du vill dirigera leveransmottagare till en extern adress via en bild klickar du på den relevanta bilden för att visa popup-verktygsfältet, placerar markören på den första ikonen och klickar sedan på **[!UICONTROL Link to an external URL]**. Mer information finns i [Lägga till en länk](editing-content.md#adding-a-link).

  ![](assets/dce_externalpage.png)

  Ange URL-adressen för länken i fältet **URL** med följande format: **https://www.myURL.com** och bekräfta sedan.

  Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

* Infoga en länk i text

  Om du vill integrera en extern länk i texten i leveransen markerar du en del text eller ett textblock och klickar sedan på den första ikonen i popup-verktygsfältet. Klicka på **[!UICONTROL Link to an external URL]** och ange länkadressen i fältet **[!UICONTROL URL]**. Mer information finns i [Lägga till en länk](editing-content.md#adding-a-link).

  Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

  >[!CAUTION]
  >
  >Den text som anges i fältet **[!UICONTROL Label]** ersätter den ursprungliga texten.

* Lägga till en spegelsida

  Om du vill att mottagarna ska kunna se leveransinnehållet i en webbläsare kan du integrera en länk till en spegelsida i leveransen.

  Klicka i det textfält där du vill se länken publicerad. Klicka på den första ikonen i popup-verktygsfältet, välj **[!UICONTROL Personalization block]** och sedan **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Klicka på **[!UICONTROL Save]** för att bekräfta.

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >Anpassningsblockets etikett ersätter automatiskt den ursprungliga texten i leveransen.

* Integrera en länk till ett webbprogram

  Med Digital Content Editor kan du integrera länkar till webbprogram från Adobe Campaign-konsolen, till exempel en landningssida eller en formulärsida. Mer information finns i [Länka till ett webbprogram](editing-content.md#link-to-a-web-application).

  Markera ett textfält för länken till ett webbprogram och klicka sedan på den första ikonen. Välj **[!UICONTROL Link to a Web application]** och välj sedan önskat program genom att klicka på ikonen i slutet av fältet **Webbprogram**.

  ![](assets/dce_webapp.png)

  Bekräfta genom att klicka på **Spara**.

  >[!NOTE]
  >
  >I det här steget måste du spara minst ett webbprogram i förväg. Dessa finns på fliken **[!UICONTROL Campaigns > Web applications]** i konsolen.

## Steg 5 - Spara leveransen {#step-5---saving-the-delivery}

När innehållet har integrerats sparar du leveransen genom att klicka på **Spara**. Den visas nu i din lista över leveranser på fliken **[!UICONTROL Campaigns > Deliveries]**.
