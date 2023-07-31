---
product: campaign
title: Skapa ett erbjudande
description: Skapa ett erbjudande
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: c6dd2709-06e3-4227-bbec-99f3d80144fe
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 3%

---

# Skapa ett erbjudande{#creating-an-offer}



## Skapa erbjudandet {#creating-the-offer}

Så här skapar du ett erbjudande:

1. Gå till **[!UICONTROL Campaigns]** och klicka på **[!UICONTROL Offers]** länk.

   ![](assets/offer_create_001.png)

1. Klicka på knappen **[!UICONTROL Create]**.

   ![](assets/offer_create_005.png)

1. Ändra etiketten och välj den kategori som erbjudandet ska tillhöra.

   ![](assets/offer_create_002.png)

1. Klicka **[!UICONTROL Save]** för att skapa erbjudandet.

   ![](assets/offer_create_003.png)

   Erbjudandet är tillgängligt på plattformen och dess innehåll kan konfigureras.

   ![](assets/offer_create_004.png)

## Konfigurera anbudsberättigande {#configuring-offer-eligibility}

I **[!UICONTROL Eligibility]** kan du definiera den period som erbjudandet gäller och kan presenteras, de filter som ska gälla för målet och erbjudandets vikt.

### Definiera berättigandeperioden för ett erbjudande {#defining-the-eligibility-period-of-an-offer}

Använd listrutorna och välj ett start- och ett slutdatum i kalendern för att definiera berättigandeperioden för erbjudandet.

![](assets/offer_eligibility_create_002.png)

Utanför dessa datum kommer erbjudandet inte att väljas av interaktionsmotorn. Om du även har konfigurerat berättigandedatum för erbjudandekategorin gäller den mest restriktiva perioden.

### Filter på målet {#filters-on-the-target}

Du kan använda filter på erbjudandemålet.

Klicka på **[!UICONTROL Edit query]** och välj det filter som du vill använda. (Se [det här avsnittet](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

Om fördefinierade filter redan har skapats kan du välja dem i listan med användarfilter. Mer information finns i [Skapa fördefinierade filter](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### Erbjudandevikt {#offer-weight}

Om du vill att motorn ska kunna välja mellan flera erbjudanden som målet är kvalificerat för, måste du tilldela ett eller flera vikter till erbjudandet. Du kan också tillämpa filter på målet om det behövs eller begränsa det erbjudandeutrymme som vikten gäller för. Ett erbjudande med större vikt är att föredra framför ett erbjudande med mindre vikt.

Du kan konfigurera flera vikter för samma erbjudande, t.ex. för att skilja mellan delperioder, specifika mål eller till och med ett erbjudandeutrymme.

Ett erbjudande kan till exempel ha vikten A för kontakter mellan 18 och 25 år och vikten B för kontakter över detta intervall. Om ett erbjudande är giltigt hela sommaren kan det även ha A i juli och B i augusti.

>[!NOTE]
>
>Den tilldelade vikten kan ändras tillfälligt enligt parametrarna för den kategori som erbjudandet tillhör. Mer information finns i [Skapa erbjudandekategorier](../../interaction/using/creating-offer-categories.md).

Gör så här för att skapa en vikt i ett erbjudande:

1. Klicka på **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. Ändra etiketten och tilldela en vikt. Som standard är det 1.

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >Om ingen vikt anges (0) anses målet inte vara berättigat till erbjudandet.

1. Om du vill att vikten ska gälla för en viss period definierar du datum för berättigande.

   ![](assets/offer_weight_create_002.png)

1. Begränsa vid behov vikten till ett visst erbjudandeutrymme.

   ![](assets/offer_weight_create_003.png)

1. Använd ett filter på ett mål.

   ![](assets/offer_weight_create_004.png)

1. Klicka **[!UICONTROL OK]** för att spara vikt.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >Om ett mål kan få flera vikter för ett valt erbjudande behåller motorn den bästa (högsta) vikten. Vid anrop till erbjudandemotorn väljs ett erbjudande högst en gång per kontakt.

### Sammanfattning av regler för erbjudandekvalificering {#a-summary-of-offer-eligibility-rules}

När konfigurationen är klar finns en sammanfattning av berättigandereglerna på instrumentpanelen för erbjudanden.

Klicka på **[!UICONTROL Schedule and eligibility rules]** länk.

![](assets/offer_eligibility_create_005.png)

## Skapa erbjudandeinnehåll {#creating-the-offer-content}

1. Klicka på **[!UICONTROL Edit]** klickar du på **[!UICONTROL Content]** -fliken.

   ![](assets/offer_content_create_001.png)

1. Fyll i de olika fälten i erbjudandeinnehållet.

   * **[!UICONTROL Title]** : Ange den titel som du vill ska visas i erbjudandet. Varning: detta avser inte erbjudandets etikett, som definieras i **[!UICONTROL General]** -fliken.
   * **[!UICONTROL Destination URL]** : ange erbjudandets URL. För att behandlas på rätt sätt måste det börja med&quot;http://&quot; eller&quot;https://&quot;.
   * **[!UICONTROL Image URL]** : ange en URL eller en åtkomstsökväg till bilden av ditt erbjudande.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : Ange innehållet i erbjudandet på den flik du vill ha. Om du vill generera spårning visas **[!UICONTROL HTML content]** måste bestå av HTML-element som kan omslutas av en `<div>` type-element. Resultatet av en `<table>` -elementet på HTML-sidan kommer att följas:

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   Definiera accepterings-URL:en visas i [Konfigurera status när förslaget godkänns](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) -avsnitt.

   ![](assets/offer_content_create_002.png)

   Om du vill hitta de obligatoriska fälten som de definierades under konfigurationen av erbjudandeutrymmet klickar du på knappen **[!UICONTROL Content definitions]** länk för att visa listan. Mer information finns i [Skapa erbjudandemellanslag](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   I det här exemplet måste erbjudandet innehålla en titel, en bild, HTML och en mål-URL.

## Förhandsgranska erbjudandet {#previewing-the-offer}

Så snart innehållet i erbjudandet har konfigurerats kan du förhandsgranska erbjudandet så som det kommer att visas för mottagaren. Så här gör du:

1. Klicka på **[!UICONTROL Preview]** -fliken.

   ![](assets/offer_preview_create_001.png)

1. Välj den representation av erbjudandet som du vill visa.

   ![](assets/offer_preview_create_002.png)

1. Om du har personaliserat erbjudandeinnehållet väljer du erbjudandemålet för att visa personalisering.

   ![](assets/offer_preview_create_003.png)

## Skapa en hypotes om ett erbjudande {#creating-a-hypothesis-on-an-offer}

Du kan skapa hypoteser om dina erbjudanden. På så sätt kan du avgöra hur era erbjudanden påverkar de inköp som görs för den berörda produkten.

>[!NOTE]
>
>Dessa hypoteser utförs via Response Manager. Kontrollera licensavtalet.

Hypoeser som utförs på ett offertförslag hänvisas till i deras **[!UICONTROL Measure]** -fliken.

Skapa hypoteser beskrivs i [den här sidan](../../response/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)
