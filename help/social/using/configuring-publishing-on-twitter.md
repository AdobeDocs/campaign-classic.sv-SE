---
title: Konfigurera publicering på Twitter
seo-title: Konfigurera publicering på Twitter
description: Konfigurera publicering på Twitter
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# Konfigurera publicering på Twitter{#configuring-publishing-on-twitter}

För att Adobe Campaign ska kunna skicka tweets till dina Twitter-konton måste du delegera skrivåtkomst till Adobe Campaign för dessa konton. Gör detta genom att utföra följande konfigurationssteg:

* Skapa ett Twitter-konto.
* Skapa ett Twitter-testkonto för att skicka korrektur.
* Skapa ett Twitter-program per Twitter-konto.
* Skapa en ny **[!UICONTROL Twitter]** typtjänst för varje Twitter-program.

![](assets/social_diagram_twitter_service.png)

## Förutsättningar {#prerequisites}

Börja med att skapa ett eller flera Twitter-konton att skicka tweetar till.

Om du vill skapa ett Twitter-konto går du till [http://twitter.com](http://twitter.com).

## Skapa ett testkonto på Twitter {#creating-a-test-account-on-twitter}

Vi rekommenderar även att du skapar ett privat Twitter-konto som kan användas för att skicka tweet-korrektur (mer information finns i [Skicka korrektur](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* Skapa ett nytt Twitter-konto.
* Klicka på menyn i det övre högra hörnet och välj **[!UICONTROL Settings]**.
* Markera **[!UICONTROL Security and privacy]** fliken och markera **[!UICONTROL Protect my Tweets]** rutan.
* Klicka på **[!UICONTROL Save Changes]** knappen längst ned på sidan.

![](assets/social_twitter_test_page.png)

## Skapa ett program på Twitter {#creating-an-application-on-twitter}

För att Adobe Campaign ska kunna skicka tweets till dina Twitter-konton måste du skapa ett Twitter-program per Twitter-konto. Gör så här:

1. Logga in på ditt Twitter-konto.
1. Ange följande adress i webbläsaren: [https://apps.twitter.com/](https://apps.twitter.com/).
1. Klicka sedan på **[!UICONTROL Create New App]** knappen till höger.

   ![](assets/social_create_twitter_app_001.png)

1. Låt guiden vägleda dig genom processen.

   För att det här programmet ska tillåta Adobe Campaign att skicka tweets till ditt konto går du till fliken **[!UICONTROL Permissions]** i programmet och väljer **[!UICONTROL Read and Write]** för **[!UICONTROL Access]** avsnittet. På fliken **[!UICONTROL Settings]** måste du också lämna **[!UICONTROL Callback URL]** fältet tomt.

   ![](assets/social_create_twitter_app_002.png)

## Delegera skrivåtkomst till Adobe Campaign {#delegating-write-access-to-adobe-campaign}

För varje Twitter-program måste du skapa en annan **[!UICONTROL Twitter]** typtjänst som inkluderar programinställningarna.

Det här steget kräver samtidig åtkomst till Adobe Campaign-konsolen och en webbläsare som är inloggad på ditt Twitter-konto:

* **Twitter**: markera det program som skapats tidigare ([https://dev.twitter.com/apps](https://dev.twitter.com/apps)) och klicka på **[!UICONTROL Keys and Access Tokens]** .

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**: Gå till **[!UICONTROL Profiles and targets]** universum, klicka på **[!UICONTROL Services and Subscriptions]** länken och klicka på **[!UICONTROL Create]** knappen.

   ![](assets/social_twitter_service_007.png)

1. Välj **[!UICONTROL Twitter]** typ.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >Alternativet är **[!UICONTROL Synchronize subscriptions]** aktiverat som standard. När kryssrutan är markerad återställs listan med Twitter-följare i arbetsflödet för kontosynkronisering (se [Synkronisera Twitter-konton](#synchronizing-twitter-accounts)) så att du kan skicka direktmeddelanden till dem (se [Skicka direktmeddelanden till prenumeranter](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)). Om du inte vill återställa listan med följare avmarkerar du den här rutan.

1. Ange etiketten och det interna namnet på tjänsten.

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >Tjänstens namn måste vara identiskt **[!UICONTROL Internal name]** med namnet på Twitter-kontot. Följ stegen nedan för att vara säker på att det inte finns några inmatningsfel.

   * Klicka på **[!UICONTROL Save]** knappen.
   * Klicka på den Twitter-typtjänst som du just har skapat i översikten över tjänster.
   * Klicka på **[!UICONTROL Twitter page]** fliken. Twitter-kontot ska visas.

      ![](assets/social_twitter_service_010.png)

1. I **[!UICONTROL Visitor folder]** fältet väljer du den besökarmapp som följarna ska skapas i. Mer information finns i [driftsprincipen](../../social/using/publishing-on-twitter.md#operating-principle). Som standard skapas följare i roten av **[!UICONTROL Visitors]** mappen.

   ![](assets/social_twitter_service_010_b.png)

1. På Twitter kopierar du innehållet i **[!UICONTROL Consumer Key (API Key)]** och **[!UICONTROL Consumer Secret (API Secret)]** fälten och klistrar in det i **[!UICONTROL Consumer key]** och **[!UICONTROL Consumer secret]** i konsolens fält.

   ![](assets/social_twitter_service_012.png)

1. På Twitter kopierar du innehållet i **[!UICONTROL Access Token]** och **[!UICONTROL Access Token Secret]** fälten och klistrar in det i **[!UICONTROL Access token]** och **[!UICONTROL Access token secret]** i konsolens fält.

   ![](assets/social_twitter_service_013.png)

1. Klicka på i Adobe Campaign-konsolen **[!UICONTROL Save]**. Delegeringen av skrivåtkomst till Adobe Campaign är nu klar.

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>Du måste skapa en **[!UICONTROL Twitter]** typtjänst per Twitter-program.

I arbetsflödet synkroniseras Twitter-konton i Adobe Campaign. **[!UICONTROL Twitter account Synchronization]** Mer information finns i [Synkronisera Facebook-sidor](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages).

## Synkroniserar Twitter-konton {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>För att arbetsflödet ska kunna återställa listan över Twitter-prenumeranter måste **[!UICONTROL Twitter account synchronization]** kryssrutan vara markerad i redigeringsavsnittet för den tjänst som är länkad till kontot. Mer information finns i [Delegera skrivåtkomst till Adobe Campaign](#delegating-write-access-to-adobe-campaign).

Med **[!UICONTROL Twitter account synchronization]** arbetsflödet, som nås via **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** noden, kan du synkronisera Twitter-konton som konfigurerats tidigare med Adobe Campaign. Som standard aktiveras arbetsflödet varje torsdag kl. 7.30.

>[!NOTE]
>
>Det går att starta arbetsflödet när som helst genom att köra förväntad uppgiftsbearbetning. Du kan också redigera schemaläggaren för att ändra arbetsflödets utlösande frekvens. Mer information om schemaläggaren finns i [det här avsnittet](../../workflow/using/scheduler.md).

Nu kan du skicka tweets till dina Twitter-konton och skicka direktmeddelanden till dina följare. Mer information finns i: Publicera [på Twitter](../../social/using/publishing-on-twitter.md).
