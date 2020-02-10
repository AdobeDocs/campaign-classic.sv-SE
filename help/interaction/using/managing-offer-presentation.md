---
title: Hantera presentation av erbjudanden
seo-title: Hantera presentation av erbjudanden
description: Hantera presentation av erbjudanden
seo-description: null
page-status-flag: never-activated
uuid: cf4614b9-a322-4170-aa6d-4f138f8ca2d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: f6e44634-3a13-480e-ab44-f3c744054a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Hantera presentation av erbjudanden{#managing-offer-presentation}

## Översikt över presentationsregler {#presentation-rules-overview}

Med interaktion kan ni styra flödet av erbjudandeförslag med hjälp av presentationsregler. Dessa regler, som är specifika för Interaktion, är typologiregler. Med dem kan du utesluta erbjudanden baserat på historiken för de förslag som redan har lämnats till en mottagare. De refereras i miljön

## Skapa och referera till en presentationsregel för erbjudande {#creating-and-referencing-an-offer-presentation-rule}

1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** noden.
1. Skapa en typologiregel och välj **[!UICONTROL Offer presentation]** typ.

   ![](assets/offer_typology_001.png)

1. Ange kanalen som regeln ska gälla för.

   ![](assets/offer_typology_002.png)

1. Konfigurera regelns programvillkor. Mer information finns i Inställningar för [presentationsregel](#presentation-rule-settings).
1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** noden och skapa en typologi som grupperar alla **[!UICONTROL Offer presentation]** textregler.

   ![](assets/offer_typology_003.png)

1. När typologin har skapats placerar du markören på typologireglerna och grupperar dem i den typologi du just har skapat.

   ![](assets/offer_typology_004.png)

1. I er erbjudandemiljö kan du referera till typologin i listrutan.

   ![](assets/offer_typology_005.png)

## Inställningar för presentationsregel {#presentation-rule-settings}

### Ansökningskriterier {#application-criteria-}

Med de programvillkor som finns på fliken **[!UICONTROL General]** kan du ange vilka erbjudanden presentationsregeln ska gälla för. För att kunna göra detta måste du skapa en fråga och välja de aktuella erbjudandena enligt beskrivningen nedan.

1. Klicka på länken för att skapa din fråga i din typologiregel **[!UICONTROL Edit the rule application conditions...]** .

   ![](assets/offer_typology_006.png)

1. I frågefönstret kan du tillämpa ett filter på de erbjudanden som du vill tillämpa en typologiregel på.

   Du kan till exempel välja en erbjudandekategori.

   ![](assets/offer_typology_008.png)

### Erbjudandedimensioner {#offer-dimensions}

På fliken **[!UICONTROL Offer presentation]** måste du ange samma dimensioner för presentationsregeln som de som konfigurerats i miljön.

De **[!UICONTROL Targeting dimension]** sammanfaller med mottagartabellen (som standard: nms:mottagare) som får erbjudandeförslagen. Detta sammanfaller **[!UICONTROL Storage dimension]** med tabellen som innehåller den förslagshistorik som är länkad till måldimensionen (som standard:nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>Du kan också använda tabeller som inte är standard. Om du vill använda en specifik målgruppsdimension måste du skapa tabeller och en dedikerad miljö med målmappningen. Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### Period {#period}

Detta är en glidande period som börjar på presentationsdatumet för erbjudandet. Det fastställer en tidsgräns för giltigheten för erbjudandeförslag. Regeln gäller inte för offertförslag som gjorts efter denna period.

Perioden börjar **n** dagar före förslagsdatumet och slutar **n** dagar därefter, där **n** motsvarar numret som anges i **[!UICONTROL Period considered]** fältet:

* För inkommande blanksteg är förslagsdatumet presentationsdatumet.
* För utgående blanksteg är förslagsdatumet leveransens kontaktdatum (till exempel leveransdatumet som anges i ett målarbetsflöde).

Använd pilarna för att ändra antalet dagar eller ange en punkt direkt (&quot;2d 6h&quot;, till exempel).

![](assets/offer_typology_010.png)

### Antal offerter {#number-of-propositions}

Det är möjligt att fastställa det högsta antal anbud som kan lämnas innan de berörda erbjudandena utesluts.

Använd pilarna för att ändra antalet offertförslag.

![](assets/offer_typology_011.png)

## Definiera förslag och mottagare {#defining-propositions-and-recipients}

I **[!UICONTROL Propositions to count]** **[!UICONTROL General]** avsnittet kan du ange både mottagare och förslag som kommer att leda till att de erbjudanden som definieras på fliken utesluts om de visas ett visst antal gånger i förslagshistoriken.

### Filtrera förslag {#filtering-propositions}

Du kan välja filtreringskriterier för att exkludera offerter baserat på kanal, erbjudanden eller status för tidigare tilldelade offerter.

![](assets/offer_typology_014.png)

Dessa kriterier är de vanligaste tillämpningarna av presentationsregler. Om du vill använda andra villkor kan du skapa en fråga via **[!UICONTROL Limit propositions...]** länken. Mer information finns i avsnittet [Skapa en fråga om förslag](#creating-a-query-on-propositions) .

* **Filtrera på kanalen**

   **[!UICONTROL On the same channel only]** : Med kan du utesluta erbjudandeförslag på den kanal som anges på **[!UICONTROL General]** fliken.

   Kanalen som anges för regeln på fliken är till exempel e-post **[!UICONTROL General]** . Om de erbjudanden som regeln gäller hittills bara fanns på webbkanalen kan interaktionsmotorn presentera erbjudandena i en e-postleverans. Men när erbjudandena har presenterats via e-post väljer interaktionsmotorn en annan kanal för att presentera erbjudandena.

   >[!NOTE]
   >
   >Vi pratar om kanalen och inte rymden. Om regeln utesluter ett erbjudande på webbkanalen kommer det erbjudande som ska presenteras på en webbplats i två blanksteg (i en banderoll och till exempel i sidans brödtext) inte att visas på webbplatsen om det redan har presenterats tidigare.
   >
   >För ett arbetsflöde som innehåller en erbjudandepresentation beaktas reglerna bara korrekt om de är konfigurerade för **[!UICONTROL All channels]**.

* **Filtrera på erbjudandet**

   Med det här filtret kan du begränsa antalet erbjudandeförslag som ska räknas till specifika erbjudanden.

   **[!UICONTROL All offers]** : standardvärde. Inget filter tillämpas på erbjudandena.

   **[!UICONTROL Offer being presented]** : erbjudandet som anges på **[!UICONTROL General]** fliken utesluts om det redan har presenterats.

   **[!UICONTROL Offers from the same category]** : ett erbjudande utesluts om ett erbjudande från samma kategori redan har lämnats in.

   **[!UICONTROL The offers which the rule applies to]** : När flera erbjudanden definieras på **[!UICONTROL General]** fliken, beaktas alla erbjudandeförslag från den här uppsättningen med erbjudanden och avslutas med att alla erbjudanden utesluts om tröskelvärdet för erbjudandet nås.

   Erbjudandena 2, 3 och 5 definieras till exempel på **[!UICONTROL General]** fliken. Det högsta antalet offerter är 2. Om erbjudandena 2 och 5 presenteras en gång, kommer antalet offerter att vara 2. Därför kommer erbjudande 3 aldrig att presenteras.

* **Filter på förslagsstatus**

   Med det här filtret kan du välja de vanligaste statusvärdena för erbjudandeförslag som ska beaktas i förslagshistoriken.

   **[!UICONTROL Regardless of the proposition status]** : standardvärde. Inget filter tillämpas på förslagets status.

   **[!UICONTROL Accepted or rejected propositions]** : kan du utesluta tidigare presenterade erbjudanden som har godkänts eller avvisats.

   **[!UICONTROL Accepted propositions]** : kan du utesluta tidigare presenterade erbjudanden som har godkänts.

   **[!UICONTROL Rejected propositions]** : kan du utesluta tidigare erbjudanden som har avvisats.

### Definiera mottagare {#defining-recipients}

Om du vill ange mottagare klickar du på **[!UICONTROL Edit the query from the targeting dimension...]** länken och väljer de mottagare som berörs av regeln.

![](assets/offer_typology_012.png)

### Skapa en fråga om förslag {#creating-a-query-on-propositions}

Om du vill ange de förslag som ska räknas via en fråga klickar du på **[!UICONTROL Limit propositions...]** länken och anger de villkor som ska beaktas.

I följande exempel är de förslag som ska räknas efter två presentationer de som finns i kategorin **Specialerbjudanden** , för **Call center** , med en vikt under **20**.

![](assets/offer_typology_013.png)

