---
product: campaign
title: Publicera på Facebook-väggar
description: Publicera på Facebook-väggar
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: b5334de18eca8fc1147ae0c42fe23a6932bf71d2
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 4%

---

# Publicera på Facebook-väggar{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

För att Adobe Campaign ska kunna skicka publikationer till Facebook väggar måste du delegera skrivåtkomsten för dessa sidor till Adobe Campaign. Detta inbegriper följande konfigurationssteg:

1. Skapa ett Facebook-konto med en eller flera sidor.
1. Skapa en Facebook-testsida för att skicka korrektur.
1. Skapa en Facebook-applikation.
1. Ange programinställningarna för Facebook i Adobe Campaign i dialogrutan **[!UICONTROL Facebook routing]** externt konto.

## Förhandskrav {#prerequisites}

Börja med att skapa ett Facebook-konto och flera sidor: dessa kommer att användas för att skicka publikationer.

* Om du vill skapa ett Facebook-konto använder du [https://www.facebook.com](https://www.facebook.com) länk.
* Om du vill skapa en Facebook-sida använder du [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) länk.

   Vi rekommenderar att du använder samma Facebook-konto för att administrera alla dina sidor. På så sätt behöver du bara ett Facebook-program och ett externt konto för att skriva på alla sidor i kontot.

   ![](assets/social_diagram_fb_external_account.png)

## Skapa en testsida för Facebook {#creating-a-test-facebook-page}

Vi rekommenderar att du skapar en privat Facebook-sida för korrektur av publikationer (mer information finns i [det här avsnittet](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Logga in på det Facebook-konto som du använder för att administrera dina sidor.
1. Skapa en ny Facebook-sida.
1. Klicka på **[!UICONTROL Settings]** i det övre högra hörnet.
1. I **[!UICONTROL General]** ändrar du sidans synlighetsparametrar: kontrollera **[!UICONTROL Page unpublished]** box.
1. Klicka på knappen **[!UICONTROL Save Changes]**.

![](assets/social_facebook_test_page.png)

## Skapa en Facebook-applikation {#creating-a-facebook-application}

För att Adobe Campaign ska kunna publicera på sidorna måste du skapa ett Facebook-program. Gör så här:

1. Logga in på det Facebook-konto som du använder för att administrera sidor.
1. Ange följande adress i webbläsaren: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!CAUTION]
   >
   >Beroende på vilken typ av konto du har kan en eller flera auktoriseringar vara nödvändiga.
   >
   >Om du vill skapa ett Facebook-program måste du ha en **verifierad** Facebook-konto.

1. Klicka på **[!UICONTROL Add a New App]** i sidans övre högra hörn. Ange ett appnamn och en e-postadress till kontakten och skicka sedan säkerhetskontrollen.

   ![](assets/social_create_facebook_app_002.png)

1. Under **[!UICONTROL Settings > Basic]**, klicka på **[!UICONTROL Add a platform]** och väljer **[!UICONTROL Facebook Web Games]** typ.

   ![](assets/social_create_facebook_app_003.png)

1. I **[!UICONTROL Products]** -avsnittet, i den vänstra menyn, kontrollera att du ser **[!UICONTROL Facebook Login]** produkt. Om inte, lägg till en ny produkt och välj **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. När programmet har skapats väljer du **[!UICONTROL App Review]** och publicera programmet.

   ![](assets/social_create_facebook_app_004.png)

## Delegera skrivåtkomst till Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Om du vill delegera skrivåtkomst till Adobe Campaign för publicering på sidornas väggar måste du ange parametrarna för det tidigare skapade Facebook-programmet.

Det här steget kräver åtkomst till både Adobe Campaign-konsolen och en webbläsare som är inloggad på det Facebook-konto som du använder för sidadministration:

>[!CAUTION]
>
>Adobe Campaign-operatorn måste ha administrationsbehörighet för att kunna utföra den här konfigurationen.

* **Facebook**: välj det tidigare skapade programmet ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) och väljer **[!UICONTROL Settings > Basic]** -fliken.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Om **[!UICONTROL Facebook Web Games]** visas inte klickar du på **[!UICONTROL Add Platform]** längst ned på sidan och välj **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: gå till **[!UICONTROL Administration > Platform > External Accounts]** trädnod, välj **[!UICONTROL Facebook routing]** externt konto och klicka på **[!UICONTROL Connector]** -fliken.

   ![](assets/social_facebook_external_account_001.png)

1. I Adobe Campaign Console kopierar du adressen som finns i **[!UICONTROL Secure Canvas URL]** och klistra in den i **[!UICONTROL Secure Web Games URL (https)]** på Facebook (i **[!UICONTROL Facebook Web Games]** ).

   ![](assets/social_facebook_external_account_006.png)

   >[!CAUTION]
   >
   >Du får inte använda den osäkra URL:en under några omständigheter.

   Kopiera och klistra in den här URL:en även under **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Om du vill kontrollera URL-adressens giltighet sparar du programmet, kopierar och klistrar in URL-adressen i **[!UICONTROL Redirect URI to Check]** fält och klicka på **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. På Facebook kopierar du innehållet i **[!UICONTROL App ID]** och **[!UICONTROL App Secret]** fält och klistra in dem i konsolens matchande fält.

   ![](assets/social_facebook_external_account_007.png)

1. På Facebook klickar du på **[!UICONTROL Save Changes]** längst ned på sidan.
1. Gå till Adobe Campaign-konsolen och spara det externa kontot.

   >[!NOTE]
   >
   >The **[!UICONTROL Marketing URL]** fältet är valfritt.

1. I Adobe Campaign-konsolen klickar du på **[!UICONTROL Request the authorization from the application]** länken längst ned i **[!UICONTROL Connector]** -fliken. The **[!UICONTROL Synchronize Facebook pages]** arbetsflödet aktiveras automatiskt och alla Facebook-sidor som hanteras av administratören samlas in. [Läs mer](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Som standard läggs sidorna till i **[!UICONTROL Facebook]** tjänstmapp, tillgänglig via **[!UICONTROL Profiles and Targets > Services and Subscriptions]** nod. The **[!UICONTROL Folder]** fält för **[!UICONTROL Connector]** kan du ändra den tjänstmapp som Facebook-sidorna skapas i efter synkronisering. Du kan också välja de Facebook-sidor du vill synkronisera i Adobe Campaign med **[!UICONTROL Filter]** fält. Om du lämnar det här fältet tomt synkroniseras alla Facebook-sidor som hanteras av administratören.

1. En dialogruta med de olika behörighetsinställningarna för Facebook visas. Med dessa kan Adobe Campaign skicka publikationer till Facebook kontosidor.

   Godkänn de olika behörighetsförfrågningarna.

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign har rätt att publicera på väggarna på Facebook-kontots sidor.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Om Facebook-kontot administrerar flera sidor konfigurerar du bara ett externt konto så att du kan skriva på valfri sida i Facebook-kontot. För varje nytt Facebook-konto måste du skapa ett nytt **[!UICONTROL Routing]** skriv ett externt konto.

The **[!UICONTROL Synchronization of Facebook pages]** arbetsflödet synkroniserar alla sidor som administreras av Facebook-kontot så att du kan publicera dem direkt via Adobe Campaign. [Läs mer](#synchronizing-facebook-pages).

## Synkronisera Facebook-sidor {#synchronizing-facebook-pages}

The **[!UICONTROL Synchronization of Facebook pages]** arbetsflöde, som du kommer åt via **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** kan du synkronisera (i Adobe Campaign) sidorna i det Facebook-konto som konfigurerats tidigare. Som standard är arbetsflödet konfigurerat att köras en gång om dagen eller när en administratör klickar på **[!UICONTROL Request an authorization from the application]** på skärmen för tjänstkonfiguration. [Läs mer](#delegating-write-access-to-adobe-campaign).

När synkroniseringen är klar visas de insamlade sidorna i den tjänstmapp som har angetts i det externa kontot. [Läs mer](#delegating-write-access-to-adobe-campaign)).

Som standard läggs sidor till i roten av **[!UICONTROL Facebook]** tjänstmappen som är tillgänglig via **[!UICONTROL Profiles and Targets > Services and subscriptions]** -menyn.

![](assets/social_facebook_service_002.png)

Nu kan du publicera på Facebook väggar direkt via Adobe Campaign. [Läs mer](#publishing-on-facebook-walls).
