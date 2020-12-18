---
solution: Campaign Classic
product: campaign
title: Publicera på Facebook-väggar
description: Publicera på Facebook-väggar
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 2%

---


# Publicera på Facebook-väggar{#publishing-on-facebook-walls}

För att Adobe Campaign ska kunna skicka publikationer till Facebook-väggar måste du delegera skrivåtkomsten för dessa sidor till Adobe Campaign. Detta inbegriper följande konfigurationssteg:

1. Skapa ett Facebook-konto med en eller flera sidor.
1. Skapa en Facebook-testsida för att skicka korrektur.
1. Skapa ett Facebook-program.
1. Ange Facebook-programinställningarna i Adobe Campaign i det externa kontot **[!UICONTROL Facebook routing]**.

## Förutsättningar {#prerequisites}

Börja med att skapa ett Facebook-konto och flera sidor: dessa kommer att användas för att skicka publikationer.

* Om du vill skapa ett Facebook-konto använder du länken [https://www.facebook.com](https://www.facebook.com).
* Om du vill skapa en Facebook-sida använder du länken [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create).

   Vi rekommenderar att du använder samma Facebook-konto för att administrera alla dina sidor. På så sätt behöver du bara ett Facebook-program och ett externt konto för att skriva på alla sidor i kontot.

   ![](assets/social_diagram_fb_external_account.png)

## Skapa en Facebook-testsida {#creating-a-test-facebook-page}

Vi rekommenderar att du skapar en privat Facebook-sida för att skicka ut korrektur för publicering (mer information finns i [Skicka korrektur](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Logga in på det Facebook-konto som du använder för att administrera dina sidor.
1. Skapa en ny Facebook-sida.
1. Klicka på knappen **[!UICONTROL Settings]** i det övre högra hörnet.
1. Ändra sidans synlighetsparametrar på fliken **[!UICONTROL General]**: markera rutan **[!UICONTROL Page unpublished]**.
1. Klicka på knappen **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Skapa ett Facebook-program {#creating-a-facebook-application}

För att Adobe Campaign ska kunna publicera på dina sidors väggar måste du skapa ett Facebook-program. Gör så här:

1. Logga in på det Facebook-konto som du använder för att administrera sidor.
1. Ange följande adress i webbläsaren: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >Beroende på vilken typ av konto du har kan en eller flera auktoriseringar vara nödvändiga.
   >
   >Om du vill skapa ett Facebook-program behöver du ett **verifierat** Facebook-konto.

1. Klicka på knappen **[!UICONTROL Add a New App]** i det övre högra hörnet på sidan. Ange ett appnamn och en e-postadress till kontakten och skicka sedan säkerhetskontrollen.

   ![](assets/social_create_facebook_app_002.png)

1. Klicka på **[!UICONTROL Add a platform]** under **[!UICONTROL Settings > Basic]** och välj typen **[!UICONTROL Facebook Web Games]**.

   ![](assets/social_create_facebook_app_003.png)

1. Kontrollera att du ser **[!UICONTROL Facebook Login]**-produkten i den vänstra menyn i **[!UICONTROL Products]**-avsnittet. Om inte, lägger du till en ny produkt och väljer **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. När programmet har skapats väljer du fliken **[!UICONTROL App Review]** och publicerar programmet.

   ![](assets/social_create_facebook_app_004.png)

## Delegerar skrivåtkomst till Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Om du vill delegera skrivåtkomst till Adobe Campaign för publicering på sidornas väggar måste du ange parametrarna för det Facebook-program som skapats tidigare.

Det här steget kräver åtkomst till både din Adobe Campaign-konsol och en webbläsare som är inloggad på det Facebook-konto som du använder för sidadministration:

>[!IMPORTANT]
>
>Adobe Campaign-operatorn måste ha administrationsbehörighet för att kunna utföra den här konfigurationen.

* **Facebook**: markera det tidigare skapade programmet (  [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) och välj  **[!UICONTROL Settings > Basic]** fliken.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Om **[!UICONTROL Facebook Web Games]**-avsnittet inte visas klickar du på knappen **[!UICONTROL Add Platform]** längst ned på sidan och väljer **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: Gå till  **[!UICONTROL Administration > Platform > External Accounts]** trädnoden, markera det  **[!UICONTROL Facebook routing]** externa kontot och klicka på  **[!UICONTROL Connector]** fliken.

   ![](assets/social_facebook_external_account_001.png)

1. Kopiera adressen i fältet **[!UICONTROL Secure Canvas URL]** i Adobe Campaign-konsolen och klistra in den i fältet **[!UICONTROL Secure Web Games URL (https)]** på Facebook (i avsnittet **[!UICONTROL Facebook Web Games]**).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >Du får inte använda den osäkra URL:en under några omständigheter.

   Kopiera och klistra in den här URL-adressen även under **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Om du vill kontrollera URL-adressens giltighet sparar du programmet, kopierar och klistrar in URL-adressen i fältet **[!UICONTROL Redirect URI to Check]** och klickar på **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. På Facebook kopierar du innehållet i fälten **[!UICONTROL App ID]** och **[!UICONTROL App Secret]** och klistrar in det i konsolens matchande fält.

   ![](assets/social_facebook_external_account_007.png)

1. På Facebook klickar du på knappen **[!UICONTROL Save Changes]** längst ned på sidan.
1. Gå till Adobe Campaign-konsolen och spara det externa kontot.

   >[!NOTE]
   >
   >Fältet **[!UICONTROL Marketing URL]** är valfritt.

1. Klicka på länken **[!UICONTROL Request the authorization from the application]** längst ned på fliken **[!UICONTROL Connector]** i Adobe Campaign-konsolen. Arbetsflödet **[!UICONTROL Synchronize Facebook pages]** aktiveras automatiskt och samlar in alla Facebook-sidor som hanteras av administratören. Mer information finns i [Synkronisera Facebook-sidor](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Som standard läggs sidorna till i **[!UICONTROL Facebook]**-tjänstmappen, som är tillgänglig via noden **[!UICONTROL Profiles and Targets > Services and Subscriptions]**. I fältet **[!UICONTROL Folder]** på fliken **[!UICONTROL Connector]** kan du ändra den tjänstmapp som Facebook-sidorna skapas i efter synkronisering. Du kan också välja de Facebook-sidor som du vill synkronisera i Adobe Campaign via fältet **[!UICONTROL Filter]**. Om du lämnar det här fältet tomt synkroniseras alla Facebook-sidor som hanteras av administratören.

1. En dialogruta med de olika behörighetsinställningarna för Facebook visas. Dessa gör att Adobe Campaign kan skicka publikationer till Facebook-kontosidorna.

   Godkänn de olika behörighetsförfrågningarna.

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign har fått rätt att publicera på Facebook-kontots väggar.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Om Facebook-kontot administrerar flera sidor konfigurerar du bara ett externt konto så att du kan skriva på valfri sida i Facebook-kontot. För varje nytt Facebook-konto måste du skapa ett nytt **[!UICONTROL Routing]**-konto.

Arbetsflödet i **[!UICONTROL Synchronization of Facebook pages]** synkroniserar alla sidor som administreras av Facebook-kontot så att du kan publicera dem direkt via Adobe Campaign. Mer information finns i [Synkronisera Facebook-sidor](#synchronizing-facebook-pages).

## Synkroniserar Facebook-sidor {#synchronizing-facebook-pages}

Med arbetsflödet **[!UICONTROL Synchronization of Facebook pages]**, som nås via noden **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**, kan du synkronisera (i Adobe Campaign) sidorna på det Facebook-konto som konfigurerats tidigare. Som standard är det här arbetsflödet konfigurerat att köras en gång om dagen eller när en administratör klickar på länken **[!UICONTROL Request an authorization from the application]** på tjänstkonfigurationsskärmen (se [Delegera skrivåtkomst till Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

När synkroniseringen är klar visas de insamlade sidorna i den tjänstmapp som anges i det externa kontot (se [Delegera skrivåtkomst till Adobe Campaign](#delegating-write-access-to-adobe-campaign)). Som standard läggs sidor till i roten för **[!UICONTROL Facebook]**-tjänstmappen, som är tillgänglig via **[!UICONTROL Profiles and Targets > Services and subscriptions]**-menyn.

![](assets/social_facebook_service_002.png)

Nu kan du publicera på Facebooks väggar direkt via Adobe Campaign. Mer information finns i [Publicera på Facebook](#publishing-on-facebook-walls).
