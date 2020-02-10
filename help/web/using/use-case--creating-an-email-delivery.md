---
title: '"Användningsfall: skapa e-postleverans"'
seo-title: '"Användningsfall: skapa e-postleverans"'
description: '"Användningsfall: skapa e-postleverans"'
seo-description: null
page-status-flag: never-activated
uuid: 7cd6329c-63d5-4cf0-9451-f0b4c2eaf0dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 4ec34980-62a2-47b9-b103-de4290925624
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Användningsfall: skapa e-postleverans{#use-case-creating-an-email-delivery}

I det här fallet får du lära dig hur du utformar en e-postleverans med Adobe Campaign Digital Content Editor (DCE).

Vårt sista mål är att skapa en leverans med en personlig mall som innehåller:

* En direkt adress till en mottagare (med för- och efternamn)
* Två typer av länkar till en extern URL
* En spegelsida
* En länk till ett webbprogram

>[!NOTE]
>
>Innan du börjar måste du ha minst en **HTML-mall** konfigurerad som värd för innehållet i framtida leveranser.
>
>Kontrollera att **[!UICONTROL Properties]** (på **[!UICONTROL Content editing mode]** fliken) är inställt på **[!UICONTROL Advanced]** **[!UICONTROL DCE]** i leveransfönstret. Mer information om hur du optimerar redigeringsprogrammet finns i Bästa tillvägagångssätt för [innehållsredigering](../../web/using/content-editing-best-practices.md).

## Steg 1 - Skapa en leverans {#step-1---creating-a-delivery}

Om du vill skapa en ny leverans placerar du markören på fliken **Kampanjer** och klickar på **Leveranser**. Klicka sedan på knappen **Skapa** ovanför listan över befintliga leveranser. Mer information om hur du skapar leveranser finns på [den här sidan](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Steg 2 - Välja en mall {#step-2---selecting-a-template}

Välj en leveransmall och ge sedan leveransen ett namn. Det här namnet visas endast för användare av Adobe Campaign-konsolen och inte för dina mottagare, men den här rubriken visas i din lista över leveranser. Klicka **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Steg 3 - Markera ett innehåll {#step-3---selecting-a-content}

Redigeraren för digitalt innehåll innehåller olika färdiga mallar med olika strukturer (kolumner, textområden osv.).

Markera den innehållsmall som du vill använda och klicka sedan på **[!UICONTROL Start with the selected content]** knappen för att visa mallen i den skapade leveransen.

![](assets/dce_select_model.png)

Du kan också importera HTML-innehåll som har skapats utanför Adobe Campaign genom att välja **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Du kan spara innehållet som en mall för framtida bruk. När du har skapat en personlig innehållsmall kan du förhandsgranska den i listan med mallar. Mer information finns i [Mallhantering](../../web/using/template-management.md).

>[!CAUTION]
>
>Om du använder webbgränssnittet **för** Adobe Campaign måste du importera en ZIP-fil som innehåller HTML-innehållet och relaterade bilder.

## Steg 4 - Utforma meddelandet {#step-4---designing-the-message}

* Visa de första och andra namnen på mottagarna

   Om du vill infoga mottagarnas för- och efternamn i ett textfält i leveransen klickar du på det valda textfältet och placerar sedan markören där du vill att de ska visas. Klicka på den första ikonen i popup-verktygsfältet och klicka sedan på **[!UICONTROL Personalization block]**. Markera **[!UICONTROL Greetings]** och klicka sedan på **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Infoga en länk i en bild

   Om du vill dirigera leveransmottagare till en extern adress via en bild, klickar du på den relevanta bilden för att visa popup-verktygsfältet, placerar markören på den första ikonen och klickar sedan på **[!UICONTROL Link to an external URL]**. Mer information finns i [Lägga till en länk](../../web/using/editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Ange länkens URL i fältet **URL** i följande format **https://www.myURL.com** och bekräfta sedan.

   Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

* Infoga en länk i text

   Om du vill integrera en extern länk i texten i leveransen markerar du en del text eller ett textblock och klickar sedan på den första ikonen i popup-verktygsfältet. Klicka **[!UICONTROL Link to an external URL]** och ange länkadressen i **[!UICONTROL URL]** fältet. Mer information finns i [Lägga till en länk](../../web/using/editing-content.md#adding-a-link).

   Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

   >[!CAUTION]
   >
   >Den text som anges i **[!UICONTROL Label]** fältet ersätter den ursprungliga texten.

* Lägga till en spegelsida

   Om du vill att mottagarna ska kunna se leveransinnehållet i en webbläsare kan du integrera en länk till en spegelsida i leveransen.

   Klicka i det textfält där du vill se länken publicerad. Klicka på den första ikonen i popup-verktygsfältet, markera **[!UICONTROL Personalization block]** och sedan **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Bekräfta genom **[!UICONTROL Save]** att klicka.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >Anpassningsblockets etikett ersätter automatiskt den ursprungliga texten i leveransen.

* Integrera en länk till ett webbprogram

   Med Digital Content Editor kan du integrera länkar till webbprogram från Adobe Campaign-konsolen, till exempel en landningssida eller en formulärsida. Mer information finns i [Länka till ett webbprogram](../../web/using/editing-content.md#link-to-a-web-application).

   Markera ett textfält för länken till ett webbprogram och klicka sedan på den första ikonen. Välj **[!UICONTROL Link to a Web application]** och välj sedan önskat program genom att klicka på ikonen i slutet av fältet **Webbprogram** .

   ![](assets/dce_webapp.png)

   Bekräfta genom att klicka på **Spara** .

   >[!NOTE]
   >
   >I det här steget måste du spara minst ett webbprogram i förväg. Dessa finns på **[!UICONTROL Campaigns > Web applications]** fliken i konsolen.

## Steg 5 - Spara leveransen {#step-5---saving-the-delivery}

När innehållet är integrerat sparar du leveransen genom att klicka på **Spara**. Den visas nu i din lista över leveranser på fliken **[!UICONTROL Campaigns > Deliveries]** .
