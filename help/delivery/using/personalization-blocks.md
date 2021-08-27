---
product: campaign
title: Block för personalisering
description: Block för personalisering
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 2%

---

# Block för personalisering{#personalization-blocks}

![](../../assets/common.svg)

Personaliseringsblock är dynamiska, personaliserade och innehåller en specifik rendering som du kan infoga i leveranserna. Du kan till exempel lägga till en logotyp, ett gratulationsmeddelande eller en länk till en spegelsida. Se [Infoga anpassningsblock](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png)[ Upptäck den här funktionen i en video](#personalization-blocks-video)

Personaliseringsblock nås via noden **[!UICONTROL Resources > Campaign Management > Personalization blocks]** i Adobe Campaign Explorer. Flera block är tillgängliga som standard (se [Körklara anpassningsblock](#out-of-the-box-personalization-blocks)).

Ni kan definiera nya block som gör att ni kan optimera er leveranspersonalisering. Mer information finns i [Definiera anpassade anpassningsblock](#defining-custom-personalization-blocks).

>[!NOTE]
>
>Anpassningsblock finns också tillgängliga från **[!UICONTROL Digital Content Editor (DCE)]**. Mer information finns på [den här sidan](../../web/using/editing-content.md#inserting-a-personalization-block).

## Infoga personaliseringsblock {#inserting-personalization-blocks}

Följ stegen nedan om du vill infoga ett anpassningsblock i ett meddelande:

1. Klicka på ikonen för det anpassade fältet i innehållsredigeraren i leveransguiden och välj menyn **[!UICONTROL Include]**.
1. Välj ett anpassningsblock i listan (listan visar de 10 senast använda blocken) eller klicka på menyn **[!UICONTROL Other...]** för att få tillgång till den fullständiga listan.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Menyn **[!UICONTROL Other...]** ger åtkomst till alla färdiga och anpassade anpassningsblock (se [Körklara anpassningsblock](#out-of-the-box-personalization-blocks) och [Definiera anpassade anpassningsblock](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Personaliseringsblocket infogas sedan som ett skript. Den anpassas automatiskt till mottagarprofilen när personalisering genereras.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Klicka på fliken **[!UICONTROL Preview]** och välj en mottagare för att visa personaliseringen.

   ![](assets/s_ncs_user_personalized_block04.png)

Du kan inkludera källkoden för ett personaliseringsblock i leveransinnehållet. Om du vill göra det väljer du **[!UICONTROL Include the HTML source code of the block]** när du markerar den.

![](assets/s_ncs_user_personalized_block05.png)

HTML-källkoden infogas i leveransinnehållet. Personaliseringsblocket **[!UICONTROL Greetings]** visas till exempel enligt nedan:

![](assets/s_ncs_user_personalized_block06.png)

## Exempel på personaliseringsblock {#personalization-blocks-example}

I det här exemplet skapar vi ett e-postmeddelande där vi använder personaliseringsblock för att göra det möjligt för mottagaren att visa spegelsidan, dela nyhetsbrevet i sociala nätverk och avbryta prenumerationen på framtida leveranser.

För att göra detta måste vi infoga följande personaliseringsblock:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Mer information om generering av spegelsida finns i [Generera spegelsidan](sending-messages.md#generating-the-mirror-page).

1. Skapa en ny leverans eller öppna en befintlig e-posttypsleverans.
1. Klicka på **[!UICONTROL Subject]** i leveransguiden för att redigera meddelandets ämne och ange ett ämne.
1. Infoga personaliseringsblocken i meddelandetexten. Det gör du genom att klicka i meddelandeinnehållet, klicka på ikonen för anpassat fält och välja menyn **[!UICONTROL Include]**.
1. Markera det första blocket som ska infogas. Förnya proceduren och inkludera de två andra blocken.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Klicka på fliken **[!UICONTROL Preview]** för att visa personaliseringsresultatet. Du måste välja en mottagare för att kunna visa mottagarens meddelande.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Bekräfta att blockinnehållet visas korrekt.

## Körklara personaliseringsblock {#out-of-the-box-personalization-blocks}

En lista med personaliseringsblock är som standard tillgänglig för att hjälpa dig att anpassa innehållet i meddelandet.

>[!NOTE]
>
>Listan med personaliseringsblock beror på vilka moduler och alternativ som har installerats på din instans.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : infogar hälsningar med mottagarens namn. Exempel: &quot;Hej John Doe.&quot;
* **[!UICONTROL Insert logo]** : infogar en logotyp som inte finns i rutan och som har definierats när instansen konfigureras.
* **[!UICONTROL Powered by Adobe Campaign]** : infogar logotypen&quot;Powered by Adobe Campaign&quot;.
* **[!UICONTROL Mirror page URL]** : infogar spegelsidans URL, vilket gör att leveransdesigners kan kontrollera länken.

   >[!NOTE]
   >
   >Mer information om generering av spegelsida finns i [Generera spegelsidan](sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : infogar en länk till spegelsidan: &quot;Om du inte kan visa det här meddelandet korrekt klickar du här&quot;.
* **[!UICONTROL Unsubscription link]** : infogar en länk som gör det möjligt att avbryta prenumerationen på alla leveranser (blockeringslista).
* **[!UICONTROL Formatting function for proper nouns]** : genererar  **[!UICONTROL toSmartCase]** JavaScript-funktionen, som ändrar den första bokstaven i varje ord till versaler.
* **[!UICONTROL Registration page URL]** : infogar en prenumerations-URL (se  [Om tjänster och prenumerationer](about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : infogar en prenumerationslänk. som har definierats när instansen konfigureras.
* **[!UICONTROL Registration link (with referrer)]** : infogar en prenumerationslänk som gör det möjligt att identifiera besökaren och leveransen. Länken har definierats när instansen konfigureras.

   >[!NOTE]
   >
   >Det här blocket kan bara användas för leveranser till besökare.

* **[!UICONTROL Registration confirmation]** : infogar en länk som bekräftar prenumerationen.
* **[!UICONTROL Social network sharing links]** : infogar knappar som gör att mottagaren kan dela en länk till det spegelvända sidinnehållet med e-postklienten, Facebook, Twitter och LinkedIn (se  [Viral marketing: till en vän](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** och  **[!UICONTROL Notification style]** : generera kod som formaterar ett e-postmeddelande med fördefinierade HTML-format. Dessa block måste infogas i källkoden för leveransen, i avsnittet **[!UICONTROL ...]**, i **`<style>...</style>`**-taggar.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : infogar en URL som gör det möjligt att ange ett interaktionserbjudande  **[!UICONTROL Accepted]** (se  [det här avsnittet](../../interaction/using/offer-analysis-report.md)).

## Definiera anpassade personaliseringsblock {#defining-custom-personalization-blocks}

Du kan definiera nya anpassningsfält som ska infogas från den anpassade fältikonen via menyn **[!UICONTROL Include...]**. Dessa fält definieras i personaliseringsblock.

Om du vill skapa ett personaliseringsblock går du till Utforskaren och utför följande steg:

1. Klicka på noden **[!UICONTROL Resources > Campaign Management > Personalization blocks]**.
1. Högerklicka på listan med block och välj **[!UICONTROL New]** .
1. Fyll i inställningarna för anpassningsblocket:

   ![](assets/s_ncs_user_personalized_block.png)

   * Ange blockets etikett. Den här etiketten visas i fönstret där personaliseringsfältet infogas.
   * Välj **[!UICONTROL Visible in the customization menus]** om du vill göra det här blocket tillgängligt från ikonen för infogning av anpassningsfält.
   * Om det behövs väljer du **[!UICONTROL The content of the personalization block depends upon the format]** för att definiera två separata block för e-postmeddelanden i HTML-format och de i textformat.

      Två flikar visas sedan i det nedre avsnittet av redigeraren (HTML-innehåll och textinnehåll) för att definiera motsvarande innehåll.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Ange innehållet (i HTML, text, JavaScript osv.) av anpassningsblocket/personaliseringsblocken och klicka på **[!UICONTROL Save]**.

## Videokurs {#personalization-blocks-video}

Lär dig hur du skapar dynamiska innehållsblock och hur du använder dem för att anpassa innehållet i e-postleveransen.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
