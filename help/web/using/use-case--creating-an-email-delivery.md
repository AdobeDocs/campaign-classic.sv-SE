---
product: campaign
title: Användningsfall - skapa e-postleverans
description: Skapa ett användningsfall för e-postleverans
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Användningsfall: skapa en e-postleverans{#use-case-creating-an-email-delivery}

![](../../assets/common.svg)

I det här fallet får du lära dig hur du utformar en e-postleverans med Adobe Campaign Digital Content Editor (DCE).

Vårt sista mål är att skapa en leverans med en personlig mall som innehåller:

* En direkt adress till en mottagare (med för- och efternamn)
* Två typer av länkar till en extern URL
* En spegelsida
* En länk till ett webbprogram

>[!NOTE]
>
>Innan du börjar måste du ha minst en **HTML-mall** konfigurerad för att vara värd för innehållet i dina framtida leveranser.
>
>I leveransen **[!UICONTROL Properties]** måste du se till att **[!UICONTROL Content editing mode]** (i **[!UICONTROL Advanced]** tab) är inställd på **[!UICONTROL DCE]**. För att säkerställa att redigeraren fungerar optimalt kan du läsa [Bästa praxis för innehållsredigering](content-editing-best-practices.md).

## Steg 1 - Skapa en leverans {#step-1---creating-a-delivery}

Om du vill skapa en ny leverans placerar du markören i **Kampanjer** och klicka **Leveranser**. Klicka på **Skapa** ovanför listan över befintliga leveranser. Mer information om hur du skapar leveranser finns i [den här sidan](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## Steg 2 - Välja en mall {#step-2---selecting-a-template}

Välj en leveransmall och ge sedan leveransen ett namn. Det här namnet visas endast för användare av Adobe Campaign-konsolen och inte för dina mottagare, men den här rubriken visas i din lista över leveranser. Klicka på **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## Steg 3 - Markera ett innehåll {#step-3---selecting-a-content}

Redigeraren för digitalt innehåll innehåller olika färdiga mallar med olika strukturer (kolumner, textområden osv.).

Markera den innehållsmall som du vill använda och klicka sedan på **[!UICONTROL Start with the selected content]** för att visa mallen i den skapade leveransen.

![](assets/dce_select_model.png)

Du kan även importera HTML-innehåll som har skapats utanför Adobe Campaign genom att markera **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

Du kan spara innehållet som en mall för framtida bruk. När du har skapat en personlig innehållsmall kan du förhandsgranska den i listan med mallar. Mer information finns i [Mallhantering](template-management.md).

>[!CAUTION]
>
>Om du använder **Adobe Campaign webbgränssnitt** måste du importera en ZIP-fil som innehåller HTML-innehåll och relaterade bilder.

## Steg 4 - Utforma meddelandet {#step-4---designing-the-message}

* Visa de första och andra namnen på mottagarna

   Om du vill infoga mottagarnas för- och efternamn i ett textfält i leveransen klickar du på det valda textfältet och placerar sedan markören där du vill att de ska visas. Klicka på den första ikonen i popup-verktygsfältet och klicka sedan på **[!UICONTROL Personalization block]**. Välj **[!UICONTROL Greetings]** och sedan klicka **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* Infoga en länk i en bild

   Om du vill dirigera leveransmottagare till en extern adress via en bild, klickar du på den relevanta bilden för att visa popup-verktygsfältet, placerar markören på den första ikonen och klickar sedan på **[!UICONTROL Link to an external URL]**. Mer information finns i [Lägga till en länk](editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   Ange länkens URL i dialogrutan **URL** fält med följande format **https://www.myURL.com**, och bekräfta sedan.

   Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

* Infoga en länk i text

   Om du vill integrera en extern länk i texten i leveransen markerar du en del text eller ett textblock och klickar sedan på den första ikonen i popup-verktygsfältet. Klicka **[!UICONTROL Link to an external URL]** anger du länkadressen i **[!UICONTROL URL]** fält. Mer information finns i [Lägga till en länk](editing-content.md#adding-a-link).

   Länken kan ändras när som helst med hjälp av avsnittet till höger om fönstret.

   >[!CAUTION]
   >
   >Den text som anges i **[!UICONTROL Label]** fältet ersätter den ursprungliga texten.

* Lägga till en spegelsida

   Om du vill att mottagarna ska kunna se leveransinnehållet i en webbläsare kan du integrera en länk till en spegelsida i leveransen.

   Klicka i det textfält där du vill se länken publicerad. Klicka på den första ikonen i popup-verktygsfältet och välj **[!UICONTROL Personalization block]** sedan **[!UICONTROL Link to Mirror Page (MirrorPage)]**. Klicka **[!UICONTROL Save]** för att bekräfta.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >Anpassningsblockets etikett ersätter automatiskt den ursprungliga texten i leveransen.

* Integrera en länk till ett webbprogram

   Med Digital Content Editor kan du integrera länkar till webbprogram från Adobe Campaign-konsolen, till exempel en landningssida eller en formulärsida. Mer information finns i [Länka till ett webbprogram](editing-content.md#link-to-a-web-application).

   Markera ett textfält för länken till ett webbprogram och klicka sedan på den första ikonen. Välj **[!UICONTROL Link to a Web application]** markerar du sedan det önskade programmet genom att klicka på ikonen i slutet av **Webbprogram** fält.

   ![](assets/dce_webapp.png)

   Klicka **Spara** för att bekräfta.

   >[!NOTE]
   >
   >I det här steget måste du spara minst ett webbprogram i förväg. Dessa finns i **[!UICONTROL Campaigns > Web applications]** -fliken i konsolen.

## Steg 5 - Spara leveransen {#step-5---saving-the-delivery}

När innehållet är integrerat sparar du leveransen genom att klicka **Spara**. Den visas nu i din lista över leveranser som finns i **[!UICONTROL Campaigns > Deliveries]** -fliken.
