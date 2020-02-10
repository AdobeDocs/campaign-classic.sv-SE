---
title: Skapa ett erbjudande
seo-title: Skapa ett erbjudande
description: Skapa ett erbjudande
seo-description: null
page-status-flag: never-activated
uuid: 9e8b0351-e2a5-4043-be86-e275d2f849ea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 010c88f4-9444-448f-bb7b-7191517d2e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Skapa ett erbjudande{#creating-an-offer}

## Skapa erbjudandet {#creating-the-offer}

Så här skapar du ett erbjudande:

1. Gå till **[!UICONTROL Campaigns]** universum och klicka på **[!UICONTROL Offers]** länken.

   ![](assets/offer_create_001.png)

1. Klicka på **[!UICONTROL Create]** knappen.

   ![](assets/offer_create_005.png)

1. Ändra etiketten och välj den kategori som erbjudandet ska tillhöra.

   ![](assets/offer_create_002.png)

1. Klicka **[!UICONTROL Save]** för att skapa erbjudandet.

   ![](assets/offer_create_003.png)

   Erbjudandet är tillgängligt på plattformen och dess innehåll kan konfigureras.

   ![](assets/offer_create_004.png)

## Konfigurera anbudsberättigande {#configuring-offer-eligibility}

Ange den period som erbjudandet gäller för och kan presenteras, de filter som ska gälla för målet och erbjudandets vikt på **[!UICONTROL Eligibility]** fliken.

### Definiera berättigandeperioden för ett erbjudande {#defining-the-eligibility-period-of-an-offer}

Använd listrutorna och välj ett start- och ett slutdatum i kalendern för att definiera berättigandeperioden för erbjudandet.

![](assets/offer_eligibility_create_002.png)

Utanför dessa datum kommer erbjudandet inte att väljas av interaktionsmotorn. Om du även har konfigurerat berättigandedatum för erbjudandekategorin gäller den mest restriktiva perioden.

### Filter på målet {#filters-on-the-target}

Du kan använda filter på erbjudandemålet.

Klicka på **[!UICONTROL Edit query]** länken och markera det filter som du vill använda. (Se [det här avsnittet](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

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

Så här skapar du en vikt i ett erbjudande:

1. Klicka **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. Ändra etiketten och tilldela en vikt. Som standard är det 1.

   ![](assets/offer_weight_create_006.png)

   >[!CAUTION]
   >
   >Om ingen vikt anges (0) anses målet inte vara berättigat till erbjudandet.

1. Om du vill att vikten ska gälla för en viss period definierar du datum för berättigande.

   ![](assets/offer_weight_create_002.png)

1. Begränsa vid behov vikten till ett visst erbjudandeutrymme.

   ![](assets/offer_weight_create_003.png)

1. Använd ett filter på ett mål.

   ![](assets/offer_weight_create_004.png)

1. Klicka **[!UICONTROL OK]** för att spara bredden.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >Om ett mål kan få flera vikter för ett valt erbjudande behåller motorn den bästa (högsta) vikten. Vid anrop till erbjudandemotorn väljs ett erbjudande högst en gång per kontakt.

### En sammanfattning av reglerna för erbjudandebehörighet {#a-summary-of-offer-eligibility-rules}

När konfigurationen är klar finns en sammanfattning av berättigandereglerna på instrumentpanelen för erbjudanden.

Klicka på **[!UICONTROL Schedule and eligibility rules]** länken om du vill visa den.

![](assets/offer_eligibility_create_005.png)

## Skapa erbjudandeinnehåll {#creating-the-offer-content}

1. Klicka på **[!UICONTROL Edit]** fliken och sedan på **[!UICONTROL Content]** fliken.

   ![](assets/offer_content_create_001.png)

1. Fyll i de olika fälten i erbjudandeinnehållet.

   * **[!UICONTROL Title]** : Ange den titel som du vill ska visas i erbjudandet. Varning: detta avser inte erbjudandets etikett, som definieras på **[!UICONTROL General]** fliken.
   * **[!UICONTROL Destination URL]** : ange erbjudandets URL. För att behandlas på rätt sätt måste det börja med&quot;http://&quot; eller&quot;https://&quot;.
   * **[!UICONTROL Image URL]** : Ange en URL eller en åtkomstsökväg till bilden av erbjudandet.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : Ange innehållet i erbjudandet på fliken som du vill ha. Om du vill generera spårning måste **[!UICONTROL HTML content]** elementet bestå av HTML-element som kan omslutas av ett `<div>` tytelement. Resultatet av ett `<table>` element på HTML-sidan blir följande:

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

   Definitionen av accepterings-URL:en visas i avsnittet [Konfigurera status när förslaget accepteras](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) .

   ![](assets/offer_content_create_002.png)

   Om du vill hitta de obligatoriska fälten så som de definierades under konfigurationen av erbjudandeutrymmet klickar du på **[!UICONTROL Content definitions]** länken för att visa listan. Mer information finns i [Skapa erbjudandemellanslag](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   I det här exemplet måste erbjudandet innehålla en titel, en bild, HTML-innehåll och en mål-URL.

## Förhandsgranska erbjudandet {#previewing-the-offer}

Så snart innehållet i erbjudandet har konfigurerats kan du förhandsgranska erbjudandet så som det kommer att visas för mottagaren. Så här gör du:

1. Klicka på **[!UICONTROL Preview]** fliken.

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

Hypoeser som utförs på ett offertförslag refereras på respektive **[!UICONTROL Measure]** flik.

Skapa hypoteser finns på [den här sidan](../../campaign/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)

