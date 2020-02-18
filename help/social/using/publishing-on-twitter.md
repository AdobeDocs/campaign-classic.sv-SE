---
title: Publicera på Twitter
seo-title: Publicera på Twitter
description: Publicera på Twitter
seo-description: null
page-status-flag: never-activated
uuid: 405bce50-a63c-4bd3-8f03-c71809bb1cfd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 2dc278ce-477c-493d-8abb-8bbdf2e988a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Publicera på Twitter{#publishing-on-twitter}

## Publicera på dina Twitter-konton {#publishing-on-your-twitter-accounts}

När konfigurationen är klar kan du med Social Marketing skicka tweets till dina Twitter-konton.

### Begränsningar {#limitations}

Följande begränsningar är begränsningar som är inbyggda i Twitter.

* Meddelandet får inte vara längre än 140 tecken.
* HTML-format stöds inte.

### Skapa leveransen {#creating-the-delivery}

Skapa en ny leverans baserat på **[!UICONTROL Tweet (twitter)]** leveransmallen.

![](assets/social_twitter_delivery_001.png)

### Välja huvudmål {#selecting-the-main-target}

Markera det eller de konton som du vill skicka tweets till.

1. Klicka på **[!UICONTROL To]** länken.

   ![](assets/social_twitter_delivery_002.png)

1. Klicka på **[!UICONTROL Add]** knappen.

   ![](assets/social_twitter_delivery_006.png)

1. Välj **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. I **[!UICONTROL Folder]** fältet väljer du den tjänstmapp som innehåller Twitter-kontot. Välj sedan det Twitter-konto som du vill skicka tweeten till.

   ![](assets/social_twitter_delivery_011.png)

### Välja provtryckets mål {#selecting-the-target-of-the-proof}

På fliken **[!UICONTROL Target of the proofs]** kan du definiera det Twitter-konto som ska användas för testleveranser före den slutliga leveransen. Därför rekommenderar vi att du skapar ett privat Twitter-konto som är dedikerat till att skicka korrektur. Mer information om hur du skapar ett privat Twitter-konto finns i [Skapa ett testkonto på Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Stegen för val av korrekturmål är desamma som för val av huvudmål. Se [Skapa ett testkonto på Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter).

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>Om du använder samma Twitter-testkonto för alla leveranser kan du spara korrekturmålet i **[!UICONTROL Tweet]** leveransmallen, som du når via **[!UICONTROL Resources > Templates > Delivery templates]** noden. Korrekturmålet anges sedan som standard för varje ny leverans.

### Definiera meddelandeinnehållet {#defining-the-message-content}

Skriv in innehållet i tweeten på **[!UICONTROL Content]** fliken.

![](assets/social_twitter_delivery_005.png)

### Visa förhandsgranskningen {#viewing-the-preview}

På fliken **[!UICONTROL Preview]** kan du visa en återgivning av tweeten.

1. Klicka på **[!UICONTROL Preview]** fliken.
1. Klicka på den **[!UICONTROL Test personalization]** nedrullningsbara menyn och välj **[!UICONTROL Service]**.
1. I **[!UICONTROL Folder]** fältet väljer du den tjänstmapp som innehåller ditt Twitter-konto.
1. Välj det Twitter-konto som du vill testa förhandsvisningen med.

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>Förhandsvisningen kan skilja sig något från den slutliga tweeten. Vi rekommenderar starkt att du skickar ett korrektur före slutleverans för att få en exakt återgivning av tweeten. Se [Skicka korrekturet](#sending-the-proof).

### Konfigurerar spårning {#configuring-tracking}

Spårning kan visas i leveransrapporterna och på fliken **[!UICONTROL Edit > Tracking]** för leverans och tjänsten.

Spårningskonfigurationen är densamma som för en e-postleverans. Mer information finns i [det här avsnittet](../../delivery/using/monitoring-a-delivery.md).

>[!NOTE]
>
>Spårning är aktiverat som standard i leveransmallen. **[!UICONTROL Tweet]**

>[!IMPORTANT]
>
>Vi kan inte skilja på robotar som analyserar tweets och användare som faktiskt klickar.

### Skicka korrekturet {#sending-the-proof}

Vi rekommenderar starkt att du skickar ett bevis på din publikation före slutleveransen för att få en exakt återgivning av publikationen på en privat Twitter-testsida. Mer information om hur du skapar ett privat Twitter-konto finns i [Skapa ett testkonto på Twitter](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter). Stegen för val av korrekturmål beskrivs i [Välja provtryckets](#selecting-the-target-of-the-proof)mål.

Korrekturleveranser är identiska med e-postleveranser. Se [det här avsnittet](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Skicka meddelandet {#sending-the-message}

1. När innehållet har godkänts klickar du på **[!UICONTROL Send]** .
1. Markera **[!UICONTROL Deliver as soon as possible]** och klicka på **[!UICONTROL Analyze]** knappen.

   >[!NOTE]
   >
   >Med det här **[!UICONTROL Postpone the delivery]** alternativet kan du skjuta upp leveransen till ett senare datum.

   ![](assets/social_twitter_delivery_012.png)

1. Kontrollera resultatet när analysen är klar.
1. Klicka **[!UICONTROL Confirm delivery]** och sedan på **[!UICONTROL Yes]**.

![](assets/social_facebook_delivery_016.png)

## Skicka direktmeddelanden till prenumeranter {#sending-direct-messages-to-subscribers}

### Verksamhetsprincip {#operating-principle}

Arbetsflödet **[!UICONTROL Synchronize Twitter accounts]** (se [Synkronisera Twitter-konton](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)) återställer listan över Twitter-prenumeranter så att du kan skicka dem direkt. De återskapade följarna lagras i en specifik tabell: besökstabellen. Om du vill visa listan med Twitter-följare går du till **[!UICONTROL Profiles and Targets > Visitors]** noden.

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>För att arbetsflödet ska kunna återskapa listan med Twitter-följare måste du markera **[!UICONTROL Synchronize Twitter accounts]** rutan i fönstret Redigera för den tjänst som är länkad till kontot. Mer information finns i: Delegera [skrivåtkomst till Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign).

Adobe Campaign återhämtar följande information för varje följare:

* **[!UICONTROL Origin]**: det sociala nätverkets namn (**Twitter** i det här fallet)
* **[!UICONTROL External ID]**: användar-ID
* **[!UICONTROL User name]**: användarens kontonamn
* **[!UICONTROL Full name]**: användarens namn
* **[!UICONTROL Language]**: användarspråk
* **[!UICONTROL Number of friends]**: antal följare
* **[!UICONTROL Time zone]**: användartidszon
* **[!UICONTROL Verified]**: det här fältet anger om användaren har ett verifierat Twitter-konto

### Begränsningar {#limitations-1}

Följande begränsningar är begränsningar som är inbyggda i Twitter.

* Meddelandet får inte vara längre än 140 tecken.
* HTML stöds inte.
* Du kan inte skicka mer än 250 direktmeddelanden per dag. För att undvika att överskrida detta tröskelvärde kan du leverera i flera vågor. Leveranser i påfyllnader konfigureras som e-postleveranser. Mer information finns i [det här avsnittet](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Skapa leveransen {#creating-the-delivery-}

Skapa en ny leverans baserat på **[!UICONTROL Tweet (Direct Message)]** leveransmallen.

![](assets/social_twitter_delivery_010.png)

### Välja huvudmål {#selecting-the-main-target-1}

Välj de följare som du vill skicka ditt direktmeddelande till.

1. Klicka på **[!UICONTROL To]** länken.

   ![](assets/social_twitter_delivery_016.png)

1. Klicka på **[!UICONTROL Add]** knappen.

   ![](assets/social_twitter_delivery_006.png)

1. Välj en typ av mål.

   ![](assets/social_twitter_delivery_017.png)

   * Välj **[!UICONTROL Twitter subscribers]** att skicka ett direktmeddelande till alla kontoföljare.

      >[!IMPORTANT]
      >
      >Du kan inte skicka mer än 250 meddelanden per dag. Om ditt Twitter-konto har fler än 250 följare rekommenderar vi att du levererar i vågor. Detta innebär samma process som för e-postleveranser. Se [det här avsnittet](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * Välj **[!UICONTROL Filter conditions]** för att definiera en fråga och visa resultatet. Det här alternativet är detsamma som för e-postleveranser. Mer information finns i [det här avsnittet](../../platform/using/defining-filter-conditions.md) .

      ![](assets/social_twitter_delivery_018.png)

### Välja provtryckets mål {#selecting-the-target-of-the-proof-1}

På fliken **[!UICONTROL Target of the proofs]** kan du välja den följare som ska få korrekturet av ditt direktmeddelande. Markeringsprocessen är densamma som för huvudmålet. Se [Välja huvudmål](#selecting-the-main-target).

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>Om du vill skicka alla dina korrektur för direktmeddelanden till samma Twitter-följare kan du spara korrekturmålet i **[!UICONTROL Tweet (Direct Message)]** leveransmallen som nås via **[!UICONTROL Resources > Templates > Delivery templates]** noden. Korrekturmålet anges sedan som standard för varje ny leverans.

### Definiera meddelandeinnehåll {#defining-message-content-}

Ange tweetens innehåll på **[!UICONTROL Content]** fliken.

![](assets/social_twitter_delivery_015.png)

Anpassningsfält kan användas på samma sätt som för e-postleveranser, t.ex. för att lägga till följarens namn i meddelandets brödtext. Innehållspersonalisering beskrivs i [det här avsnittet](../../delivery/using/about-personalization.md).

![](assets/social_twitter_delivery_021.png)

Följande steg är samma som när du skickar en tweet till ett Twitter-konto. Mer information finns i [Publicera på Twitter-konton](#publishing-on-your-twitter-accounts).
